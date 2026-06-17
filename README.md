# 🛒 Smart Grocery

A modern, cloud-synchronized Point-of-Sale (POS) and Inventory Management System for retail grocery stores.

Smart Grocery digitizes and automates the entire retail lifecycle — from barcode scanning and bill generation at checkout to real-time inventory tracking and actionable sales analytics — replacing legacy POS systems with a sleek, mobile-first experience.

## 📑 Table of Contents
- [Project Goal](#-project-goal)
- [Features](#-features)
- [User Roles & Access Control](#-user-roles--access-control)
- [Tech Stack](#-tech-stack)
- [Database Schema](#%EF%B8%8F-database-schema)
- [Try It Out](#-try-it-out)
- [Roadmap](#-roadmap)

---

## 🎯 Project Goal

Smart Grocery is built to be a highly efficient POS and inventory management solution tailored for retail grocery stores. It aims to:
- Drastically reduce checkout times through fast barcode-based billing.
- Prevent inventory stockouts with real-time, automatic stock deduction.
- Empower store owners with data-driven insights via an analytics dashboard.
- Provide a secure, role-based experience for customers, staff, and administrators alike.

---

## ✨ Features

### 1. High-Speed Point of Sale (POS)
- **Barcode Scanning** — Uses the device camera to instantly recognize products via barcode.
- **Smart Cart** — Automatically calculates sub-totals, applies taxes, and handles bulk quantities seamlessly.
- **Instant Billing** — Generates unique bill numbers and atomically records transactions to the cloud database.

### 2. Automated Inventory Management
- **Real-Time Deductions** — Inventory is automatically updated the moment a bill is processed, using secure backend transactions.
- **Stock Threshold Alerts** — Tracks `current_stock` against a `min_stock_threshold` to notify owners when items (e.g., fresh produce, dairy) need restocking.

### 3. Dynamic Offer & Discount Engine
- **Flat Discounts** — e.g., $5 off a qualifying order.
- **Percentage Discounts** — e.g., 10% off a category like Snacks.
- **Buy-One-Get-One (BOGO)** — Quantity-based promotional pricing.
- **Auto-Application** — The billing engine automatically cross-references cart items against active offers and applies the best available discount.

### 4. Owner Analytics Dashboard
- Bird's-eye view of overall store health.
- Visualizes total revenue, items sold, and top-performing product categories.

---

## 👥 User Roles & Access Control

Smart Grocery implements strict Role-Based Access Control (RBAC), routing users to distinct interfaces based on securely managed roles.

| Role | Access | Capabilities |
|------|--------|--------------|
| **Customer** | Storefront & personal profile | Browse products, view personal purchase history, see current offers |
| **Staff / Cashier** | Checkout & scanning interfaces | Scan barcodes, adjust quantities, apply discounts, generate bills (no analytics or inventory edit access) |
| **Store Owner (Admin)** | Full administrative access | View sales analytics, manage product catalog, update stock, configure offers, review all transactions |

*Security is enforced at the database level via Row Level Security (RLS) policies, ensuring staff cannot tamper with owner-level data.*

---

## 💻 Tech Stack

### Frontend
| Component | Technology |
|-----------|------------|
| **Framework** | Flutter (Android & iOS) |
| **Language** | Dart |
| **State Management** | Provider |
| **UI/UX** | Custom responsive UI — glassmorphism, dark mode, micro-animations |

### Backend
| Component | Technology |
|-----------|------------|
| **Backend-as-a-Service** | Supabase |
| **Database** | PostgreSQL |
| **Authentication** | Supabase Auth (Email/Password; OTP/Phone-ready) |
| **Security** | Row Level Security (RLS) policies |

> **Note:** The architecture is designed to support a future migration of intensive transaction logic to a custom Node.js / Prisma backend if required.

---

## 🗄️ Database Schema

The relational structure ensures data integrity and zero redundancy:

| Table | Description |
|-------|-------------|
| **categories** | Broad product groupings (e.g., Dairy, Produce, Snacks) |
| **products** | Individual items with MRP, selling price, and barcodes |
| **inventory** | 1-to-1 mapping with products tracking live stock counts and restock dates |
| **offers** | Promotional rules linked to specific products or entire categories |
| **bills / bill_items** | Parent-child relationship tracking final transaction amounts and line items |

---

## 🚀 Try It Out

Want to check out the app? Just grab the latest build and install it on your device:

📥 **[Download Android APK](apk/smart-grocery.apk)** (Click to download and install on your device)

---

## 🚀 Roadmap
- [ ] **Payment Gateway Integration** — Stripe / Razorpay support for direct digital payments.
- [ ] **Thermal Printer Support** — Bluetooth receipt printing for staff devices.
- [ ] **Advanced Analytics** — AI-driven sales forecasting to predict stock depletion based on historical patterns.
