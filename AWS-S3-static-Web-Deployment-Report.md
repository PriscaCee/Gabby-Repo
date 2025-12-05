# AWS S3 Static Website Deployment – PriscaHomes

*Live Website (HTTPS):* https://priscahomes-2025.s3.eu-north-1.amazonaws.com/index.html  
*GitHub Repository:* https://github.com/PriscaCee/Gabby-Repo  

*Author:* ENUJUBA PRISCA CHIKAMSO | AWS CLOUD COMPUTING | TechCrush Cohort 4 | December 2025  | AWS/2025/TC4/055.

### Introduction.

This project focuses on building a simple static real estate website using HTML5 and CSS3, and deploying it to the cloud using Amazon S3. The aim is to give beginners practical experience with:
- Basic web development  
- Git version control  
- Cloud hosting on S3  
- Static website deployment  

This mirrors the foundational DevOps workflow: Build - Version - Deploy.  

As a learner on my path to AWS Certified Solutions Architect with TechCrush, web design isn't my core skill yet, so I directed Grok (xAI) to generate the code based on my specifications. I handled all Git commands, S3 configurations, and deployment.

### Objectives.

1. Deploy a fully functional static website on AWS S3 as a public site.  
2. Learn the complete S3 static-website workflow: bucket creation, file upload, static hosting, public permissions.  
3. Master the difference between HTTP endpoint and HTTPS object URL.  
4. Understand and fix the 403 Access Denied error using bucket policy (not ACLs). 
5. Practice real Git workflow: init, add, commit, push, replace files, clean history. 
6. Customize a basic site.
7. Document every step and every error for future reference. 

### Pre-requisites.
- Active AWS Free Tier account.  
- Git installed.  
- VS Code (or any code editor).
- Basic understanding of HTML (learned during the process).

### GitHub Workflow.

1. Opened the project folder in VS Code  
2. Initialized the repository  
   bash
   git init
     
3. Added the file index.html  
   bash
   git add index.html
     
4. Committed the changes 
   bash
   git commit -m "AWS S3 Static Website Deployment – PriscaHomes live"
     
5. Linked to my remote GitHub repository  
   bash
   git remote add origin https://github.com/PriscaCee/Gabby-Repo.git
     
6. Renamed branch to main and pushed  
   bash
   git branch -M main
   git push -u origin main
   

### Step-by-Step Deployment Process.

1. **Logged into my AWS Console**  
   I opened https://aws.amazon.com, signed in with my Free Tier account.

2. *Went to S3*  
   Typed “S3” in the search bar at the top - clicked *Amazon S3*.

3. **Created the bucket**  
   - Clicked the  *Create bucket* button.
   - Bucket name: priscahomes-2025 (I had to make sure it was unique). 
   - Region: eu-north-1.
   - Scrolled down - *“Unblocked all public access”*  
   - l ticked the small box that says “I acknowledge…”  
   - Clicked *Create bucket*
<img width="1366" height="768" alt="Bucket-creation" src="https://github.com/user-attachments/assets/036d6314-03fb-48d5-a51e-66eb0994077e" />

4. **Uploaded my index.html**  
   - Clicked on the bucket name priscahomes-2025  
   - Clicked the  *Upload* button  
   - Dragged my final index.html from my laptop and dropped it  
   - Clicked *Upload* → waited → clicked *Close*

<img width="1366" height="768" alt="index-file-upload" src="https://github.com/user-attachments/assets/4608ff6b-577b-4f74-86c9-77367fce9a35" />
5. **Turned on Static Website Hosting**  
   - Inside the bucket → clicked the *Properties* tab  
   - Scrolled all the way down until I saw *Static website hosting*  
   - Clicked *Edit* → chose *Enable*  
   - Typed index.html in the Index document box  
   - Clicked *Save changes*  
   - Copied the endpoint that appeared (http://priscahomes-2025.s3-website.eu-north-1.amazonaws.com)
<img width="1366" height="768" alt="AWS-Static-Web-Hosting" src="https://github.com/user-attachments/assets/d13f050c-1fab-4092-8bac-d12e3c13dcf4" />

6. **Made the bucket public. Then I got an error message the first time**  
   - Clicked the *Permissions* tab  
   - Scrolled to *Bucket policy* - clicked *Edit*  
 - Pasted this exact JSON:

json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::priscahomes-2025/*"
    }
  ]
}


   - Clicked *Save changes*  
   - The 403 error message disappeared after this and l was able to access my site.
<img width="1366" height="768" alt="Bucket-Policy" src="https://github.com/user-attachments/assets/d108aad6-e472-429f-9aa8-06a0b94676a4" />

7. **Got my final live links**  
 - HTTPS (secured):       https://priscahomes-2025.s3.eu-north-1.amazonaws.com/index.html  
  
 - HTTP endpoint:   http://priscahomes-2025.s3-website.eu-north-1.amazonaws.com  
<img width="1366" height="768" alt="Live-Website" src="https://github.com/user-attachments/assets/531555d6-1137-4a69-a758-bf1a18427680" />

*Note on Public Access Method*  
I used the *bucket policy (JSON)* method to make the site public — not the older ACL method.  
This is the current AWS-recommended best practice and gives cleaner, more reliable control.

*JSON is a clear command of:*
Version: tells AWS which policy language to use (2012 format).
Effect: "Allow": gives permission (not deny).
Principal: "*": means “everybody on the internet”.
Action: "s3:GetObject": allows people to read/download files only (no upload or delete).
Resource: it points to all files inside my bucket (priscahomes-2025).

### Problems Encountered & Solutions.

- *403 Access Denied (first time)*  
I forgot to uncheck “Block all public access” when creating the bucket - l went back, unchecked it.

- *403 Access Denied (second time)*  
My site showed “Access Denied” after enabling static hosting - then l added the bucket policy JSON (public read).

- *“Not secure” warning in Chrome*  
The HTTP endpoint showed a red warning - switched to the HTTPS object URL.

- *Got “Invalid principal” error*  
Due to extra spaces/typo in the JSON policy - l fixed the formatting, removed spaces, saved again.

### Conclusion.

I successfully deployed a fully responsive static website on AWS S3 using static website hosting.

And l learned:
- S3 bucket creation and public access setup.
- Static website hosting configuration.
- Bucket policy implementation (JSON method).
- Git commands and push to GitHub.
- Difference between HTTPS object URL and HTTP endpoint.

Live site:  
https://priscahomes-2025.s3.eu-north-1.amazonaws.com/index.html


*PriscaCee | December 2025*
