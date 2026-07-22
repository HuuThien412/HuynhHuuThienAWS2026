---
title: "Amazon S3"
date: 2026-07-21
weight: 6
chapter: false
pre: "<b>5.3.6 </b>"
---

## Introduction

Amazon Simple Storage Service (Amazon S3) is the object storage service used to store attachment files uploaded by users.

Instead of saving files directly inside the database, the application stores attachments in Amazon S3 while only keeping the object URL inside DynamoDB. This approach reduces database size and improves scalability.

---

## Role in the Project

Amazon S3 is responsible for:

- Storing ticket attachment files.
- Providing highly durable object storage.
- Generating accessible object URLs.
- Reducing DynamoDB storage requirements.
- Supporting file retrieval from the frontend application.

---

## S3 Bucket

The project uses a dedicated S3 bucket for storing uploaded files.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.6-Amazon-S3/s3-bucket.png"
alt="Amazon S3 bucket"
caption="Figure 5.3.6.1: Amazon S3 bucket used by the project."
>}}

The bucket stores all uploaded attachments and serves as the centralized storage service for the application.

---

## Upload Attachments

Whenever a user submits a ticket with an attachment, AWS Lambda uploads the file into Amazon S3.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.6-Amazon-S3/uploaded-files.png"
alt="Uploaded files"
caption="Figure 5.3.6.2: Uploaded attachment files stored in Amazon S3."
>}}

Only the file URL is stored inside DynamoDB, while the file itself remains in S3.

This design improves performance and reduces database storage usage.

---

## Folder Structure

Uploaded files are organized inside the bucket using a folder prefix.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.6-Amazon-S3/attachment-folder.png"
alt="S3 folder structure"
caption="Figure 5.3.6.3: Folder structure inside the S3 bucket."
>}}

The folder structure makes it easier to manage uploaded files and simplifies future maintenance.

---

## Results

Amazon S3 provides:

- Highly durable object storage.
- Automatic scalability.
- Easy integration with AWS Lambda.
- Efficient attachment management.
- Reduced database storage requirements.
