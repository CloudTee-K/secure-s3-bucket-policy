# secure-s3-bucket-policy
A project demonstrating how to secure an AWS S3 bucket with IAM bucket policy using least privilege principles.


This project demonstrates how to securely configure an Amazon S3 bucket by:
- Blocking all public access
- Granting read/write access to a specific IAM user via a bucket policy
- Testing access using the AWS CLI

---
 Project Summary (STAR Method)

S – Situation:  
Needed to secure file uploads in an AWS S3 bucket by allowing access only to an internal IAM user.

T – Task:
Set up a private S3 bucket with a policy that gives `text-user` specific read/write permissions while denying public access.

A – Action:  
- Created and configured an S3 bucket named `my-secure-bucket-cloudtee-k`
- Enabled “Block all public access” in the bucket settings
- Wrote a custom bucket policy granting access to the IAM user using their ARN
- Tested the configuration by uploading a file using AWS CLI

R – Result: 
Successfully uploaded a file using the IAM user. The bucket is now secure and accessible only by authorized users over HTTPS.

---

 Tools & Services
- AWS S3
- AWS IAM
- AWS CLI

 Security Practices Used
- Bucket Policy
- IAM least privilege
- Block public access
- Verified using CLI

 Sample Bucket Policy (Sanitized)
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowReadWriteToSpecificUser",
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::123456789012:user/text-user"
      },
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::my-secure-bucket-cloudtee-k/*"
    }
  ]
}
