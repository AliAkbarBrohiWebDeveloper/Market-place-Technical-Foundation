# Market-place-Technical-Foundation


# E-Commerce Marketplace API Documentation This API is designed for managing products like shoes and shirts, handling orders, and tracking shipments. The system allows customers to browse available products, create orders, and track their shipments.
Endpoints

Fetch All Products Endpoint Name: /products Method: GET Description: Retrieve all available products from the marketplace, including details such as product name, price, stock availability, and product image. Response Example: json Copy { "id": 1, "name": "Running Shoes", "price": 120, "stock": 25, "image": "https://example.com/running-shoes.jpg" } 2. Create a New Order Endpoint Name: /orders Method: POST Description: Create a new order by submitting customer details, product(s), and payment status. Request Body Example:

json Copy { "customer_id": "123", "products": [ { "product_id": "1", "quantity": 2 } ], "payment_status": "pending" } Response Example:

json Copy { "order_id": "56789", "status": "Order Created", "message": "Your order has been successfully created." } 3. Track Order Status Endpoint Name: /order-tracking/{order_id} Method: GET Description: Fetch the real-time tracking details for a specific order, including shipment status, current location, expected delivery date, and tracking number. Path Parameter:

order_id: The unique identifier of the order to track. Response Example:

json Copy { "order_id": "12345", "shipment_status": "In Transit", "current_location": "New York, NY", "expected_delivery_date": "2025-01-20", "tracking_number": "ABCD1234EFGH", "carrier": "FedEx", "delivery_status": "On Track" } Response Fields:

order_id: Unique identifier of the order. shipment_status: Current shipment status (e.g., "Shipped", "In Transit"). current_location: Current location of the shipment. expected_delivery_date: Estimated delivery date. tracking_number: Shipment's unique tracking number. carrier: The carrier handling the shipment (e.g., FedEx). delivery_status: Delivery status (e.g., "On Track", "Delayed"). 4. Manage Product Inventory Endpoint Name: /products Method: POST Description: Add a new product (shoes or shirts) to the marketplace. Only available for Admin or Seller roles. Request Body Example:

json Copy { "name": "Nike Air Max", "price": 150, "description": "Comfortable running shoes with Air cushioning.", "stock": 50, "image": "https://example.com/nike-air-max.jpg" } Authentication To ensure secure interactions, certain API requests require authentication.

Authentication Method:JWT Token Obtaining the Token: After successful login or registration, a JWT token will be returned. Usage: Include the token in the Authorization header for any requests that require authentication. Integration Notes Content Management: The API integrates with Sanity CMS for managing product information (e.g., shoes, shirts). Payment Processing: Payments are securely processed via Stripe. Shipment Tracking: Shipment details are fetched using ShipEngine or other third-party services.
