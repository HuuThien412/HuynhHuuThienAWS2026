---
title: "Amazon SES"
date: 2026-07-21
weight: 7
chapter: false
pre: "<b>5.3.7 </b>"
---

# Amazon SES

## Introduction

Amazon Simple Email Service (Amazon SES) is a cloud-based email service provided by AWS for sending transactional and notification emails securely and reliably.

The service allows applications to send emails without maintaining a dedicated mail server. It also provides account health monitoring, sender identity verification, sending quotas, and optional delivery tracking features.

In the Campus IT Support Portal project, Amazon SES was configured as a supporting service for email notification functionality. A sender email identity was successfully verified, providing the required foundation for integration with AWS Lambda.

---

## Role in the Project

Amazon SES is intended to support the following email notification scenarios:

- Sending confirmation emails when a ticket is created.
- Sending alerts for High or Critical priority tickets.
- Notifying users when a ticket status changes.
- Delivering administrative notifications to the IT support team.
- Supporting asynchronous email delivery through AWS Lambda.

The current SES account is operating in the Sandbox environment. Therefore, email delivery is currently limited to verified sender and recipient identities.

---

## Amazon SES Dashboard

The Amazon SES account dashboard provides an overview of the service status, sending limits, account health, and current operating environment.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.7-Amazon-SES/ses-dashboard.png"
alt="Amazon SES account dashboard"
caption="Figure 5.3.7.1: Amazon SES account dashboard displaying account status and sending limits."
>}}

The dashboard shows that the account is operating in the Asia Pacific (Singapore) Region and remains in the SES Sandbox environment.

It also displays:

- Daily sending quota.
- Maximum email sending rate.
- Account health status.
- Access to reputation metrics.
- Production access information.

The configured account currently supports up to 200 emails within a 24-hour period and a maximum sending rate of one email per second.

---

## Verified Identity

Amazon SES requires sender identities to be verified before they can be used to send emails.

An identity can be either:

- An individual email address.
- A complete email domain.
- A subdomain.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.7-Amazon-SES/verified-identity.png"
alt="Verified Amazon SES sender identity"
caption="Figure 5.3.7.2: Verified sender identity configured in Amazon SES."
>}}

In this project, a Gmail address was successfully verified as an Amazon SES identity. The verified status confirms that the address is authorized for email delivery through the service.

Because the account is still in Sandbox mode, emails can currently be sent only to other verified email identities. Production access would be required before sending notifications to unrestricted recipients.

---

## Configuration Sets

Amazon SES provides Configuration Sets to manage sending behavior, publish delivery events, and monitor email activity.

Configuration Sets can be used to track events such as:

- Email delivery.
- Rejected messages.
- Bounces.
- Complaints.
- Opens.
- Link clicks.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.7-Amazon-SES/email-configuration.png"
alt="Amazon SES configuration sets"
caption="Figure 5.3.7.3: Amazon SES Configuration Sets for managing email delivery."
>}}

No Configuration Set was created during the current project implementation. The feature remains available for future improvements when advanced email tracking, analytics, or event publishing is required.

The current notification implementation can still use Amazon SES without a Configuration Set for basic transactional email delivery.
