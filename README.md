read batch collection example{
  "_id": {
    "$oid": "6a2168239c32e8a548522531"
  },
  "jobName": "migrateCustomersToSF",
  "jobExecutionId": "6a2167c64057f4b070a46ddb",
  "batchNo": 64,
  "remarks": "Bulk write operation error on MongoDB server 10.31.3.230:27017. Write errors: [BulkWriteError{index=0, code=11000, message='E11000 duplicate key error collection: data-bridge-qa.sync_records index: jobExecutionId_-1_recordId_-1 dup key: { jobExecutionId: \"6a2167c64057f4b070a46ddb\", recordId: \"PI0302887320\" }', details={}}]. ",
  "status": "FAILED",
  "retryCount": 3,
  "createdAt": {
    "$date": "2026-06-04T11:57:23.650Z"
  },
  "updatedAt": {
    "$date": "2026-06-04T11:57:26.942Z"
  },
  "_class": "com.star.databridge.entity.ReadBatchExecutionEntity"
}

write batch collection example
{
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
