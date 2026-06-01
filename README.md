# AWS Static Jewelry Store with CI/CD

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

## Author

ANEES FATIMA

Step 1 — Create the Static Website

index.html
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

---

style.css

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

---

script.js

 function shopNow() {
    alert("Welcome to Luxe Jewelry Store!");
}




