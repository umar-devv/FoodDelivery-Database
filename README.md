# 🍔 Food Delivery Database Management System (MongoDB)

<p align="center">
  <img src="https://img.shields.io/badge/MongoDB-NoSQL-green?style=for-the-badge&logo=mongodb">
  <img src="https://img.shields.io/badge/Database-Project-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge">
  <img src="https://img.shields.io/badge/License-MIT-orange?style=for-the-badge">
</p>

---

## 📖 Introduction

The **Food Delivery Database Management System** is a NoSQL database project developed using **MongoDB**. This project simulates a modern online food delivery platform where customers can browse restaurants, order food, make payments, and receive deliveries through riders.

The project is designed for students, beginners, and developers who want to learn MongoDB database design and implementation through a real-world application. It demonstrates proper database modeling, collection relationships, CRUD operations, aggregation pipelines, and report generation.

---

# 🎯 Project Objectives

The main objectives of this project are:

- Design a complete food delivery database using MongoDB.
- Implement a real-world NoSQL database structure.
- Store and manage customer, restaurant, order, payment, and rider information.
- Perform CRUD operations efficiently.
- Generate useful business reports.
- Practice aggregation pipelines and data analysis.
- Understand document-based database architecture.
- Develop hands-on experience with MongoDB Compass and Mongo Shell.

---

# 🌟 Features

✅ Complete MongoDB Database Project

✅ 6 Interconnected Collections

✅ Realistic Food Delivery Data

✅ Customer Management

✅ Restaurant Management

✅ Menu Item Management

✅ Order Tracking System

✅ Payment Processing Records

✅ Rider Management System

✅ MongoDB Aggregation Pipelines

✅ Report Generation

✅ MongoDB Compass Compatible

✅ Beginner-Friendly Structure

---

# 🏗 System Overview

The Food Delivery System consists of six major entities:

### 👤 Customers
Stores customer information, contact details, city, and spending history.

### 🍽 Restaurants
Stores restaurant details including ratings, cuisine types, and delivery fees.

### 🍕 Menu Items
Contains food products available for customers to order.

### 📦 Orders
Maintains all order transactions and delivery statuses.

### 💳 Payments
Stores payment methods, payment amounts, and transaction statuses.

### 🛵 Riders
Manages delivery personnel information and earnings.

---

# 🗂 Database Collections

## 1️⃣ Customers Collection

Stores customer information.

### Sample Document

```json
{
  "_id": ObjectId(),
  "name": "Ali Khan",
  "email": "ali@gmail.com",
  "phone": "03001234567",
  "city": "Lahore",
  "total_spent": 2500
}
```

### Fields

| Field | Description |
|---------|-------------|
| _id | Unique Customer ID |
| name | Customer Name |
| email | Customer Email |
| phone | Contact Number |
| city | Customer City |
| total_spent | Total Amount Spent |

---

## 2️⃣ Restaurants Collection

Stores restaurant details.

### Sample Document

```json
{
  "_id": ObjectId(),
  "name": "Biryani House",
  "cuisine": "Pakistani",
  "rating": 4.8,
  "delivery_fee": 150,
  "is_open": true
}
```

### Fields

| Field | Description |
|---------|-------------|
| _id | Restaurant ID |
| name | Restaurant Name |
| cuisine | Cuisine Type |
| rating | Customer Rating |
| delivery_fee | Delivery Charges |
| is_open | Availability Status |

---

## 3️⃣ Menu Items Collection

Stores available food items.

### Sample Document

```json
{
  "_id": ObjectId(),
  "name": "Chicken Biryani",
  "category": "Main Course",
  "price": 650,
  "restaurant": "Biryani House"
}
```

### Fields

| Field | Description |
|---------|-------------|
| _id | Menu Item ID |
| name | Food Item Name |
| category | Food Category |
| price | Food Price |
| restaurant | Restaurant Name |

---

## 4️⃣ Orders Collection

Stores customer orders.

### Sample Document

```json
{
  "_id": ObjectId(),
  "customer_name": "Ali Khan",
  "restaurant_name": "Biryani House",
  "items": [
    "Chicken Biryani",
    "Cold Drink"
  ],
  "status": "Delivered",
  "grand_total": 800
}
```

### Fields

| Field | Description |
|---------|-------------|
| _id | Order ID |
| customer_name | Customer Name |
| restaurant_name | Restaurant Name |
| items | Ordered Food Items |
| status | Current Status |
| grand_total | Final Amount |

---

## 5️⃣ Payments Collection

Stores payment records.

### Sample Document

```json
{
  "_id": ObjectId(),
  "method": "Cash",
  "amount": 800,
  "status": "Paid"
}
```

### Fields

| Field | Description |
|---------|-------------|
| _id | Payment ID |
| method | Payment Method |
| amount | Payment Amount |
| status | Payment Status |

---

## 6️⃣ Riders Collection

Stores rider information.

### Sample Document

```json
{
  "_id": ObjectId(),
  "name": "Usman Ali",
  "vehicle": "Bike",
  "status": "Available",
  "earnings": 12000
}
```

### Fields

| Field | Description |
|---------|-------------|
| _id | Rider ID |
| name | Rider Name |
| vehicle | Vehicle Type |
| status | Availability Status |
| earnings | Total Earnings |

---

# 🔗 Database Relationships

```text
CUSTOMERS
    │
    ▼
ORDERS
    │
    ├────────► PAYMENTS
    │
    ▼
RESTAURANTS
    │
    ▼
MENU ITEMS

RIDERS
    │
    ▼
ORDERS
```

### Relationship Summary

| Relationship | Type |
|-------------|------|
| Customer → Orders | One-to-Many |
| Order → Payment | One-to-One |
| Restaurant → Orders | One-to-Many |
| Restaurant → Menu Items | One-to-Many |
| Rider → Orders | One-to-Many |

---

# 📊 Database Statistics

| Collection | Documents |
|------------|-----------|
| Customers | 10 |
| Restaurants | 10 |
| Menu Items | 15 |
| Orders | 10 |
| Payments | 10 |
| Riders | 5 |

### Additional Insights

- Total Revenue: ₨ 8,500+
- Delivered Orders: 7
- Preparing Orders: 2
- Out For Delivery Orders: 1
- Active Customers: 10
- Available Riders: 5
- Restaurants Across Multiple Cities
- Multiple Food Categories Available

---

# 📁 Project Structure

```text
FoodDelivery-Database/
│
├── README.md
│
├── data/
│   ├── customers.json
│   ├── restaurants.json
│   ├── menuitems.json
│   ├── orders.json
│   ├── payments.json
│   └── riders.json
│
├── queries/
│   ├── find_queries.txt
│   ├── update_queries.txt
│   ├── delete_queries.txt
│   └── aggregate_queries.txt
│
├── reports/
│   ├── revenue_report.txt
│   ├── customer_analysis.txt
│   ├── payment_analysis.txt
│   ├── restaurant_analysis.txt
│   └── order_status_report.txt
│
├── screenshots/
│
├── documentation/
│   └── project_documentation.pdf
│
└── LICENSE
```

---

# 🚀 Installation Guide

## Step 1: Install MongoDB

Download MongoDB Community Server:

https://www.mongodb.com/try/download/community

Install using the default settings.

---

## Step 2: Install MongoDB Compass

Download MongoDB Compass:

https://www.mongodb.com/products/compass

Install and launch MongoDB Compass.

---

## Step 3: Connect to MongoDB

Connection String:

```text
mongodb://localhost:27017
```

Click **Connect**.

---

## Step 4: Create Database

```javascript
use FoodDeliveryDB
```

---

## Step 5: Import JSON Files

Using MongoDB Compass:

1. Create Collection
2. Click Add Data
3. Select Import JSON
4. Choose File
5. Import Data

Repeat for all collections.

---

# 🔍 Sample Queries

## Find Customers from Lahore

```javascript
db.customers.find({
  city: "Lahore"
})
```

---

## Find Delivered Orders

```javascript
db.orders.find({
  status: "Delivered"
})
```

---

## Find Available Riders

```javascript
db.riders.find({
  status: "Available"
})
```

---

## Find Top Rated Restaurants

```javascript
db.restaurants.find({
  rating: {
    $gte: 4.5
  }
})
```

---

# 📈 Aggregation Queries

## Revenue by Restaurant

```javascript
db.orders.aggregate([
{
 $group:{
   _id:"$restaurant_name",
   totalRevenue:{
     $sum:"$grand_total"
   }
 }
}
])
```

---

## Customer Spending Analysis

```javascript
db.customers.aggregate([
{
 $group:{
   _id:"$city",
   totalSpent:{
     $sum:"$total_spent"
   }
 }
}
])
```

---

## Payment Method Analysis

```javascript
db.payments.aggregate([
{
 $group:{
   _id:"$method",
   count:{
     $sum:1
   }
 }
}
])
```

---

# 🎓 Learning Outcomes

This project demonstrates:

- MongoDB Fundamentals
- NoSQL Database Design
- Collections and Documents
- CRUD Operations
- Aggregation Pipelines
- Data Modeling
- Database Relationships
- Report Generation
- Database Analysis
- Real-World Database Development

---

# 💼 Portfolio Benefits

This project can be used for:

- University Database Projects
- Advanced Database Lab Submission
- MongoDB Practice
- GitHub Portfolio
- Internship Applications
- Entry-Level Developer Portfolio
- Database Administrator Learning
- NoSQL Development Practice

---

# 🛠 Technologies Used

- MongoDB
- MongoDB Compass
- JSON
- JavaScript Queries
- NoSQL Database Architecture

---

# 🤝 Contribution

Contributions are welcome.

1. Fork the repository
2. Create a new branch
3. Commit your changes
4. Push to your branch
5. Open a Pull Request

---

# 📜 License

This project is licensed under the MIT License.

---

# 👨‍💻 Author

**Muhammad Umar**

ADP Computer Science Student

Advanced Database Management System Project

---

# ⭐ Support

If you found this project useful:

⭐ Star the repository

🍴 Fork the repository

📢 Share with friends

💡 Suggest improvements

---
<p align="center"> <b>🍔 Food Delivery Database Management System 🚀</b><br> Built with MongoDB for Learning and Practice. </p>
