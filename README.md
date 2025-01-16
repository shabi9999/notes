# Marketplace Technical Foundation - My E-Commerce Marketplace
# System Architecture 
# Overview
The system architecture consists of the following components:

**1.Frontend.**: Built with React or Next.js to provide a responsive, user-friendly interface.

**2. Backend.**: Sanity CMS to manage data (products, customers, orders).

**3.Third-Party APIs.**: For payment processing and shipment tracking. 





# Key Workflows

# User Registration

**Step 1.**: User enters name, email, and password on the frontend.

**Step 2.**: Data is sent to Sanity CMS and stored as a customer record

**Step 3.**: A welcome email is sent to the user (optional).

# 2. Product Browsing

**Step 1.**: User selects a category (e.g., Casual, Formal).

**Step 2.**: Frontend fetches filtered products from Sanity CMS.

**Step 3.**: Products are displayed with sorting and filtering options.

# 3. Order Placement

**Step 1.**: User adds products to the cart.

**Step 2.**: On checkout, order details are sent to Sanity CMS and stored.

**Step 3.**: Payment details are processed via the Payment Gateway.

**Step 4.**: Order status is updated, and the user receives a confirmation.

# 4. Shipment Tracking


**Step 1.**: User requests shipment tracking.


**Step 2.**:Frontend fetches the latest status from the Shipment Tracking API.


**Step 3.**: Real-time updates are displayed to the user.

# API Endpoints

# Products
 
- **Endpoint.**: /products

- **Method.**: GET

- **Description**: Fetch all available products.

- **Response.**:



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
```


# Orders

- **Endpoint.**: /orders

- **Method.**: POST

- **Description.**: Create a new ord

- **Payload.**:

 ```json
[
  {
   "productID" : "prod_001",
"Quantity" : 2,
"totalAmount" : 300,
"OrderDate" : " 2025-01-16"
  }
]
```

# Payment

- **Endpoint.**: /payment

- **Method.**: Post
 
- **Description.**: Process payment for an order

- **Payload.**:

```json
[
  {
 "order": {
" id": "oder_001",
"totalAmount": 150,
},
"paymentMethod": "Credit Card",
"status": "completed",
"transactionId": "txn_001",
"Amount": 300,
"PaymentDate": "2025-01-16"
  }
]
```

# Shipment


- **Endpoint.**: /shipment/:

- **Method.**: GET

- **Description.**: Track the status of a shipment.

- **Response.**:

```json
[
  {
"_id": "ship_001",
"order": {
" id": "order_001",
"totalAmount": 150,
},
"trackingNumber": "track_001",
"status": "In Transit",
"estimateDelivery": "2025-01-16"
  }
]
```

# Shipment


- **Endpoint.**: /shipment/:

- **Method.**: GET

- **Description.**: Fetch all delivery zones and their details.

- **Response.**:

```

  {

"id": "zone_001",

"zoneName": "zone_001",

"coverageArea": ["City A", "City B",

"shippingCost": "001",

"carrier": "Carrier",

"assignedDriver": "Driver 1"

  }
```

# Sanity CMS Schemas:

 # [Product]

 - _id

 - Name

 - Description

 - Image

 - Price

- Stock

- Discount price

 - Categories

 - Tags

- Reviews

 - Colors

  # [Customer]


- id

- Name

- Email

- Phone

- Address

# [Payment]

- id

- Order

- Payment method

- Status

- Transaction ID

- Amount

- Payment Date

# [Shipment]

- id

- Order

- Tracking number

- Status

- Estimate delivery

# [Delivery Zone]

-id

- Zone name

- Coverage area

- Shipping cost

- Carrier

 ### Product Schema

```json
 import { defineField, defineType } from "sanity";

export const ProductType = defineType({
  title: "Product",
  type: "document",
  name: "product",
  fields: [
    defineField({
      title: "Product Name",
      type: "string",
      name: "productName",
    }),
    defineField({
      title: "Product Description",
      type: "text",
      name: "productDescription",
    }),
    defineField({
      title: "Price",
      type: "number",
      name: "price",
    }),
    defineField({
      title: "Sale Price",
      type: "number",
      name: "salePrice",
    }),
    defineField({
      title: "Material",
      type: "string",
      name: "material",
      options: {
        list: [
          { title: "Wood", value: "wood" },
          { title: "Metal", value: "metal" },
          { title: "Plastic", value: "plastic" },
          { title: "Fabric", value: "fabric" },
        ],
      },
    }),
    defineField({
      title: "Color",
      type: "array",
      of: [{ type: "string" }],
      options: {
        list: [
          { title: "Black", value: "black" },
          { title: "White", value: "white" },
          { title: "Brown", value: "brown" },
          { title: "Grey", value: "grey" },
          // Add more colors as needed
        ],
      },
    }),
    defineField({
      title: "Dimensions",
      type: "string",
      name: "dimensions",
    }),
    defineField({
      title: "Weight",
      type: "number",
      name: "weight",
    }),
    defineField({
      title: "Style",
      type: "string",
      name: "style",
      options: {
        list: [
          { title: "Modern", value: "modern" },
          { title: "Classic", value: "classic" },
          { title: "Industrial", value: "industrial" },
          { title: "Mid-Century Modern", value: "midCenturyModern" },
        ],
      },
    }),
    defineField({
      title: "Main Image",
      name: "mainImage",
      type: "image",
      options: {
        hotspot: true,
      },
    }),
    defineField({
      title: "Gallery Images",
      name: "galleryImages",
      type: "array",
      of: [{ type: "image" }],
      options: {
        hotspot: true,
      },
    }),
  ],
});
```
 










  

  

