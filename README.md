The core abstraction
Every reader (ApiReader, SqlReader) implements DataReader, taking a ReadContext (has both offset (long) and cursor (String) fields — mutually exclusive, picked per job) and returning a ReadResult (has nextOffset, nextCursor, hasMore). Which one's used is decided entirely by PaginationConfig.type ("offset" or "cursor") in the job config's read params — same contract for both API and SQL sources.
Step by step
1. First batch — JobExecutionService.triggerJob() creates read batch #1 and publishes it with cursor = null (start from the beginning).
2. Consumer resolves the value — MigrationReadBatchConsumer.execute() reads PaginationConfig off the job config, then picks based on type:
Java
.cursor("CURSOR".equalsIgnoreCase(type) && msg.getNextCursor() != null ? msg.getNextCursor() : "0")
.offset("OFFSET".equalsIgnoreCase(type) && msg.getNextCursor() != null ? Long.parseLong(msg.getNextCursor()) : 0)
Worth knowing: the Kafka message and the persisted ReadBatchExecutionEntity.nextCursor field only have one String field — it carries either the cursor token or the offset number as text, disambiguated purely by the config's declared type, not by the message itself.
4. Reader injects it as a template variable — for API: OFFSET/CURSOR gets substituted into the configured request (e.g. ?offset={{OFFSET}}) before the HTTP call. For SQL: offset becomes a literal OFFSET {{n}} clause; cursor becomes a WHERE <configured predicate> fragment (e.g. id > :lastId), skipped on the first call unless explicitly configured to run on batch #1 too.
5. After the call, next value gets computed:
Offset: nextOffset = currentOffset + batchSize; hasMore = (rowCount == batchSize)
Cursor: extracted from the response via a configured JSONPath (pagination.nextCursorPath) — only if hasMore was true; if extraction fails, nextCursor = null and hasMore collapses to false
6. Advance — if hasMore, the consumer creates the next ReadBatchExecutionEntity and republishes with that computed value; the current batch gets readBatchService.setSuccessful(readBatch, recordIds, nextCursor) — meaning the value stored on a batch is what the next batch should use, not what that batch itself read with (this is exactly why the manual-retry endpoint had to derive its cursor from the previous batch, from that earlier conversation).
7. On failure — retries reuse the same cursor (position never advances on retry). If retries exhaust: cursor pagination always aborts the job — there's no way to skip a failed batch without the response that would've told you the next cursor. Offset pagination can optionally skip ahead (continueAtNextOffset, only if failureStrategy=IGNORE) by just computing currentOffset + batchSize and continuing.{
  "_id": {
    "$oid": "6a2167f6a9b57a5a63a7d2ae"
  },
  "jobExecutionId": "6a2167c64057f4b070a46ddb",
  "entity": "customer",
  "status": "SUCCESS",
  "errorMessage": "Not enough READY records",
  "createdAt": {
    "$date": "2026-06-04T11:56:38.924Z"
  },
  "updatedAt": {
    "$date": "2026-06-04T11:57:13.649Z"
  },
  "_class": "com.star.databridge.entity.WriteBatchExecutionEntity"
}

sync records collection example 
{
  "_id": {
    "$oid": "6a2155ca3263832bb22c8abc"
  },
  "jobExecutionId": "6a2155bb15bbc753992072e9",
  "entity": "customer",
  "recordId": "10874800-44",
  "record": {
    "AadharNumber__c": null,
    "AccountType__c": "PROPOSER",
    "BankAccountNumber__c": null,
    "BankBranchCode__c": null,
    "CKYCStatus__c": null,
    "CKYCNUMBER__c": null,
    "CustomerProfile__c": null,
    "PersonBirthdate": "AgV46j/jy1z0N6iQ/Rh2QNVAMhNbwuqfuAy5MTp9oQBkCroAXwABABVhd3MtY3J5cHRvLXB1YmxpYy1rZXkAREFpR0ZodzJEdXR6Q1BiaHFkdzRaQk51VmNnemJaQ0ZUbVAxeEZCakNLY2JoNjRKS1BNTTJLSC95bldXbE0xT1Y5QT09AAEAEnNpdC1zdGFyLWNyeXB0by1zbQAXREVLAAAAgAAAAAw7hPKBygjMS3AXvC4AMBM8+4Lhzdts0blKMJwA6c2zKfImvI6hfOHQkwv2NKEwdCKkt5rufOl9oBwAEa9/WgIAABAAhPSjPc7tWCUTZj8k7z0BJIuTWT+Ap9uP6MWhQX601/4huwywYjyBEeaJZZSCIY+F/////wAAAAEAAAAAAAAAAAAAAAEAAAAKSxWxMjY4puOxsRLzwwyc0gNq5JlcuRyw8oAAZzBlAjBPQKoCc9hE2I/59Bsu7nu7NKZURVUBC4fARqbn6MA1Q9WrMN8ms6zVJF947urW/gECMQC+Xs5+r3UTGv/SfU9iyflgxWle508wYsGTVGQF1sk2ENmstvLWdgZAT2o6Q4spX3g=",
    "DLUniqueId__c": "10874800-44",
    "PersonEmail": "AgV4qoufTBaueUMWeNZ66VrgCZgcqTw9R/hQtQgzX4MrLgMAXwABABVhd3MtY3J5cHRvLXB1YmxpYy1rZXkAREE4UkdyVTAzaFRCT0lXcnV3a3lOSzgvc05nZCtmZDIzZEVFSmM0aENKK01tR3p3WW9IbFRnNUttQTdybFd3OEd2QT09AAEAEnNpdC1zdGFyLWNyeXB0by1zbQAXREVLAAAAgAAAAAzb4khPgeDF2TS091QAMPjnDMviiBCu2JipI6I2TqEhL1qr0YXHBB1kEfLTosbJmkX3HyJMcM/vaAOnM8acdAIAABAAyYsqcSdGVWoYq2O3ljI6Ui13HfHyADpRtXYwvl+58uJMqYCyq5SUc0NePE+DxykB/////wAAAAEAAAAAAAAAAAAAAAEAAAAOE3SUhhmJvtZXJ5aA7QvioQ+w/IjsxW4GBmdYw8JiAGcwZQIxAKFQbzX264w524tu3/o+H1GnelK6z2HdSR25MxaApbhuTHzvW6575osmVEMF12WtQgIwXSrmmPR4Xrd4pSFfi1dUGZN2vZtSCI5t2oziNddRlu5Run3mGNNqI6Ka7vXrC8o1",
    "FirstName": null,
    "CFirstName__pc": null,
    "PersonGenderIdentity": "MALE",
    "HealthId__c": "PI0385966500",
    "LastName": "VIJENDER SATBIR SINGH ",
    "CLastName__pc": "VIJENDER SATBIR SINGH ",
    "PersonMailingCity": "Chennai",
    "PersonMailingCountry": "INDIAN",
    "PersonMailingState": "Tamil Nadu",
    "PersonMailingStreet": "SM",
    "PersonMailingPostalCode": "91",
    "MaritalStatus__c": null,
    "MaritalStatus__pc": null,
    "CMiddleName__pc": null,
    "PersonMobilePhone": "AgV4cA2daF45RcsAOxZOBCdIVpH6owaPlnhFSdWYcf/AUmUAXwABABVhd3MtY3J5cHRvLXB1YmxpYy1rZXkAREE3OVJZK1I3SGRNWWQxWVRxdlBObTNtNjYwRHEyVWZma05YRW1XQSs2TmhHVXVueWVnOWNndlgyVEF1b09td2NZUT09AAEAEnNpdC1zdGFyLWNyeXB0by1zbQAXREVLAAAAgAAAAAwdTEwBqB8/Xb9PGJsAMJ42hXxY8Pn6l3uCPwGUMURbmpEMNx00wPdYGUepncuILAA9Ah8rMlISMLSRJfM/IQIAABAA0kh5i+reD9yfsw23EpbbWdD4+C8hTBbZXCinGQ8JXMTXJ4tAyYyAJIc85rr0D/Fj/////wAAAAEAAAAAAAAAAAAAAAEAAAAK3qz78XwcvIDFCCGNqAJVnUdrfqip9Bgu9+8AZzBlAjBIsmpXc8a775M6SswDUlcXwvElRB4mcmOoWCCCUryqnm8i/fQy7zH9+PbKX3jiQm8CMQDlt+yO1rTnHH+Li/5nVw3HEgUUYWQ47SrTOVpsMzbUg3MXneq6pKpBJ/0lss468v4=",
    "Occupation__c": "Professional",
    "Occupation__pc": "Professional",
    "PANNumber__c": null,
    "PartyType__c": "PARTY_CODE",
    "PartyCode__c": "10874800-44",
    "Phone": "AgV4/JbsW93o2UKViVu1FQROU5TokC5CBz5QRVTNnS8gnS4AXwABABVhd3MtY3J5cHRvLXB1YmxpYy1rZXkAREF0ejl6SmZ4Z1R4ZFZFOHlzSy8xbHFzeFdIVDRHZFh0UWhBNUNQUnZ0YjgrWVd3VmVNRkFick5xbHlya21SKzdNUT09AAEAEnNpdC1zdGFyLWNyeXB0by1zbQAXREVLAAAAgAAAAAzHS28u/kLksooMgD8AMLStZ9nyxuhmPE3nLinwZvyzb51WKvtHbeAsCMA8OIUPXAiBB51tGXmSKHgq/Z7p2wIAABAArRxB0dr2ODy3c5xTMmi6KnjZGZ6r1wDMVea3RqTClg3Ou4Aim3iRbVT1/ySk7xvw/////wAAAAEAAAAAAAAAAAAAAAEAAAAKVHziBlAU/aI16E7/qrN8RnP+5LPtd+g9AVUAZzBlAjEAm1a3/+oWIveVEUh7xksqnb4uTxIUMjqndTYJ0Yq/BQ9916dnIf3wlUfmqV0cM0KpAjAInxN25LRT8/xhKZ/8oMutit82xCDWltk0BQOUBFS8JT/pyWKmWhY4gr1CZSCYXxU=",
    "AccountRecordType__c": "Person Account",
    "SourceSystem__c": "BANCS",
    "ClusterId__c": null,
    "AlternatePhoneNo1__c": null,
    "AlternatePhoneNo2__c": null,
    "BillingCountry": "India",
    "RecordType": {
      "Name": "Person Account"
    }
  },
  "retryCount": 0,
  "status": "FAILED",
  "createdAt": {
    "$date": "2026-06-04T10:39:05.909Z"
  },
  "updatedAt": {
    "$date": "2026-06-04T10:39:05.909Z"
  },
  "_class": "com.star.databridge.entity.SyncRecordEntity",
  "errorMessage": "Job aborted by user"
}

step executions collection example

{
  "_id": {
    "$oid": "6a1fdd1dcf3c083ed3474ef9"
  },
  "stepExecutionId": "208b1fa3-07a9-4b7a-a033-db089467e984",
  "batchId": "6a1fdd0d72538959565c3ba7",
  "batchType": "READ",
  "jobExecutionId": "6a1fdd0d72538959565c3ba6",
  "startedAt": {
    "$date": "2026-06-03T07:51:57.078Z"
  },
  "status": "SUCCESS",
  "stepName": "transformSFHospitals",
  "stepType": "JOLT_TRANSFORM",
  "completedAt": {
    "$date": "2026-06-03T07:51:57.987Z"
  }
}

plugins {
    id 'java'
    id 'org.springframework.boot' version '4.1.0'
    id 'io.spring.dependency-management' version '1.1.7'
    id "org.sonarqube" version "7.2.3.7755"
    id 'jacoco'
}

group = 'com.star.databridge'
version = '0.0.1-SNAPSHOT'
description = 'initial setup'
java {
    toolchain {
        languageVersion = JavaLanguageVersion.of(25)
    }
}
ext {
    set('logback.version', '1.5.36')
    set('tomcat.version', '11.0.23')
}

configurations {
    compileOnly {
        extendsFrom annotationProcessor
    }
}

dependencies {
    implementation 'com.jayway.jsonpath:json-path:2.9.0'
    implementation 'org.springframework.boot:spring-boot-starter-web'
    //below 3 for snyk
    implementation 'org.apache.tomcat.embed:tomcat-embed-core:11.0.23'
    implementation 'org.apache.httpcomponents.core5:httpcore5-h2:5.4.3'
    implementation 'ch.qos.logback:logback-core:1.5.36'
    implementation 'org.apache.httpcomponents.client5:httpclient5'
    implementation 'org.springframework.boot:spring-boot-starter-actuator'
    implementation 'net.logstash.logback:logstash-logback-encoder:8.1'
    implementation 'org.springframework.boot:spring-boot-starter-kafka'
    implementation 'org.springframework.boot:spring-boot-starter-data-mongodb'
    implementation 'org.springframework.boot:spring-boot-starter-jdbc'
    runtimeOnly 'org.postgresql:postgresql:42.7.12'
    runtimeOnly 'com.mysql:mysql-connector-j'
    implementation 'com.fasterxml.jackson.core:jackson-databind:2.18.9'
    implementation 'com.fasterxml.jackson.datatype:jackson-datatype-jsr310'
    // Jolt uses Jackson 2 internally, but we only call Chainr.fromSpec(List) and
    // chainr.transform(Map) — neither path loads Jackson classes at runtime.
    implementation 'com.bazaarvoice.jolt:jolt-core:0.1.8'
    implementation 'com.auth0:java-jwt:4.4.0'
    // ShedLock — distributed lock for scheduled tasks (one pod per cron trigger)
    implementation 'net.javacrumbs.shedlock:shedlock-spring:6.3.1'
    implementation 'net.javacrumbs.shedlock:shedlock-provider-mongo:6.3.1'
    testImplementation('org.springframework.kafka:spring-kafka-test') {
        exclude group: 'org.apache.kafka', module: 'kafka-clients'
    }
    implementation 'com.starhealth:star-crypto-util:2.1.1'
    implementation 'com.github.ben-manes.caffeine:caffeine:3.1.8'
    testImplementation 'org.apache.kafka:kafka-clients'

    compileOnly 'org.projectlombok:lombok'
    annotationProcessor 'org.projectlombok:lombok'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
    testRuntimeOnly 'org.junit.platform:junit-platform-launcher'
    implementation 'io.micrometer:micrometer-observation'
    implementation 'io.micrometer:micrometer-registry-prometheus'
    implementation 'org.springframework.boot:spring-boot-micrometer-tracing-brave'
    implementation 'io.micrometer:micrometer-tracing-bridge-brave'
    implementation 'org.bouncycastle:bcprov-jdk18on:1.84'

}
sonarqube {
    properties {
        property "sonar.token", project.findProperty("SONAR_TOKEN") ?: System.getenv("SONAR_TOKEN")
        property "sonar.host.url", project.findProperty("SONAR_HOST") ?: System.getenv("SONAR_HOST")
        property "sonar.java.coveragePlugin", "jacoco"
        property "sonar.coverage.exclusions", ""
    }
}

jacoco {
    toolVersion = "0.8.10" // Replace this with your JaCoCo version
}

test {
    jacoco {
        // This is similar to `prepare-agent` in Maven
        destinationFile = layout.buildDirectory.file("jacoco/test.exec").get().asFile
        excludes = []
    }

    reports {
        junitXml.required=true // Set custom directory
        junitXml.mergeReruns = true // Combine test rerun results into a single XML file
    }
}

jacocoTestReport {
    reports {
        xml.required = true
        html.required = true
    }
}

jacocoTestCoverageVerification {
    violationRules {
        rule {
            element = 'CLASS'
        }
    }
}
task mergeTestReports {
    doLast {
        def reportDir = file("$buildDir/test-results/test")
        def mergedReportFile = file("$buildDir/test-results/test/merged-test-results.xml")

        def reportFiles = reportDir.listFiles().findAll { it.name.endsWith('.xml') }

        if (reportFiles.size() > 1) {
            println "Merging ${reportFiles.size()} test result files into one..."

            mergedReportFile.withWriter { writer ->
                writer.writeLine('<testsuites>')

                reportFiles.each { file ->
                    def lines = file.readLines()
                    lines.drop(1).dropRight(1).each { line ->
                        writer.writeLine(line)
                    }
                }

                writer.writeLine('</testsuites>')
            }

            println "Merged test report created at: $mergedReportFile"
        } else {
            println "No multiple XML files to merge."
        }
    }
}

test.finalizedBy(mergeTestReports)  // Ensure merging happens after tests run

tasks.check.dependsOn jacocoTestCoverageVerification
tasks.named('build') {
    dependsOn tasks.named('jacocoTestReport')
}
