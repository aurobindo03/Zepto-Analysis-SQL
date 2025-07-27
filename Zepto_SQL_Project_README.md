
# Zepto SQL Data Analyst Portfolio Project


## 📁 Table of Contents
- [Project Overview](#project-overview)
- [Schema Design](#schema-design)
- [Data Exploration](#data-exploration)
- [Data Cleaning](#data-cleaning)
- [Data Analysis](#data-analysis)
- [Key Learnings](#key-learnings)


---

## 📌 Project Overview

The goal of this project is to practice SQL skills using PostgreSQL to perform data wrangling and analysis tasks. We simulate common business use-cases such as revenue analysis, discount analysis, product categorization, and inventory insights.
The dataset was sourced from Kaggle and was originally scraped from Zepto’s official product listings. It mimics what you’d typically encounter in a real-world e-commerce inventory system.

Each row represents a unique SKU (Stock Keeping Unit) for a product. Duplicate product names exist because the same product may appear multiple times in different package sizes, weights, discounts, or categories to improve visibility – exactly how real catalog data looks.

🧾 Columns:

sku_id: Unique identifier for each product entry (Synthetic Primary Key)

name: Product name as it appears on the app

category: Product category like Fruits, Snacks, Beverages, etc.

mrp: Maximum Retail Price (originally in paise, converted to ₹)

discountPercent: Discount applied on MRP

discountedSellingPrice: Final price after discount (also converted to ₹)

availableQuantity: Units available in inventory

weightInGms: Product weight in grams

outOfStock: Boolean flag indicating stock availability

quantity: Number of units per package (mixed with grams for loose produce)
## 🗃️ Schema Design

```sql
CREATE TABLE zepto (
    sku_id SERIAL PRIMARY KEY,
    category VARCHAR(120),
    name VARCHAR(150) NOT NULL,
    mrp NUMERIC(8,2),
    discountPercent NUMERIC(5,2),
    availableQuantity INTEGER,
    discountedSellingPrice NUMERIC(8,2),
    weightInGms INTEGER,
    outOfStock BOOLEAN,
    quantity INTEGER
);
```

## 🔍 Data Exploration

- View sample data and total row count.
- Identify `NULL` values.
- Explore unique categories.
- Count products in stock vs out of stock.
- Detect duplicate product names.

## 🧹 Data Cleaning

- Remove records where MRP or selling price = 0.
- Convert paise to rupees by dividing MRP and Selling Price by 100.

## 📊 Data Analysis

1. **Top 10 Best-Value Products by Discount Percentage**
2. **High MRP Products that are Out of Stock**
3. **Estimated Revenue per Category**
4. **Products with MRP > ₹500 and Discount < 10%**
5. **Top 5 Categories by Average Discount**
6. **Price per Gram for Products ≥ 100g**
7. **Categorize Products as Low, Medium, Bulk Based on Weight**
8. **Total Inventory Weight per Category**

## 💡 Key Learnings

- SQL Data Cleaning and Formatting
- Aggregation and Grouping Techniques
- CASE Statements for Categorization
- Revenue and Inventory Analysis
- Filtering and Sorting Logic
- Real-world E-Commerce SQL Use Cases

