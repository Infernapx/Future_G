# Smart Grocery POS & Store Management

A comprehensive, production-ready Flutter application for retail stores, offering seamless point-of-sale (POS) operations, inventory management, and automated billing through a secure, multi-role architecture.

📥 **[Download Android APK](apk/smart-grocery.apk)** (Click to download and install on your device)

## 🏗️ Architecture overview

The application is built entirely using **Flutter** and leverages cloud-based databases for real-time synchronization.

### Core Technologies
- **Frontend Framework:** Flutter (Dart)
- **Database Architecture:** Relational cloud database (PostgreSQL)
- **Authentication:** Secure Email/Password & Role metadata
- **State Management:** Provider

### Role-Based Access Control (RBAC)
The architecture routes users based on securely managed metadata roles:
1. **Customer:** Can browse products, view cart, and view purchase history.
2. **Staff / Gatekeeper:** Can scan physical items via barcodes and process checkouts.
3. **Store Owner:** Has full access to the Owner Dashboard to manage inventory, update product listings, configure discount offers, and view detailed sales reports.

## ✨ Key Features

- **Real-Time Inventory Tracking:** Stock levels are automatically decremented via secure database transactions when a bill is processed.
- **Dynamic Offer Engine:** Automatically applies Flat, Percentage, or Buy-One-Get-One (BOGO) discounts to qualifying items at checkout.
- **Barcode Scanning:** Staff can rapidly scan product barcodes to add items to the billing cart.
- **Interactive Dashboards:** Analytics and management screens tailored to the Owner role for complete store control.

## 📁 Repository Structure
- **`lib/`**: Contains the complete Flutter application source code organized by feature modules (Auth, Customer, Staff, Owner).
- **`database/`**: Contains the SQL schema definitions and Python seeding scripts used to design the database architecture.

## 🔐 Security Considerations

- All sensitive inventory updates (like reducing stock and applying discounts) are handled atomically.
- Role verification happens on authentication state changes, ensuring unprivileged accounts cannot access administrative views.
