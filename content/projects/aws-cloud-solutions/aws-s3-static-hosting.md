---
title: "🌐 Hosting a Static Website on AWS S3"
date: 2025-05-10
tags: ["AWS", "S3", "Web Hosting"]
cover:
  image: "/images/aws-s3-cover.png"
  alt: "AWS S3 Static Website"
draft: false
---

📝 **Project Overview**  
In this project, I deployed a fully functional static website using Amazon S3 (Simple Storage Service). This task introduced me to cloud-based storage, object permissions, and static site hosting—core skills for cloud computing and web deployment.

---

🎯 **Objectives**
- Learn how to create and configure an S3 bucket  
- Upload and serve static content (HTML, CSS)  
- Set object-level permissions for public access  
- Enable static website hosting on S3  

---

🛠️ **Tools & Technologies**
- Amazon S3  
- HTML / CSS  

---

## 🧪 Steps Followed

### 1. Created an S3 Bucket
- Named the bucket with a unique name  
- Disabled “Block all public access” to allow website visitors  

---

### 2. Uploaded Website Files
Files included:
- `index.html`: Homepage  
- `style.css`: Page styling  
- `error.html`: Custom 404 error page  

📸  
![Uploaded Files](/images/aws/uploaded-files.png)

---

### 3. Enabled Static Website Hosting
- Enabled the static website option in the bucket properties  
- Set `index.html` as the default page  
- Added `error.html` as the error document  

📸  
![Static Website Hosting Enabled](/images/aws/static-hosting.png)

---

### 4. Set Bucket Policy for Public Access

```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Principal": "*",
    "Action": "s3:GetObject",
    "Resource": "arn:aws:s3:::brianscloudcraft/*"
  }]
}
```

---

### 5. Accessed the Live Site
Used the S3 website endpoint URL to access the live static website

📸  
![Accessed the Live Site](/images/aws/aws-s33.png)

---

💡 What I Learned
S3 buckets can serve as simple, cost-effective static web hosts
Managing file permissions is crucial for public accessibility
Cloud hosting doesn’t always require complex server setups.
HERE ARE THE FILES I UPLOADED TO THE BUCKET

You can get them on my github repository:

error.html
index.html
style.css
https://github.com/Bnjenga1/brianscloudcraft