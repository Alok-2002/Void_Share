# 🌐 TempDrive – Temporary File Sharing Platform (AWS Cloud-Native)

![AWS](https://img.shields.io/badge/Platform-AWS-orange?style=for-the-badge\&logo=amazonaws)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-In%20Development-blue?style=for-the-badge)
![Language](https://img.shields.io/badge/Built%20With-JavaScript%20%26%20Python-yellow?style=for-the-badge\&logo=javascript)
![Visitors](https://visitor-badge.laobi.icu/badge?page_id=TempDrive-Repo)
![PRs](https://img.shields.io/badge/PRs-Welcome-brightgreen?style=for-the-badge)
![Stars](https://img.shields.io/github/stars/alok-2002/void_share?style=for-the-badge)

---

## 📌 Project Overview

**TempDrive** is a secure, cloud-native file sharing platform that allows users to upload any type of file, choose how long it stays available (1 hour to 5 years), and automatically deletes it after expiry. Built entirely using **AWS services**, it ensures privacy, scalability, and low maintenance with **zero backend server management**.

---

## 🚀 Features

* 👤 User authentication using AWS Cognito
* 🔐 Per-user isolated file storage on S3
* ⏱️ Custom file expiry from 1 hour to 5 years
* 🧹 Auto-deletion of expired files using EventBridge & Lambda
* 📄 Public and private file sharing
* 📬 (Optional) Email notifications before expiry
* 📱 Responsive modern UI built with React
* 🌩️ Fully deployed and hosted on AWS

---

## ⚙️ Tech Stack

| Layer            | Technology                |
| ---------------- | ------------------------- |
| Frontend         | React.js, Tailwind CSS    |
| Hosting          | Amazon S3 + CloudFront    |
| Authentication   | Amazon Cognito            |
| Backend APIs     | AWS Lambda + API Gateway  |
| File Storage     | Amazon S3                 |
| Metadata DB      | Amazon DynamoDB           |
| Expiry & Cleanup | AWS EventBridge + Lambda  |
| Email Service    | Amazon SES (optional)     |
| Infrastructure   | AWS CLI / Terraform / CDK |

---

## 🧱 System Architecture

![Architecture Diagram](./assets/architecture.png)

---

## 💸 Cost Estimation

| Service            | Approx. Monthly Cost       |
| ------------------ | -------------------------- |
| S3 (Storage <20GB) | \$1–\$5                    |
| Lambda             | <\$1                       |
| API Gateway        | <\$1                       |
| Cognito            | Free (<50k users)          |
| DynamoDB           | <\$1                       |
| CloudFront + S3    | Free / <\$1                |
| SES (Optional)     | Free (up to 62,000 emails) |

> 💰 Total: **\~\$5/month average** (Free under light use). You can scale further with your **\$180 AWS credits**.

---

## 🔐 File Security & Access Control

* Files are uploaded under `uploads/{user_id}/filename.ext`
* IAM policies ensure only the file owner can read/delete their files
* All requests are token-secured using JWTs from Cognito
* Public files can be shared via a link; private files require login

---

## 📁 Folder Structure

```
tempdrive/
├── backend/
│   ├── lambda-upload.js
│   ├── lambda-delete.js
│   ├── lambda-cleanup.js
│   └── terraform/
├── frontend/
│   ├── public/
│   └── src/
│       ├── components/
│       └── pages/
├── assets/
│   └── architecture.png
├── README.md
```

---

## 📄 Upload & Expiry Flow

1. User logs in via Cognito
2. Selects file and expiry time (1 hour to 5 years)
3. File is uploaded to S3 and metadata stored in DynamoDB
4. Expiry timestamp is stored in DynamoDB TTL
5. Lambda checks and deletes expired files daily via EventBridge

---

## 🧪 Future Upgrades

* [ ] Password-protected file links
* [ ] Drag-and-drop interface
* [ ] QR code generator
* [ ] Analytics dashboard for users
* [ ] Extend/renew expiry before deletion

---

## 🌍 Deployment (100% on AWS)

```bash
# Deploy Frontend
aws s3 sync ./frontend/build s3://your-frontend-bucket/
aws cloudfront create-invalidation --distribution-id YOUR_DIST_ID --paths "/*"

# Deploy Backend (Lambda + API Gateway)
terraform init
terraform apply
```

---

## 👨‍💻 Developer Info

| Name      | Role                |
| --------- | ------------------- |
| Your Name | Cloud App Developer |

---

## 📌 Useful Links

* 🔗 [AWS Free Tier Info](https://aws.amazon.com/free/)
* 🔗 [Amazon S3 Pricing](https://aws.amazon.com/s3/pricing/)
* 🔗 [DynamoDB TTL Docs](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/TTL.html)
* 🔗 [CloudFront Setup](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.html)

---

## 📸 Screenshots (Placeholders)

| Upload Page                   | File List                   | Expiry Selector                   |
| ----------------------------- | --------------------------- | --------------------------------- |
| ![](./assets/upload-page.png) | ![](./assets/file-list.png) | ![](./assets/expiry-selector.png) |

---

## 📜 License

This project is licensed under the [MIT License](./LICENSE).

---

## 🙌 Contributing

PRs are welcome! Open issues, fork the repo, and create a pull request. Let’s build this awesome tool together.

---

## ⭐ Show Your Support

Give a ⭐️ if this project helped you or inspired you!
