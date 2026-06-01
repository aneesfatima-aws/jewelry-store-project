# AWS Static Jewelry Store with CI/CD
<img width="1536" height="1024" alt="WhatsApp Image 2026-06-01 at 5 15 32 AM" src="https://github.com/user-attachments/assets/9d2617f2-bcfb-4b20-afe2-5dce87adb35c" />


## Project Overview

This project demonstrates deployment automation of a static jewelry shopping website using AWS and GitHub Actions.

## Architecture

GitHub → GitHub Actions → AWS S3 → CloudFront → Users

## AWS Services Used

- Amazon S3
- CloudFront
- IAM
- GitHub Actions

## Features

- Static website hosting
- Automated CI/CD pipeline
- Global content delivery using CloudFront
- Responsive frontend design

## Technologies Used

- HTML
- CSS
- JavaScript
- GitHub Actions
- AWS S3

## CI/CD Workflow:

1. Developer pushes code to GitHub
2. GitHub Actions workflow triggers automatically
3. Website files sync to AWS S3
4. CloudFront serves updated content globally

## Learning Outcomes

- Implemented CI/CD pipeline
- Learned AWS S3 static hosting
- Configured IAM credentials securely
- Automated deployments using GitHub Actions

## Future Improvements

- Add shopping cart
- Integrate Stripe payments
- Add product filtering
- Add responsive animations

# Author
# ANEES FATIMA

## Step 1 — Create the Static Website
# index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Luxe Jewelry Store</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
 <header>
        <h1>Luxe Jewelry</h1>
        <nav>
            <a href="#">Home</a>
            <a href="#products">Products</a>
            <a href="#about">About</a>
            <a href="#contact">Contact</a>
        </nav>
    </header>
<section class="hero">
        <h2>Elegant Jewelry for Every Occasion</h2>
        <p>Luxury collections crafted with perfection.</p>
        <button onclick="shopNow()">Shop Now</button>
    </section>
<section id="products" class="products">
        <div class="card">
            <img src="https://images.unsplash.com/photo-1617038220319-276d3cfab638?q=80&w=800" alt="Ring">
            <h3>Diamond Ring</h3>
            <p>$299</p>
        </div>
 <div class="card">
            <img src="https://images.unsplash.com/photo-1617038220319-276d3cfab638?q=80&w=800" alt="Necklace">
            <h3>Gold Necklace</h3>
            <p>$499</p>
        </div>
<div class="card">
            <img src="https://images.unsplash.com/photo-1515562141207-7a88fb7ce338?q=80&w=800" alt="Bracelet">
            <h3>Silver Bracelet</h3>
            <p>$199</p>
        </div>
    </section>
<footer>
        <p>© 2026 Luxe Jewelry Store</p>
    </footer>
<script src="script.js"></script>
</body>
</html>
```

---

#style.css

```css

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    background: #f9f6f2;
    color: #333;
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px 50px;
    background: #111;
    color: white;
}

nav a {
    color: white;
    margin-left: 20px;
    text-decoration: none;
}

.hero {
    text-align: center;
    padding: 100px 20px;
    background: linear-gradient(to right, #f4d03f, #f39c12);
    color: white;
}
.hero h2 {
    font-size: 3rem;
    margin-bottom: 20px;
}

.hero button {
    padding: 12px 25px;
    border: none;
    background: black;
    color: white;
    cursor: pointer;
    margin-top: 20px;
}

.products {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    padding: 50px;
}

.card {
    background: white;
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    text-align: center;
    padding-bottom: 20px;
}

.card img {
    width: 100%;
    height: 250px;
    object-fit: cover;
}

.card h3 {
    margin-top: 15px;
}

footer {
    text-align: center;
    padding: 20px;
    background: #111;
    color: white;
}
```

---

# script.js

 ```
 function shopNow() {
    alert("Welcome to Luxe Jewelry Store!");
}
```

---

Step 2 — Create GitHub Repository

Create a New Repository

Go to GitHub and create:

```
Repository Name:
jewelry-store-project
```

---

Upload Project Files

Open terminal in your project folder.

Initialize Git

```
git init
```
Add Files
```
git add .
```
Commit Files
```
git commit -m "Initial commit"
```
Connect GitHub Repository
```
git remote add origin https://github.com/YOUR-USERNAME/jewelry-store-project.git
```
Push Code
```
git branch -M main

git push -u origin main
```

---

Step 3 — Create AWS S3 Bucket

Open AWS S3

Create bucket:

Bucket Name Example:
`luxe-jewelry-store-123`


---

Bucket Settings

Disable:

Block all public access

Acknowledge warning.


---

Enable Static Website Hosting

Go to:

Properties → Static Website Hosting

Enable:

Host a static website

Set:

Index document:
index.html


---

Step 4 — Add Bucket Policy

Go to:

Permissions → Bucket Policy

Paste this:
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
    }
  ]
}
```
Replace:

`YOUR-BUCKET-NAME`

with your actual bucket name.


---

Step 5 — Create IAM User for GitHub Actions

Create User

Go to:

IAM → Users → Create User

Example:

github-deployer


---

Attach Permissions

Attach:

AmazonS3FullAccess


---

Create Access Keys

Save:

AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY

You will use these inside GitHub secrets.


---
Step 6 — Configure GitHub Secrets

Go to:

`GitHub Repo → Settings → Secrets and Variables → Actions`

Create:

`AWS_ACCESS_KEY_ID`
`AWS_SECRET_ACCESS_KEY`
`AWS_REGION`
`S3_BUCKET`

Example:

`AWS_REGION = us-east-1`
`S3_BUCKET = luxe-jewelry-store-123`


---

Step 7 — Create GitHub Actions Workflow

Create file:

`.github/workflows/deploy.yml`

Add:
```
name: Deploy Static Website to S3

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3

      - name: Configure AWS Credentials
        uses: aws-actions/configure-aws-credentials@v2
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: ${{ secrets.AWS_REGION }}

      - name: Deploy to S3
        run: |
          aws s3 sync . s3://${{ secrets.S3_BUCKET }} --delete
```

---

Step 8 — Push Updated Workflow

Run:
```
git add .

git commit -m "Added GitHub Actions CI/CD workflow"

git push origin main
```

---

Step 9 — Verify Deployment

Go to:

`GitHub → Actions Tab`

You should see:

Workflow completed successfully

Then open:

S3 Static Website Endpoint

Your jewelry website should be live.


---

Step 10 — Configure CloudFront (Optional but Recommended)

Create CloudFront Distribution

Origin:

Select S3 Static Website Endpoint

Enable:

Redirect HTTP to HTTPS


---

Benefits

Faster website globally

HTTPS support

CDN caching

Professional architecture



---
Important AWS Cost Tips

To avoid charges:

Delete unused CloudFront distributions

Delete unused S3 buckets

Stay within free tier limits

Avoid large AWS services for now



