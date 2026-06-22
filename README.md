# 🍔 Food Delivery Database - MongoDB Project

[![MongoDB](https://img.shields.io/badge/MongoDB-4.4+-green.svg)](https://www.mongodb.com/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

A complete, production-ready sample database for a food delivery system built with MongoDB. Perfect for learning, portfolio, or as a starting point for your food delivery app.

---

## 📋 **Project Overview**

This database simulates a real-world food delivery platform with:

- **6 Collections** covering all business entities
- **50+ Documents** with realistic Pakistani food delivery data
- **Complete Relationships** between customers, orders, restaurants, and payments
- **Ready-to-Use Queries** for data analysis
- **Generated Reports** from real data insights

### **Key Features**
✅ Realistic sample data with Pakistani cities and cuisine  
✅ Proper MongoDB schema design  
✅ Relationship mapping between collections  
✅ Pre-written queries for common operations  
✅ Data analysis reports  
✅ Easy to import and use  

---

## 🗂️ **Collections & Data Summary**

| # | Collection | Documents | Description | Key Fields |
|---|------------|-----------|-------------|------------|
| 1 | **customers** | 10 | User profiles with order history | name, email, city, total_spent |
| 2 | **restaurants** | 10 | Restaurant details and ratings | name, cuisine, rating, delivery_fee |
| 3 | **menuitems** | 15 | Food items with pricing | name, price, category, restaurant |
| 4 | **orders** | 10 | Complete order transactions | items, status, grand_total |
| 5 | **payments** | 10 | Payment records | method, amount, status |
| 6 | **riders** | 5 | Delivery personnel info | vehicle, status, earnings |

### **Data Statistics**
- **Total Customers**: 10 (100% Active)
- **Total Orders**: 10 
  - Delivered: 7
  - Preparing: 2
  - Out for Delivery: 1
- **Total Revenue**: ₨8,500 (from completed orders)
- **Total Restaurants**: 10 across 5 cities
- **Total Riders**: 5 with ₨53,400 total earnings
- **Total Menu Items**: 15 across 8 categories

---

## 🔗 **Schema Relationships**
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│ CUSTOMERS │────▶│ ORDERS │────▶│ PAYMENTS │
│ (1) │ │ (M) │ │ (1) │
└─────────────┘ └─────────────┘ └─────────────┘
│
▼
┌─────────────┐
│ RESTAURANTS │
│ (1) │
└─────────────┘
│
▼
┌─────────────┐
│ MENU ITEMS │
│ (M) │
└─────────────┘

┌─────────────┐
│ RIDERS │
│ (M) │
└─────────────┘

text

### **Relationship Details**
- **Customers → Orders**: One-to-Many (One customer can have many orders)
- **Orders → Payments**: One-to-One (Each order has one payment)
- **Orders → Restaurants**: Many-to-One (Many orders go to one restaurant)
- **Restaurants → Menu Items**: One-to-Many (One restaurant has many menu items)
- **Riders → Orders**: Many-to-Many (Riders deliver many orders)

---

## 🚀 **How to Import Data**

### **Method 1: MongoDB Compass (GUI - Recommended for Beginners)**

1. **Download MongoDB Compass** from [mongodb.com/products/compass](https://www.mongodb.com/products/compass)
2. **Connect** to your MongoDB instance
3. **Create a new database** called `FoodDeliveryDB`
4. **Click "Add Data"** → **"Import File"**
5. **Select JSON files** from the `data/` folder
6. **Import each collection** one by one:

| Collection | File to Import |
|------------|----------------|
| customers | customers.json |
| restaurants | restaurants.json |
| menuitems | menuitems.json |
| orders | orders.json |
| payments | payments.json |
| riders | riders.json |

### **Method 2: Command Line (Terminal)**

```bash
# Import all collections at once
mongoimport --db FoodDeliveryDB --collection customers --file data/customers.json --jsonArray
mongoimport --db FoodDeliveryDB --collection restaurants --file data/restaurants.json --jsonArray
mongoimport --db FoodDeliveryDB --collection menuitems --file data/menuitems.json --jsonArray
mongoimport --db FoodDeliveryDB --collection orders --file data/orders.json --jsonArray
mongoimport --db FoodDeliveryDB --collection payments --file data/payments.json --jsonArray
mongoimport --db FoodDeliveryDB --collection riders --file data/riders.json --jsonArray

# Verify import
mongosh
use FoodDeliveryDB
show collections
db.customers.count()  # Should show 10
Method 3: MongoDB Shell
javascript
// In MongoDB Shell
use FoodDeliveryDB

// Import using load() function
load("data/customers.json")
load("data/restaurants.json")
// ... etc
📊 Sample Queries
Basic Queries
1. Find all customers from Lahore
javascript
db.customers.find({ city: "Lahore" }).pretty()
// Returns: 3 customers (Ali, Fatima, Zara)
2. Find all delivered orders
javascript
db.orders.find({ status: "Delivered" }).pretty()
// Returns: 7 orders
3. Find active restaurants with rating > 4.5
javascript
db.restaurants.find({ 
  rating: { $gte: 4.5 }, 
  is_open: true 
}).pretty()
// Returns: Tasty Bites, Spice Garden, Biryani House, Desi Dhaba, Steak House
4. Find available riders
javascript
db.riders.find({ status: "Available" }).pretty()
// Returns: Usman Ali, Bilal Malik, Sana Tariq
Advanced Aggregation Queries
5. Total Revenue by Restaurant
javascript
db.orders.aggregate([
  { 
    $group: { 
      _id: "$restaurant_name", 
      totalRevenue: { $sum: "$grand_total" },
      orderCount: { $sum: 1 }
    } 
  },
  { $sort: { totalRevenue: -1 } }
])
6. Most Popular Food Items
javascript
db.orders.aggregate([
  { $unwind: "$items" },
  { 
    $group: { 
      _id: "$items", 
      count: { $sum: 1 } 
    } 
  },
  { $sort: { count: -1 } },
  { $limit: 5 }
])
7. Customer Spending Analysis
javascript
db.customers.aggregate([
  { 
    $group: {
      _id: "$city",
      totalSpent: { $sum: "$total_spent" },
      avgSpent: { $avg: "$total_spent" },
      customerCount: { $sum: 1 }
    }
  },
  { $sort: { totalSpent: -1 } }
])
8. Payment Method Distribution
javascript
db.payments.aggregate([
  { 
    $group: {
      _id: "$method",
      count: { $sum: 1 },
      totalAmount: { $sum: "$amount" }
    }
  },
  { $sort: { count: -1 } }
])
9. Order Status Summary
javascript
db.orders.aggregate([
  { 
    $group: {
      _id: "$status",
      count: { $sum: 1 },
      totalValue: { $sum: "$grand_total" }
    }
  }
])
10. Restaurant Performance Metrics
javascript
db.orders.aggregate([
  {
    $group: {
      _id: "$restaurant_name",
      totalOrders: { $sum: 1 },
      totalRevenue: { $sum: "$grand_total" },
      avgOrderValue: { $avg: "$grand_total" }
    }
  },
  { $sort: { totalRevenue: -1 } }
])
📈 Pre-Generated Reports
Check the reports/ folder for detailed analysis:

Report	Description
total_revenue.txt	Total revenue from all orders
orders_by_restaurant.txt	Orders count and revenue per restaurant
popular_items.txt	Most ordered food items
customer_spending.txt	Top spending customers
payment_methods.txt	Payment method distribution
orders_by_status.txt	Order status breakdown
city_analysis.txt	City-wise customer and order analysis
🖼️ Screenshots
Check the screenshots/ folder for visual documentation:

Database view in MongoDB Compass

Each collection data view

Query results

Report visualizations

🛠️ MongoDB Setup Guide
Install MongoDB on Windows
Download MongoDB Installer from mongodb.com/try/download/community

Run Installer and choose "Complete" setup

Choose "Run Service as Network Service"

Install MongoDB Compass (check the box)

Click Install and wait for completion

Install MongoDB on macOS
bash
# Using Homebrew
brew tap mongodb/brew
brew install mongodb-community

# Start MongoDB service
brew services start mongodb-community
Install MongoDB on Linux (Ubuntu)
bash
# Import MongoDB public GPG key
wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -

# Add MongoDB repository
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list

# Update and install
sudo apt-get update
sudo apt-get install -y mongodb-org

# Start MongoDB
sudo systemctl start mongod
📚 MongoDB Compass Guide
Connecting to MongoDB
Open MongoDB Compass

Connection String: mongodb://localhost:27017

Click "Connect"

Creating Database
Click "Create Database"

Database Name: FoodDeliveryDB

Collection Name: customers (you'll create others)

Click **"Create Database"`

Importing Data
Select your database (FoodDeliveryDB)

Click the collection name

Click "Add Data" → "Import File"

Select JSON file from data/ folder

Click "Import"

📝 Query Files Included
Check the queries/ folder for:

find_queries.txt - All read operations

update_queries.txt - All update operations

delete_queries.txt - All delete operations

aggregate_queries.txt - Advanced aggregation pipelines

📁 Project Structure
text
FoodDelivery-Database/
│
├── README.md                          ← You are here
├── data/                              ← JSON data files
│   ├── customers.json
│   ├── restaurants.json
│   ├── menuitems.json
│   ├── orders.json
│   ├── payments.json
│   └── riders.json
│
├── queries/                           ← All query examples
│   ├── find_queries.txt
│   ├── update_queries.txt
│   ├── delete_queries.txt
│   └── aggregate_queries.txt
│
├── reports/                           ← Generated reports
│   ├── total_revenue.txt
│   ├── orders_by_restaurant.txt
│   ├── popular_items.txt
│   ├── customer_spending.txt
│   ├── payment_methods.txt
│   ├── orders_by_status.txt
│   └── city_analysis.txt
│
├── screenshots/                       ← Visual documentation
│   └── [Your screenshots here]
│
├── setup/                             ← Setup guides
│   ├── mongodb_install_guide.txt
│   └── compass_guide.txt
│
├── documentation/                     ← Project docs
│   └── project_overview.txt
│
└── .gitignore
🎯 Why This Project is Portfolio-Ready
Demonstrates:
✅ Database Design - Proper schema and relationships
✅ MongoDB Skills - Collections, documents, queries
✅ Data Analysis - Aggregation pipelines, reports
✅ Documentation - Professional README and guides
✅ Organization - Clean folder structure
✅ Real-World Data - Realistic food delivery scenario

Best For:
Junior Developer Portfolio

MongoDB Learning Resource

Database Design Example

Interview Preparation

Open Source Contribution

🤝 How to Contribute
Fork the repository

Create your feature branch (git checkout -b feature/AmazingFeature)

Commit your changes (git commit -m 'Add some AmazingFeature')

Push to the branch (git push origin feature/AmazingFeature)

Open a Pull Request

📝 License
This project is licensed under the MIT License - see the LICENSE file for details.

📞 Support
GitHub Issues: Create an issue

Documentation: See documentation/ folder

Setup Help: See setup/ folder

⭐ Show Your Support
If you find this project helpful:

Star the repository ⭐

Fork it for your own use

Share with others

Contribute improvements

Made with ❤️ for learning and portfolio

🔗 Quick Links
MongoDB Documentation

MongoDB Compass

MongoDB University

GitHub Guide

Happy Coding! 🚀
