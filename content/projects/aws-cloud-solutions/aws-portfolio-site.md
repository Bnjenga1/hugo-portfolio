---
title: "Hosting a Professional Portfolio Website on AWS with Hugo"
date: 2025-06-26T12:00:00+03:00
tags: ["AWS", "S3", "CloudFront", "Hugo", "CI/CD", "GitHub Actions"]
description: "How I built and deployed my personal portfolio site using Hugo, AWS S3, CloudFront, Route 53, and GitHub Actions."
draft: false
---

I built and deployed this portfolio website to showcase my projects and experience as a data analyst and cloud enthusiast. The site is powered by Hugo (a fast static site generator) and hosted entirely on AWS. It features a professional contact form, clean layout, dark/light theme support, and fully automated deployment.

---

## 🚀 What I Did

### 🏗️ Site Setup with Hugo
- Used the **PaperMod** theme for a clean and responsive design  
- Created pages for blog posts, project case studies, and an about page  
- Customized the config file for metadata, theme options, and menu items  

### 🌐 AWS Hosting
- **S3 Buckets**:  
  - `www.brianmwaura.com` (main bucket with website files)  
  - `brianmwaura.com` (redirect bucket)  
  - `brians-portfolio-site` (legacy/test bucket)  
- **Route 53**:  
  - Managed domain registration and DNS records  
- **CloudFront**:  
  - Delivered content globally with HTTPS (SSL via ACM)  
  - Handled root redirects and caching  

### 🔁 GitHub Actions for CI/CD
- Set up GitHub repo: [`Bnjenga1/hugo-portfolio`](https://github.com/Bnjenga1/hugo-portfolio)  
- Created a workflow to:  
  - Build site with Hugo  
  - Upload `public/` directory to S3  
  - Invalidate CloudFront cache  

### 📬 Contact Page + Email
- Built a custom contact form using **Formspree** with JavaScript for UX improvements  
- Set up a professional email alias `info@brianmwaura.com` via Google Workspace  
- Ensured form styling adapts to both light and dark themes  

### 📊 SEO, Analytics & Monitoring
- Connected the site to **Google Analytics 4**  
- Submitted `sitemap.xml` to **Google Search Console**  
- Added Open Graph and meta tags for better sharing and visibility  

---

## 🧰 Tools & Services Used
- **Static Generator**: Hugo  
- **Hosting**: AWS S3 + CloudFront  
- **CI/CD**: GitHub Actions  
- **Domain Management**: Route 53  
- **Email**: Google Workspace + Formspree  
- **Analytics**: GA4 + Search Console  

---

## 💡 Key Takeaways
- Learned to configure static hosting and CDN on AWS  
- Set up secure and scalable infrastructure for a real-world personal project  
- Practiced debugging Hugo layouts and customizing themes  
- Automated deployments and version control with GitHub  
- Improved UX with clean forms, responsive design, and reliable email contact  

---

## 🔗 Live Demo
👉 [www.brianmwaura.com](https://www.brianmwaura.com)

---

If you'd like to build something similar, feel free to fork the repo or reach out via my [contact page](/contact/).
