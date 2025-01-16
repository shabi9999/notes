# Marketplace Technical Foundation - My E-Commerce Marketplace
# System Architecture 
# Overview
The system architecture consists of the following components:

1.Frontend: Built with React or Next.js to provide a responsive, user-friendly interface.

2. Backend: Sanity CMS to manage data (products, customers, orders).

3.Third-Party APIs: For payment processing and shipment tracking. 





# Key Workflows

# User Registration

Step 1: User enters name, email, and password on the frontend.

Step 2: Data is sent to Sanity CMS and stored as a customer record

Step 3: A welcome email is sent to the user (optional).

# 2. Product Browsing

Step 1: User selects a category (e.g., Casual, Formal).

Step 2: Frontend fetches filtered products from Sanity CMS.

Step 3: Products are displayed with sorting and filtering options.

# 3. Order Placement

Step 1: User adds products to the cart.

Step 2: On checkout, order details are sent to Sanity CMS and stored.

Step 3: Payment details are processed via the Payment Gateway.

Step 4: Order status is updated, and the user receives a confirmation.

# 4. Shipment Tracking

Step 1: User requests shipment tracking.

Step 2: Frontend fetches the latest status from the Shipment Tracking API.

Step 3: Real-time updates are displayed to the user.

# API Endpoints

# Products

## Endpoint: /products

 Method: GET

Description: Fetch all available products.

Response:



```json
[
  {
    "_id": "prood_001",
"name": "Wooden Coffee Table",
"description" : "A stylish wooden coffee table",
"price" : 150,
"image" : [
{"_types": "image", "asset": {"_ref": "image_ref_001",
"_type": "reference" } } ],
"material" : "wood",
"stock" : 25,
"category" : "Living Room",
"tags" : [ "sale", "new arrival"],
"reviews" : 4.5,
  }
]

# Orders

(-) Endpoint: /orders

-Method: POST

