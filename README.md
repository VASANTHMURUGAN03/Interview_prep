java.time.format.DateTimeParseException: Text '2026-08-05T14:02:05.360754135Z' could not be parsed, unparsed text found at index 29 at java.base/java.time.format.DateTimeFormatter.parseResolved0(DateTimeFormatter.java:2111) at java.base/java.time.format.DateTimeFormatter.parse(DateTimeFormatter.java:2010) at java.base/java.time.LocalDateTime.parse(LocalDateTime.java:494) at java.base/java.time.LocalDateTime.parse(LocalDateTime.java:479) at com.star.eps.eps_crm_subscriber.util.DataMapperUtil.addOffset(DataMapperUtil.java:103) at com.star.eps.eps_crm_subscriber.util.DataMapperUtil.mapToSalesforceEmiDto(DataMapperUtil.java:150) at com.star.eps.eps_crm_subscriber.service.processor.impl.EmiManagerProcessor.process(EmiManagerProcessor.java:32) at com.star.eps.eps_crm_subscriber.service.validator.EpsValidatorService.processEvent(EpsValidatorService.java:49) at com.star.eps.eps_crm_subscriber.service.validator.EpsValidatorService.validateAndProcessEvent(EpsValidatorService.java:34) at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) at java.base/java.lang.reflect.Method.invoke(Method.java:580) at org.springframework.aop.support.AopUtils.invokeJoinpointUsingReflection(AopUtils.java:360) at org.springframework.aop.framework.ReflectiveMethodInvocation.invokeJoinpoint(ReflectiveMethodInvocation.java:196) at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:163) at org.springframework.aop.aspectj.MethodInvocationProceedingJoinPoint.proceed(MethodInvocationProceedingJoinPoint.java:89) at com.star.eps.eps_subscriber_retry.aspect.EpsRetryAspect.aroundRetryableConsumer(EpsRetryAspect.java:69) at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) at java.base/java.lang.reflect.Method.invoke(Method.java:580) at org.springframework.aop.aspectj.AbstractAspectJAdvice.invokeAdviceMethodWithGivenArgs(AbstractAspectJAdvice.java:649) at org.springframework.aop.aspectj.AbstractAspectJAdvice.invokeAdviceMethod(AbstractAspectJAdvice.java:631) at org.springframework.aop.aspectj.AspectJAroundAdvice.invoke(AspectJAroundAdvice.java:71) at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:173) at org.springframework.aop.interceptor.ExposeInvocationInterceptor.invoke(ExposeInvocationInterceptor.java:97) at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184) at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:728) at com.star.eps.eps_crm_subscriber.service.validator.EpsValidatorService$$SpringCGLIB$$0.validateAndProcessEvent(<generated>) at com.star.eps.eps_crm_subscriber.listener.CrmListener.lambda$listener$0(CrmListener.java:54) at com.star.eps.eps_crm_subscriber.util.TracingUtils.runWithSpan(TracingUtils.java:19) at com.star.eps.eps_crm_subscriber.listener.CrmListener.listener(CrmListener.java:44) at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) at java.base/java.lang.reflect.Method.invoke(Method.java:580) at org.springframework.aop.support.AopUtils.invokeJoinpointUsingReflection(AopUtils.java:360) at org.springframework.aop.framework.ReflectiveMethodInvocation.invokeJoinpoint(ReflectiveMethodInvocation.java:196) at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:163) at org.springframework.aop.aspectj.MethodInvocationProceedingJoinPoint.proceed(MethodInvocationProceedingJoinPoint.java:89) at com.star.eps.loggers.impl.StarNonReactiveLogger.performLoggingAndProceed(StarNonReactiveLogger.java:48) at com.star.eps.aspects.StarLoggingAspect.maxOrderLogging(StarLoggingAspect.java:27) at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) at java.base/java.lang.reflect.Method.invoke(Method.java:580) at org.springframework.aop.aspectj.AbstractAspectJAdvice.invokeAdviceMethodWithGivenArgs(AbstractAspectJAdvice.java:649) at org.springframework.aop.aspectj.AbstractAspectJAdvice.invokeAdviceMethod(AbstractAspectJAdvice.java:631) at org.springframework.aop.aspectj.AspectJAroundAdvice.invoke(AspectJAroundAdvice.java:71) at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:173) at org.springframework.aop.interceptor.ExposeInvocationInterceptor.invoke(ExposeInvocationInterceptor.java:97) at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184) at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:728) at com.star.eps.eps_crm_subscriber.listener.CrmListener$$SpringCGLIB$$0.listener(<generated>) at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) at java.base/java.lang.reflect.Method.invoke(Method.java:580) at org.springframework.messaging.handler.invocation.InvocableHandlerMethod.doInvoke(InvocableHandlerMethod.java:169) at org.springframework.kafka.listener.adapter.KotlinAwareInvocableHandlerMethod.doInvoke(KotlinAwareInvocableHandlerMethod.java:45) at org.springframework.messaging.handler.invocation.InvocableHandlerMethod.invoke(InvocableHandlerMethod.java:119) at org.springframework.kafka.listener.adapter.HandlerAdapter.invoke(HandlerAdapter.java:78) at org.springframework.kafka.listener.adapter.MessagingMessageListenerAdapter.invokeHandler(MessagingMessageListenerAdapter.java:475) at org.springframework.kafka.listener.adapter.MessagingMessageListenerAdapter.invoke(MessagingMessageListenerAdapter.java:421) at org.springframework.kafka.listener.adapter.RecordMessagingMessageListenerAdapter.onMessage(RecordMessagingMessageListenerAdapter.java:85) at org.springframework.kafka.listener.adapter.RecordMessagingMessageListenerAdapter.onMessage(RecordMessagingMessageListenerAdapter.java:50) at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.doInvokeOnMessage(KafkaMessageListenerContainer.java:2936) at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.invokeOnMessage(KafkaMessageListenerContainer.java:2914) at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.doInvokeRecordListener(KafkaMessageListenerContainer.java:2826) at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.doInvokeWithRecords(KafkaMessageListenerContainer.java:2663) at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.invokeRecordListener(KafkaMessageListenerContainer.java:2552) at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.invokeListener(KafkaMessageListenerContainer.java:2201) at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.invokeIfHaveRecords(KafkaMessageListenerContainer.java:1555) at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.pollAndInvoke(KafkaMessageListenerContainer.java:1493) at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.run(KafkaMessageListenerContainer.java:1362) at java.base/java.util.concurrent.CompletableFuture$AsyncRun.run(CompletableFuture.java:1804) at java.base/java.lang.Thread.run(Thread.java:1583)


HOSTNAME:
eps-crm-subscriber-svc-869d949dff-qmgwm


APPLICATION_NAME:
eps-crm-subscriber


traceId:
6a7374bc7d97fbcc699a232b46a61e3e


spanId:
26ae93a24bcb7c0b
▶
2026-08-05 23:07:00.228


▶
Line:
INFO


@timestamp:
2026-08-05T23:07:00.03403371+05:30


@version:
1


message:
[EpsValidatorService] @processEvent() subscriberRequestSubscriberRequest(eventId=1e7b5b75-f518-4097-b09b-174b518e4a37, parentEventId=null, event=customeremi.updates, eventTimestamp=2026-08-05T19:32:05.451, publisherId=1512352282091655168, source=EmiManager, priority=null, subscriberGroupId=null, subscriberId=1512353026739998720, subscriberLogId=null, eventSubscriber=EventSubscriber(exponentialDelay=6000, maxRetryCount=3, isSequence=false, eventDelayConfig=null), currRetryCount=1, destination=CRM-EmiUpdates, key=9304112700081188, payload={event=MANDATE_PRESENTED, policyNumber=9304112700081188, installmentNumber=3, policyStatus=ACTIVE_POLICY, payment={status=PENDING, paymentSource=MANDATE, paymentAmount=1501.583, refundAmount=null, paymentLinkType=null, paymentUrl=null, createdDate=2026-08-05T19:32:05.360754135, paymentDate=null, refundDate=null, error=null}, receipt=null, mandate=null}, isOnDemandRequest=true, version=null, schemaId=null, retryTopic=uat-eps-kafka-crm-consumer-topic, dlqTopic=null)package com.star.eps.eps_crm_subscriber.util;

import com.star.eps.eps_crm_subscriber.dto.D2CLeadDetailsCreateDTO;
import com.star.eps.eps_crm_subscriber.dto.D2CLeadDetailsUpdateDTO;
import com.star.eps.eps_crm_subscriber.dto.LeadDataDto;
import com.star.eps.eps_crm_subscriber.dto.NameDto;
import com.star.eps.eps_crm_subscriber.dto.endorsement.EndorsementDto;
import com.star.eps.eps_crm_subscriber.dto.premium.CollectionDetailDTO;
import com.star.eps.eps_crm_subscriber.dto.proposal.PolicyDetails;
import com.star.eps.eps_crm_subscriber.dto.proposal.PolicyProposalDto;
import com.star.eps.eps_crm_subscriber.dto.refund.RefundDto;
import com.star.eps.eps_crm_subscriber.dto.request.SalesForceEmiRequest;
import com.star.eps.eps_crm_subscriber.dto.request.salesforce.CreateLeadRequestDto;
import com.star.eps.eps_crm_subscriber.dto.request.salesforce.SalesForceProposalUpdateRequestDto;
import com.star.eps.eps_crm_subscriber.dto.request.salesforce.SalesforceEndorsementRequestDto;
import com.star.eps.eps_crm_subscriber.dto.request.salesforce.UpdateLeadOrBuyingJourneyRequestDto;
import com.star.eps.eps_crm_subscriber.dto.workflow.WorkflowDto;
import com.star.eps.eps_crm_subscriber.enums.CancellationEndorsementCode;
import com.star.eps.eps_crm_subscriber.enums.ErrorCode;
import com.star.eps.eps_crm_subscriber.exception.ClientNonRetryableException;
import lombok.extern.slf4j.Slf4j;
import org.apache.logging.log4j.util.Strings;
import org.springframework.stereotype.Component;
import org.springframework.util.StringUtils;

import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.ZoneOffset;
import java.time.format.DateTimeFormatter;
import java.util.List;
import java.util.Map;
import java.util.Objects;
import java.util.Set;
import java.util.stream.Collectors;
import java.util.stream.Stream;

@Slf4j
@Component
public class DataMapperUtil {

    private static Map<String, String> STATUS_MAP = Map.of(
            "05", "ACTIVE",
            "09", "CANCELLED"
    );

    private static Map<String, Set<String>> MANDATE_STATUS_MAP = Map.of(
            "MANDATE ACTIVE", Set.of("CREATED", "ACTIVE", "PAUSED"),
            "MANDATE CANCELLED", Set.of("FAILURE", "EXPIRED", "REVOKED"),
            "MANDATE NOT REGISTERED", Set.of("NOT_REGISTERED")
    );

    private static Map<String, String> INSTALLMENT_STATUS_MAP = Map.of(
            "SINGLE_INSTALLMENT", "SINGLE_PAYMENT",
            "SINGLE_INSTALLMENT_WITH_MANDATE", "SINGLE_PAYMENT_WITH_MANDATE",
            "MULTIPLE_INSTALLMENTS", "BULK_PAYMENT",
            "BNPL", "BNPL_PAYMENT"
    );

    public static SalesForceProposalUpdateRequestDto mapToSalesforcePremiumDto(CollectionDetailDTO dto) {
        log.info("[SalesForceProposalUpdateRequestDto] @mapToSalesforcePremiumDto collectionDetailDto : {}", dto);
        if (dto == null || dto.getCollectionDetails() == null || dto.getCollectionDetails().isEmpty()) {
            return null;
        }

        try {
            CollectionDetailDTO.CollectionDetail collectionDetails = dto.getCollectionDetails().getFirst();
            Double collectedAmount = 0.0;
            Double collectionAmount = 0.0;

            if (collectionDetails != null && collectionDetails.getCollectionProperty() != null) {
                String collectedStr = collectionDetails.getCollectionProperty().getAmountToBeCollected();
                if (StringUtils.hasText(collectedStr)) {
                    collectedAmount = Double.parseDouble(collectedStr.trim());
                }

                String collectionStr = collectionDetails.getCollectionProperty().getCollectionAmount();
                if (StringUtils.hasText(collectionStr)) {
                    collectionAmount = Double.parseDouble(collectionStr.trim());
                }
            }

            return SalesForceProposalUpdateRequestDto.builder()
                    .key("proposal-default")
                    .proposalNo(dto.getProposalNumber())
                    .balancePremium(collectedAmount - collectionAmount)
                    .premiumPaidTillDate(toDateOnly(collectionDetails.getDateOfCollection()))
                    .ldPaymentMode(StringUtils.hasText(collectionDetails.getCollectionProperty().getMode())
                            ? collectionDetails.getCollectionProperty().getMode()
                            : null)
                    .build();
        } catch (Exception e) {
            log.error("[SalesForceProposalUpdateRequestDto] Error mapping PolicyProposalDto: {}", e.getMessage(), e);
            throw new ClientNonRetryableException(ErrorCode.MAPPING_ERROR, e.getMessage());
        }
    }

    private static String addOffset(String dateTime) {

        if (dateTime == null || dateTime.isBlank()) {
            return dateTime;
        }

        return LocalDateTime.parse(dateTime)
                .atOffset(ZoneOffset.ofHoursMinutes(5, 30))
                .withOffsetSameInstant(ZoneOffset.UTC)
                .toString();
    }


    public static SalesForceEmiRequest mapToSalesforceEmiDto(SalesForceEmiRequest dto) {
        String crmId = null;
        if (dto.getPolicyNumber() != null && dto.getInstallmentNumber() != null) {
            crmId = dto.getPolicyNumber() + "_" + dto.getInstallmentNumber();
        }
        dto.setCrmId(crmId);

        if (dto.getMandate() != null && dto.getMandate().getStatus() != null) {

            String mappedStatus = MANDATE_STATUS_MAP.entrySet()
                    .stream()
                    .filter(entry -> entry.getValue().contains(dto.getMandate().getStatus()))
                    .map(Map.Entry::getKey)
                    .findFirst()
                    .orElse("UNKNOWN");

            dto.getMandate().setStatus(mappedStatus);
        }

        if (dto.getPayment() != null && dto.getPayment().getPaymentLinkType() != null) {

            String currentType = dto.getPayment().getPaymentLinkType();
            String mappedStatus = INSTALLMENT_STATUS_MAP.getOrDefault(currentType, currentType);
            dto.getPayment().setPaymentLinkType(mappedStatus);
        }

        if (dto.getPayment() != null) {
            dto.getPayment().setCreatedDate(addOffset(dto.getPayment().getCreatedDate()));
            dto.getPayment().setPaymentDate(addOffset(dto.getPayment().getPaymentDate()));
        }

        if (dto.getReceipt() != null) {
            dto.getReceipt().setCreatedDate(addOffset(dto.getReceipt().getCreatedDate()));
        }

        if (dto.getMandate() != null) {
            dto.getMandate().setCreatedDate(addOffset(dto.getMandate().getCreatedDate()));
        }

        if (dto.getPayment()!=null && dto.getPayment().getCreatedDate()!=null){
            dto.getPayment().setMandatePresentationDate(addOffset(dto.getPayment().getCreatedDate()));
        }

        return dto;
    }

    public static SalesforceEndorsementRequestDto mapToSalesforceEndorsementDto(EndorsementDto dto) {
        log.info("[SalesforceEndorsementRequestDto] @mapToSalesforceEndorsementDto dto : {}", dto);
        if (dto == null || dto.getEndorsementProperties() == null || dto.getEndorsementProperties().isEmpty()) {
            return null;
        }
        try {
            EndorsementDto.EndorsementPropertyDto endorsement = dto.getEndorsementProperties().getFirst();
            if (endorsement == null || !isCancellationEndorsement(endorsement.getEndorsementCode())) {
                return null;
            }

            LocalDate cancellationDate = endorsement.getEndorsementEffectiveDate().toLocalDate();
            String endorsementType = endorsement.getEndorsementCode();
            String cancellationReason = endorsement.getEndorsementName();

            return SalesforceEndorsementRequestDto.builder()
                    .policyDetails(
                            SalesforceEndorsementRequestDto.PolicyDetails.builder()
                                    .policyNumber(dto.getPolicyNumber())
                                    .policyCancellationDate(cancellationDate)
                                    .cancellationEndorsementType(endorsementType)
                                    .cancellationReason(cancellationReason)
                                    .build()
                    )
                    .build();
        } catch (Exception e) {
            log.error("[SalesforceEndorsementRequestDto] Error mapping PremiumEndorsementDto: {}", e.getMessage(), e);
            throw new ClientNonRetryableException(ErrorCode.MAPPING_ERROR, e.getMessage());
        }
    }


    private static boolean isCancellationEndorsement(String endorsementCode) {
        if (!StringUtils.hasText(endorsementCode)) {
            return false;
        }

        try {
            CancellationEndorsementCode.valueOf(endorsementCode.trim().toUpperCase());
            return true;
        } catch (IllegalArgumentException ex) {
            return false;
        }
    }

    public static String toDateOnly(String dateTime) {
        if (dateTime == null || dateTime.trim().isEmpty()) {
            return null;
        }

        DateTimeFormatter input = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss.S");
        DateTimeFormatter output = DateTimeFormatter.ofPattern("yyyy-MM-dd");

        try {
            LocalDateTime ldt = LocalDateTime.parse(dateTime, input);
            return ldt.format(output);
        } catch (Exception ex) {
            return null;
        }
    }

    public static SalesForceProposalUpdateRequestDto mapToSalesforceWorkflowDto(WorkflowDto dto) {
        if (dto == null) {
            return null;
        }

        String cmuStatus = getFirstStatus(dto.getWorkflowItems(), "CMU Workflow");
        String tvcStatus = getFirstStatus(dto.getWorkflowItems(), "TVC Workflow");


        return SalesForceProposalUpdateRequestDto.builder()
                .key("proposal-default")
                .proposalNo(dto.getProposalNumber())
                .ldPolicystatus(dto.getPolicyStatus()) //need to check
                .cmuStatus(cmuStatus)
                .tvcStatus(tvcStatus)
                .build();


    }


    public static String getFirstStatus(List<WorkflowDto.WorkflowItemDto> items, String taskType) {
        if (items == null || taskType == null) return null;

        return items.stream()
                .filter(Objects::nonNull)
                .filter(w -> w.getTaskType() != null && w.getStatus() != null)
                .filter(w -> w.getTaskType().trim().equalsIgnoreCase(taskType))
                .map(WorkflowDto.WorkflowItemDto::getStatus)
                .findFirst()
                .orElse(null);
    }


    public static SalesForceProposalUpdateRequestDto mapToSalesforceRefundDto(RefundDto dto) {
        if (dto == null) {
            return null;
        }

        return SalesForceProposalUpdateRequestDto.builder()
                .key("proposal-default")
                .proposalNo(dto.getProposalNumber())
                .refundStatus(dto.getVerificationStatus())
                .build();
    }

    public static SalesforceEndorsementRequestDto mapToSalesforcePolicyProposalEndorsementDto(PolicyProposalDto dto) {
        log.info("[SalesforceEndorsementRequestDto] @mapToSalesforcePolicyProposalEndorsementDto dto : {}", dto);
        if (dto == null || dto.getPolicyDetails() == null) {
            return null;
        }

        PolicyDetails policyDetails = dto.getPolicyDetails();

        try {
            String proposerName = null;

            if (policyDetails.getPolicyProperty() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails() != null) {

                String firstName = policyDetails.getPolicyProperty()
                        .getProposerDetails()
                        .getFirstName();

                String middleName = policyDetails.getPolicyProperty()
                        .getProposerDetails()
                        .getMiddleName();

                String lastName = policyDetails.getPolicyProperty()
                        .getProposerDetails()
                        .getLastName();

                proposerName = Stream.of(firstName, middleName, lastName)
                        .filter(StringUtils::hasText)
                        .collect(Collectors.joining(" "));
            }


            String proposalFormNumber = null;

            if (policyDetails.getPolicyProperty() != null &&
                    policyDetails.getPolicyProperty().getSimpleProperty() != null &&
                    !policyDetails.getPolicyProperty().getSimpleProperty().isEmpty() &&
                    policyDetails.getPolicyProperty().getSimpleProperty().getFirst() != null) {

                proposalFormNumber = policyDetails.getPolicyProperty()
                        .getSimpleProperty()
                        .getFirst()
                        .getProposalFormNo();
            }
            String uinNumber = null;
            if (policyDetails.getPolicyProperty() != null &&
                    policyDetails.getPolicyProperty().getSimpleProperty() != null &&
                    !policyDetails.getPolicyProperty().getSimpleProperty().isEmpty() &&
                    policyDetails.getPolicyProperty().getSimpleProperty().getFirst() != null) {

                uinNumber = policyDetails.getPolicyProperty()
                        .getSimpleProperty()
                        .getFirst()
                        .getUinNumber();
            }

            String policyConvertedDate = null;

            if (policyDetails.getPolicyProperty() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails().getPartyProperty() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails().getPartyProperty().getOfficeDetails() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails().getPartyProperty().getOfficeDetails().getInsuredDetails() != null &&
                    !policyDetails.getPolicyProperty().getProposerDetails().getPartyProperty().getOfficeDetails().getInsuredDetails().isEmpty()) {

                policyConvertedDate = policyDetails.getPolicyProperty()
                        .getProposerDetails()
                        .getPartyProperty()
                        .getOfficeDetails()
                        .getInsuredDetails()
                        .getFirst()
                        .getPartyProperty()
                        .getPolicyConvertedTime();
            }

            String proposalCreationDate = null;

            if (policyDetails.getPolicyProperty() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails().getPartyProperty() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails().getPartyProperty().getOfficeDetails() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails().getPartyProperty().getOfficeDetails().getInsuredDetails() != null &&
                    !policyDetails.getPolicyProperty().getProposerDetails().getPartyProperty().getOfficeDetails().getInsuredDetails().isEmpty()) {

                proposalCreationDate = policyDetails.getPolicyProperty()
                        .getProposerDetails()
                        .getPartyProperty()
                        .getOfficeDetails()
                        .getInsuredDetails()
                        .getFirst()
                        .getPartyProperty()
                        .getProposalCreatedDate();
            }

            String status = null;
            if (StringUtils.hasText(policyDetails.getPolicyStatus())) {
                status = STATUS_MAP.get(policyDetails.getPolicyStatus());
            }

            return SalesforceEndorsementRequestDto.builder()
                    .policyDetails(
                            SalesforceEndorsementRequestDto.PolicyDetails.builder()
                                    .proposalFormNumber(proposalFormNumber)
                                    .proposerName(proposerName)
                                    .policyStatus(status)
                                    .policyExpiryDate(toDate(policyDetails.getPolicyExpiryDate()))
                                    .policyInceptionDate(toDate(policyDetails.getPolicyInceptionDate()))
                                    .policyConvertedDate(toDate(policyConvertedDate))
                                    .proposalCreationDate(toDate(proposalCreationDate))
                                    //.proposalNo(policyDetails.getQuotationNumber())
                                    .uinNumber(uinNumber)
                                    .productName(policyDetails.getProductName())
                                    .productCode(policyDetails.getProductCode())
                                    .policyNumber(policyDetails.getPolicyNumber())
                                    .build()
                    )
                    .build();

        } catch (Exception e) {
            log.error("[SalesForceProposalUpdateRequestDto] Error mapping PolicyProposalEndorsementDto: {}", e.getMessage(), e);
            throw new ClientNonRetryableException(ErrorCode.MAPPING_ERROR, e.getMessage());
        }
    }

    public static SalesForceProposalUpdateRequestDto mapToSalesforcePolicyProposalDto(PolicyProposalDto dto) {
        log.info("[SalesForceProposalUpdateRequestDto] @mapToSalesforcePolicyProposalDto dto : {}", dto);

        if (dto == null || dto.getPolicyDetails() == null) {
            return null;
        }

        PolicyDetails policyDetails = dto.getPolicyDetails();

        try {
            String merWaive = null;
            if (policyDetails.getPolicyProperty() != null &&
                    policyDetails.getPolicyProperty().getSimpleProperty() != null &&
                    !policyDetails.getPolicyProperty().getSimpleProperty().isEmpty() &&
                    policyDetails.getPolicyProperty().getSimpleProperty().getFirst() != null) {

                merWaive = policyDetails.getPolicyProperty()
                        .getSimpleProperty()
                        .getFirst()
                        .getMerWaive();
            }

            String issuanceType = ("NO".equalsIgnoreCase(merWaive)) ? "NSTP" : "STP";

            Double totalPremium = 0.0;
            String totalPremiumStr = policyDetails.getTotalPremium();
            if (StringUtils.hasText(totalPremiumStr)) {
                try {
                    totalPremium = Double.parseDouble(totalPremiumStr.trim());
                } catch (NumberFormatException e) {
                    log.warn("Invalid totalPremium: {}", totalPremiumStr);
                }
            }

            String branchOfficeCode = null;
            if (policyDetails.getPolicyProperty() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails().getPartyProperty() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails().getPartyProperty().getOfficeDetails() != null) {

                String officeCode = policyDetails.getPolicyProperty()
                        .getProposerDetails()
                        .getPartyProperty()
                        .getOfficeDetails()
                        .getOfficeCode();

                if (StringUtils.hasText(officeCode)) {
                    branchOfficeCode = officeCode;
                }
            }

            String customerPartyCode = null;
            if (policyDetails.getPolicyProperty() != null &&
                    policyDetails.getPolicyProperty().getProposerDetails() != null) {

                String partyCode = policyDetails.getPolicyProperty()
                        .getProposerDetails()
                        .getPartyCode();

                if (StringUtils.hasText(partyCode)) {
                    customerPartyCode = partyCode;
                }
            }

            String status = null;
            if (StringUtils.hasText(policyDetails.getPolicyStatus())) {
                status = STATUS_MAP.get(policyDetails.getPolicyStatus());
            }

            return SalesForceProposalUpdateRequestDto.builder()
                    .key("proposal-default")
                    .proposalNo(policyDetails.getQuotationNumber())
                    .policyNo(policyDetails.getPolicyNumber())
                    .branchOfficeCode(branchOfficeCode)
                    .policyName(policyDetails.getProductName())
                    .issuanceType(issuanceType)
                    .totalPremium(totalPremium)
                    .policyStartDate(toDate(policyDetails.getPolicyInceptionDate()))
                    .policyEndDate(toDate(policyDetails.getPolicyExpiryDate()))
                    .policyTenure(policyDetails.getPolicyDuration())
                    .installmentFrequency(policyDetails.getPaymentFrequency())
                    .customerPartyCode(customerPartyCode)
                    .status(status)
                    .build();

        } catch (Exception e) {
            log.error("[SalesForceProposalUpdateRequestDto] Error mapping PolicyProposalDto: {}", e.getMessage(), e);
            throw new ClientNonRetryableException(ErrorCode.MAPPING_ERROR, e.getMessage());
        }
    }


    public static String toDate(String dateTime) {
        if (dateTime == null || dateTime.trim().isEmpty()) {
            return null;
        }

        DateTimeFormatter inputFormat = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm:ss");
        DateTimeFormatter outputFormat = DateTimeFormatter.ofPattern("yyyy-MM-dd");

        try {
            LocalDateTime ldt = LocalDateTime.parse(dateTime, inputFormat);
            return ldt.format(outputFormat);
        } catch (Exception ex) {
            return null;
        }
    }


    public static CreateLeadRequestDto mapToCreateLeadRequestDto(D2CLeadDetailsCreateDTO dto) {
        if (dto == null) {
            return null;
        }

        NameDto nameDto = new NameDto();
        splitName(dto.getLastName(), nameDto);

        return CreateLeadRequestDto.builder()
                .firstName(
                        (dto.getFirstName() != null && !dto.getFirstName().isEmpty())
                                ? dto.getFirstName()
                                : nameDto.getFirstName()
                )
                .middleName(
                        (dto.getMiddleName() != null && !dto.getMiddleName().isEmpty())
                                ? dto.getMiddleName()
                                : nameDto.getMiddleName()
                )
                .lastName(nameDto.getLastName())
                .email(dto.getEmail())
                .mobile(dto.getMobile())
                .officeCode(dto.getOfficeCode())
                .preferredLanguage(dto.getPreferredLanguage())
                .productCode(dto.getProductCode())
                .productName(dto.getProductName())
                .quoteId(dto.getQuoteId())
                .policyNo(dto.getPolicyNo())
                .proposalNo(dto.getProposalNo())
                .recordReceivedFromSystem(dto.getRecordReceivedFromSystem())
                .updatedSourceThrough(dto.getUpdatedSourceThrough())
                .urlInfo(dto.getUrlInfo())
                .websiteLeadId(dto.getWebsiteLeadId())
                .zipCode(dto.getZipCode())
                .premiumAmount(dto.getPremiumAmount())
                .sumInsured(dto.getSumInsured())
                .assistedBy(dto.getAssistedBy())
                .pedStatus(dto.getPedStatus())
                .policyType(dto.getPolicyType())
                .purchaseMode(dto.getPurchaseMode())
                .preAndPostAgentCode(dto.getPreAndPostAgentCode())
                .websiteAgentCode(dto.getWebsiteAgentCode())
                .branchCode(dto.getBranchCode())
                .policyTerm(dto.getPolicyTerm())
                .emiAmount(dto.getEmiAmount())
                .utmMedium(dto.getUtmMedium())
                .income(dto.getIncome())
                .utmCampaignKeyword(dto.getUtmCampaignKeyword())
                .utmCampaign(dto.getUtmCampaign())
                .utmSource(dto.getUtmSource())
                .utmContent(dto.getUtmContent())
                .utmTerm(dto.getUtmTerm())
                .faCode(dto.getFaCode())
                .faLocation(dto.getFaLocation())
                .faCallingTime(dto.getFaCallingTime())
                .trackierId(dto.getTrackierId())
                .isOffline(dto.getIsOffline())
                .otpVerified(String.valueOf(dto.getOtpVerified()))
                .gender(dto.getGender())
                .prospectDob(dto.getProspectDob())
                .insuredDetails(dto.getInsuredDetails())
                .familySize(dto.getFamilySize())
                .referralCustomer(dto.getReferralCustomer())
                .referrerName(dto.getReferrerName())
                .referrerPolicyNo(dto.getReferrerPolicyNo())
                .referrerPhone(dto.getReferrerPhone())
                .referredByMobileNumber(dto.getReferredByMobileNumber())
                .referrerCustomerPolicyNo(dto.getReferrerCustomerPolicyNo())
                .referredCustomerRegisteredPhoneNo(dto.getReferredCustomerRegisteredPhoneNo())
                .referredCustomerRegisteredEmailId(dto.getReferredCustomerRegisteredEmailId())
                .countryPrefix(dto.getCountryPrefix())
                .countryCode(dto.getCountryCode())
                .fbclid(dto.getFbclid())
                .gclid(dto.getGclid())
                .leadComeThrough(dto.getLeadComeThrough())
                .leadSource(dto.getLeadSource())
                .leadStageInWebsite(dto.getLeadStageInWebsite())
                .country(dto.getCountry())
                .utmSourceSeo(dto.getUtmSourceSeo())
                .name(dto.getName())
                .systemKey(dto.getSystemKey())
                .zohoLeadId(dto.getZohoLeadId())
                .proposalProposerName(dto.getProposalProposerName())
                .proposalFamilySize(dto.getProposalFamilySize())
                .proposalProposerDob(dto.getProposalProposerDob())
                .proposalHighestMemberDob(dto.getProposalHighestMemberDob())
                .proposalHighestMemberAge(dto.getProposalHighestMemberAge())
                .proposalGender(dto.getProposalGender())
                .proposalPhoneNo(dto.getProposalPhoneNo())
                .proposalEmailId(dto.getProposalEmailId())
                .proposalOccupation(dto.getProposalOccupation())
                .proposalIncome(dto.getProposalIncome())
                .proposalAddress(dto.getProposalAddress())
                .proposalPincode(dto.getProposalPincode())
                .proposalState(dto.getProposalState())
                .proposalDistrict(dto.getProposalDistrict())
                .proposalCity(dto.getProposalCity())
                .proposalSumInsured(dto.getProposalSumInsured())
                .proposalRidersSelected(dto.getProposalRidersSelected())
                .utmSubSource(dto.getUtmSubSource())
                .utmAdSetName(dto.getUtmAdSetName())
                .utmDevice(dto.getUtmDevice())
                .utmUrlLink(dto.getUtmUrlLink())
                .utmCreateDesign(dto.getUtmCreateDesign())
                .utmPageType(dto.getUtmPageType())
                .paymentLink(dto.getPaymentLink())
                .paymentLinkCreatedDateTime(dto.getPaymentLinkCreatedDateTime())
                .paymentDateTime(dto.getPaymentDateTime())
                .healthFreshSource(dto.getHealthFreshSource())
                .build();
    }

    /**
     * Map a full D2C payload into a list of Salesforce DTOs.
     */
    public static UpdateLeadOrBuyingJourneyRequestDto mapToSalesforceUpdateDto(D2CLeadDetailsUpdateDTO dto) {
        UpdateLeadOrBuyingJourneyRequestDto resultDto = new UpdateLeadOrBuyingJourneyRequestDto();
        if (dto == null || dto.getData() == null) {
            return resultDto;
        }

        for (LeadDataDto lead : dto.getData()) {
            resultDto.getData().add(mapSingleLead(lead));
        }
        return resultDto;
    }

    /**
     * Map a single lead record into Salesforce DTO.
     */
    private static UpdateLeadOrBuyingJourneyRequestDto.UpdateLeadOrBuyingJourneyRequestDtoData mapSingleLead(
            LeadDataDto lead) {
        if (lead == null) return null;

        NameDto nameDto = new NameDto();
//        splitName(lead.getLastName(), nameDto);

        return UpdateLeadOrBuyingJourneyRequestDto.UpdateLeadOrBuyingJourneyRequestDtoData.builder()
                // Prospect details
                .id(lead.getId())
                .leadId(lead.getLeadId())
                .leadUniqueId(lead.getLeadUniqueId())
                .ltId(lead.getLtId())
                .zohoLeadId(lead.getZohoLeadId())
                .prospectDob(lead.getProspectDob())
                .gender(lead.getGender())
                .insuredDetails(lead.getInsuredDetails())
                .familySize(lead.getFamilySize())

                // Product details
                .productName(lead.getProductName())
                .productCode(lead.getProductCode())
                .quoteId(lead.getQuoteId())

                // Policy details
                .policyNo(lead.getPolicyNo())
                .proposalNo(lead.getProposalNo())
                .premiumAmount(lead.getPremiumAmount())
                .sumInsured(lead.getSumInsured())
                .policyTerm(lead.getPolicyTerm())
                .policyType(lead.getPolicyType())
                .purchaseMode(lead.getPurchaseMode())
                .officeCode(lead.getOfficeCode())
                .branchCode(lead.getBranchCode())
                .websiteAgentCode(lead.getWebsiteAgentCode())
                .preAndPostAgentCode(lead.getPreAndPostAgentCode())
                .preferredLanguage(lead.getPreferredLanguage())
                .recordReceivedFromSystem(lead.getRecordReceivedFromSystem())
                .updatedSourceThrough(lead.getUpdatedSourceThrough())
                .urlInfo(lead.getUrlInfo())
                .zipCode(lead.getZipCode())

                // PED details
                .pedStatus(lead.getPedStatus())
                .pedList(lead.getPedList())

                // Payment details
                .emiAmount(lead.getEmiAmount())
                .paymentLink(lead.getPaymentLink())
                .paymentLinkCreatedDateTime(lead.getPaymentLinkCreatedDateTime())
                .paymentDateTime(lead.getPaymentDateTime())

                // Proposal details
                .proposalProposerName(lead.getProposalProposerName())
                .proposalFamilySize(lead.getProposalFamilySize())
                .proposalProposerDob(lead.getProposalProposerDob())
                .proposalHighestMemberDob(lead.getProposalHighestMemberDob())
                .proposalHighestMemberAge(lead.getProposalHighestMemberAge())
                .proposalGender(lead.getProposalGender())
                .proposalPhoneNo(lead.getProposalPhoneNo())
                .proposalEmailId(lead.getProposalEmailId())
                .proposalOccupation(lead.getProposalOccupation())
                .proposalIncome(lead.getProposalIncome())
                .proposalAddress(lead.getProposalAddress())
                .proposalPincode(lead.getProposalPincode())
                .proposalState(lead.getProposalState())
                .proposalDistrict(lead.getProposalDistrict())
                .proposalCity(lead.getProposalCity())
                .proposalSumInsured(lead.getProposalSumInsured())
                .proposalRidersSelected(lead.getProposalRidersSelected())

                // Referral info
                .referralCustomer(lead.getReferralCustomer())
                .referredByMobileNumber(lead.getReferredByMobileNumber())
                .referrerCustomerPolicyNo(lead.getReferrerCustomerPolicyNo())
                .referredCustomerRegisteredPhoneNo(lead.getReferredCustomerRegisteredPhoneNo())
                .referredCustomerRegisteredEmailId(lead.getReferredCustomerRegisteredEmailId())

                // Contact info
                .email(lead.getEmail())
                .mobile(lead.getMobile())
//                .firstName(lead.getFirstName() != null ? lead.getFirstName() : nameDto.getFirstName())
//                .middleName(lead.getMiddleName()!=null ? lead.getMiddleName(): nameDto.getMiddleName())
//                .lastName(lead.getLastName() != null ? lead.getLastName() : nameDto.getLastName())
                .firstName(lead.getFirstName())
                .lastName(lead.getLastName())
                .middleName(lead.getMiddleName())
                // Journey infok,.
                .leadSource(lead.getLeadSource())
                .leadComeThrough(lead.getLeadComeThrough())
                .leadStageInWebsite(lead.getLeadStageInWebsite())
                .assistedBy(lead.getAssistedBy())
                .systemKey(lead.getSystemKey())
                .websiteLeadId(lead.getWebsiteLeadId())

                // UTM tracking
                .utmCampaignKeyword(lead.getUtmCampaignKeyword())
                .utmCampaign(lead.getUtmCampaign())
                .utmContent(lead.getUtmContent())
                .utmMedium(lead.getUtmMedium())
                .utmSource(lead.getUtmSource())
                .utmTerm(lead.getUtmTerm())
                .utmSubSource(lead.getUtmSubSource())
                .utmAdSetName(lead.getUtmAdSetName())
                .utmDevice(lead.getUtmDevice())
                .utmUrlLink(lead.getUtmUrlLink())
                .utmCreateDesign(lead.getUtmCreateDesign())
                .utmPageType(lead.getUtmPageType())
                .utmSourceSeo(lead.getUtmSourceSeo())

                // Misc
                .otpVerified(String.valueOf(lead.getOtpVerified()))
                .fbclid(lead.getFbclid())
                .gclid(lead.getGclid())
                .customerPartyCode(lead.getCustomerPartyCode())
                .countryPrefix(lead.getCountryPrefix())
                .countryCode(lead.getCountryCode())
                .country(lead.getCountry())
                .build();
    }

    /**
     * logic added to handle spliting of complete name in first,lastname basis
     *
     * @param fullName
     * @param nameDto
     */
    private static void splitName(String fullName, NameDto nameDto) {
        if (Strings.isBlank(fullName)) {
            log.warn("lastName is null");
            return;
        }
        fullName = fullName.trim().replaceAll("\\s+", " ");
        String[] nameChunks = fullName.split(" ");
        if (nameChunks.length == 1) {
            nameDto.setLastName(nameChunks[0]);
        } else if (nameChunks.length == 2) {
            nameDto.setFirstName(nameChunks[0]);
            nameDto.setLastName(nameChunks[nameChunks.length - 1]);
        } else {
            nameDto.setFirstName(nameChunks[0]);
            nameDto.setLastName(nameChunks[nameChunks.length - 1]);
            // Join everything between first and last as middle
            nameDto.setMiddleName(
                    String.join(" ", java.util.Arrays.copyOfRange(nameChunks, 1, nameChunks.length - 1)));
        }
    }
}package com.star.eps.eps_crm_subscriber.service.processor.impl;


import com.star.eps.eps_crm_subscriber.client.EmiManagerClient;
import com.star.eps.eps_crm_subscriber.dto.request.SalesForceEmiRequest;
import com.star.eps.eps_crm_subscriber.dto.response.SalesForceEmiResponse;
import com.star.eps.eps_crm_subscriber.enums.ErrorCode;
import com.star.eps.eps_crm_subscriber.exception.ClientNonRetryableException;
import com.star.eps.eps_crm_subscriber.exception.ClientRetryableException;
import com.star.eps.eps_crm_subscriber.service.processor.EventProcessor;
import com.star.eps.eps_crm_subscriber.util.DataMapperUtil;
import com.star.eps.eps_crm_subscriber.util.ObjectMapperUtil;
import com.star.eps.eps_subscriber_retry.dto.SubscriberRequest;
import lombok.RequiredArgsConstructor;
import lombok.extern.slf4j.Slf4j;
import org.springframework.stereotype.Component;

import static com.star.eps.eps_crm_subscriber.util.LogConstants.SUCCESS;

@Slf4j
@RequiredArgsConstructor
@Component
public class EmiManagerProcessor extends EventProcessor {

    private final EmiManagerClient emiManagerClient;

    @Override
    public void process(SubscriberRequest request) {
        try {
            SalesForceEmiRequest emiDetails = ObjectMapperUtil.convertObject(
                    request.getPayload(), SalesForceEmiRequest.class);
            SalesForceEmiRequest emiDetailsPayload = DataMapperUtil.mapToSalesforceEmiDto(emiDetails);

            log.info("[EmiManagerProcessor] Sending Update lead details to Salesforce: {}", emiDetailsPayload);

            SalesForceEmiResponse response = emiManagerClient.sendEmiDetailsToSalesForce(emiDetailsPayload);

            if (SUCCESS.equalsIgnoreCase(response.getStatus())) {
                log.info("[EmiManagerProcessor] Emi Details updated for the event: {}", response.getEvent());
            } else {
                log.warn("[EmiManagerProcessor]  event: {},status: {}, message:{}", response.getEvent(), response.getStatus(), response.getMessage());
                throw new ClientNonRetryableException(ErrorCode.EMI_UPDATE_ERROR, response.getMessage());
            }

        } catch (ClientNonRetryableException e) {
            log.error("[EmiManagerProcessor] Non-retryable error: {}", e.getMessage(), e);
            throw e;
        } catch (ClientRetryableException e) {
            log.warn("[EmiManagerProcessor] Retryable error: {}", e.getMessage(), e);
            throw e;
        } catch (Exception e) {
            log.error("[EmiManagerProcessor] Unexpected error occurred", e);
            throw new ClientNonRetryableException(ErrorCode.CRM_BAD_REQUEST, e.getMessage());
        }
    }
}

{
  "event": "MANDATE_PRESENTED",
  "policyNumber": "9304112700081188",
  "installmentNumber": 3,
  "policyStatus": "ACTIVE_POLICY",
  "payment": {
    "status": "PENDING",
    "paymentSource": "MANDATE",
    "paymentAmount": 1501.583,
    "refundAmount": null,
    "paymentLinkType": null,
    "paymentUrl": null,
    "createdDate": "2026-08-05T19:32:05.360754135",
    "paymentDate": null,
    "refundDate": null,
    "error": null
  },
  "receipt": null,
  "mandate": null
}
