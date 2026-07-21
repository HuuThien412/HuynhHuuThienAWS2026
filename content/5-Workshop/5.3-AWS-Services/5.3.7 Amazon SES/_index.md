---
title : "Amazon SES"
date : 2026-07-21
weight : 7
chapter : false
pre : " <b> 5.3.7 </b> "
---

Amazon Simple Email Service (Amazon SES) is a cloud-based email service provided by AWS for sending transactional and notification emails. It enables applications to send emails securely without managing their own mail servers.

In the Campus IT Support Portal project, Amazon SES was configured as a supporting service for future email notification functionality. A verified sender identity was created successfully, preparing the system for integration with AWS Lambda to send automated notifications.

---

## Amazon SES Dashboard

The Amazon SES dashboard provides an overview of the account status, sending quota, service health, and sandbox environment. It confirms that the email service has been configured successfully and is ready for future integration.

{{< figure src="/images/5-Workshop/5.3-AWS-Services/5.3.7-Amazon-SES/ses-dashboard.png"
    title="Figure 5.3.7.1: Amazon SES account dashboard displaying account status and sending limits." >}}

The dashboard shows the account status, daily sending quota, maximum send rate, and overall service health.

---

## Verified Identity

Before Amazon SES can send emails, the sender identity must be verified. This process ensures that only authorized email addresses or domains are allowed to send emails through the service.

{{< figure src="/images/5-Workshop/5.3-AWS-Services/5.3.7-Amazon-SES/verified-identity.png"
    title="Figure 5.3.7.2: Verified sender identity configured in Amazon SES." >}}

A Gmail account was successfully verified and configured as the sender identity. Although automatic email delivery has not yet been integrated into the application, the verified identity provides a secure foundation for future implementation.

---

## Configuration Sets

Amazon SES supports Configuration Sets to manage email sending behavior, event publishing, and delivery monitoring. This feature allows developers to organize email sending rules and monitor email events.

{{< figure src="/images/5-Workshop/5.3-AWS-Services/5.3.7-Amazon-SES/email-configuration.png"
    title="Figure 5.3.7.3: Amazon SES Configuration Sets for managing email delivery." >}}

Although no Configuration Set was created during this project, the feature is available for future enhancements when email notifications are integrated into the system.

---

## Results

Amazon SES was successfully configured as part of the Campus IT Support Portal architecture. The verified sender identity demonstrates that the email service is ready for future integration with AWS Lambda.

The implementation provides the following benefits:

- Secure sender identity verification.
- Reliable cloud-based email service.
- Preparation for automated email notifications.
- Easy integration with AWS Lambda.
- Scalable email delivery infrastructure.
