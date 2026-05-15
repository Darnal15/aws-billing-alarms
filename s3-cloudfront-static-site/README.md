# Static Website Hosting with S3 and CloudFront

## Overview
Hosted a static webpage on Amazon S3 and delivered it globally 
through Amazon CloudFront CDN. Configured CloudFront as the only 
access point to the S3 bucket — blocking all direct S3 access and 
ensuring content is served securely through HTTPS from edge locations 
worldwide.

---

## Architecture

---

## Services Used
- Amazon S3
- Amazon CloudFront
- S3 Origin Access Control (OAC)
- AWS Bucket Policies

---

## Objectives Completed

| Objective | Status |
|---|---|
| Create S3 bucket and upload static webpage | ✅ |
| Create CloudFront distribution with S3 as origin | ✅ |
| Block direct S3 access — only allow CloudFront | ✅ |

---

## Step by Step Process

### 1. Created S3 Bucket
- Bucket name: `my-static-website-darnal`
- Region: ap-south-1 (Mumbai)
- Block all public access: **Enabled**
- Uploaded `index.html` with custom HTML/CSS

### 2. Created CloudFront Distribution
- Origin: S3 bucket
- Origin Access Control (OAC): Enabled
- Viewer protocol policy: Redirect HTTP to HTTPS
- Cache policy: CachingOptimized (recommended for S3)
- Default root object: `index.html`
- WAF: Disabled (not required for static site)

### 3. Configured Bucket Policy
- CloudFront automatically updated S3 bucket policy
- Policy allows ONLY CloudFront to read S3 objects
- Direct S3 URL access returns Access Denied

---

## Results

| Test | Result |
|---|---|
| CloudFront URL | ✅ Website loads successfully |
| Direct S3 URL | ❌ Access Denied (as expected) |

---

## Key Concepts Learned

**What is a CDN?**
A Content Delivery Network caches content at edge locations 
worldwide — reducing latency by serving users from the nearest 
location instead of the origin server.

**What is Origin Access Control (OAC)?**
OAC ensures only CloudFront can access your private S3 bucket. 
It replaces the older Origin Access Identity (OAI) method and 
is the current AWS recommended approach.

**What are Bucket Policies?**
JSON documents attached to S3 buckets that define who can access 
the bucket and what actions they can perform. In this project, 
the policy allows only CloudFront's service principal to call 
s3:GetObject.

---

## Screenshots
![Website Live](<img width="902" height="400" alt="Screenshot 2026-05-15 113258" src="https://github.com/user-attachments/assets/d8c095f9-09db-4754-adb8-fe82dba268a6" />
.png)
![S3 Access Denied](<img width="755" height="425" alt="6" src="https://github.com/user-attachments/assets/27807e51-bd79-4b7d-92aa-ec908496e8a3" />
.png)
![CloudFront Distribution](<img width="941" height="373" alt="5" src="https://github.com/user-attachments/assets/bd870506-fd85-45a0-a5cb-c451722671aa" />
.png)
![S3 Bucket](<img width="935" height="392" alt="3" src="https://github.com/user-attachments/assets/a19b3fd5-6ec5-4353-a04d-9244e1d1920c" />
.png)

---

## Key Learnings
- S3 Block Public Access must stay ON — CloudFront accesses 
  via OAC, not public URLs
- CloudFront takes 5-10 minutes to deploy globally after creation
- Default root object must be set to serve index.html automatically
- WAF adds $5+/month — not needed for simple static sites
- Direct S3 URLs return Access Denied confirming security is correct

---
