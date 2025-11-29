# ER-Design
ER Design Introduction to DataBase
Food Delivery Management System - ER Design
High-level Overview of Functions and Use Cases
Main System Functions:

Restaurant and menu management

Customer order processing

Courier and delivery management

Payment and transaction accounting

Review and rating system

Order status tracking

Use Cases:

Customer:

Registration and profile management

Browsing restaurants and menus

Creating and tracking orders

Payment processing

Leaving reviews

Restaurant:

Managing restaurant information

Menu and price management

Processing incoming orders

Updating preparation status

Courier:

Registration and verification

Accepting delivery orders

Updating delivery status

Schedule management

Administrator:

Managing all system entities

Transaction monitoring

Analytics and reporting

Entities, Attributes and Relations Description
1. Customer
Attributes:

customer_id (PK, UUID) - unique identifier

first_name (VARCHAR(50)) - first name

last_name (VARCHAR(50)) - last name

email (VARCHAR(100)) - email address

phone (VARCHAR(20)) - phone number

address (TEXT) - delivery address

created_at (TIMESTAMP) - registration date

2. Restaurant
Attributes:

restaurant_id (PK, UUID) - unique identifier

name (VARCHAR(100)) - restaurant name

cuisine_type (VARCHAR(50)) - type of cuisine

address (TEXT) - restaurant address

phone (VARCHAR(20)) - phone number

email (VARCHAR(100)) - email address

is_active (BOOLEAN) - activity status

rating (DECIMAL(3,2)) - average rating

3. MenuItem
Attributes:

item_id (PK, UUID) - unique identifier

restaurant_id (FK, UUID) - reference to restaurant

name (VARCHAR(100)) - dish name

description (TEXT) - description

price (DECIMAL(10,2)) - price

category (VARCHAR(50)) - category (beverage, main course, etc.)

is_available (BOOLEAN) - availability status

4. Order
Attributes:

order_id (PK, UUID) - unique identifier

customer_id (FK, UUID) - customer

restaurant_id (FK, UUID) - restaurant

courier_id (FK, UUID) - courier

order_date (TIMESTAMP) - order date

total_amount (DECIMAL(10,2)) - total amount

status (VARCHAR(20)) - status (new, preparing, in delivery, delivered)

delivery_address (TEXT) - delivery address

special_instructions (TEXT) - special instructions

5. OrderItem
Attributes:

order_item_id (PK, UUID) - unique identifier

order_id (FK, UUID) - order

item_id (FK, UUID) - menu item

quantity (INTEGER) - quantity

unit_price (DECIMAL(10,2)) - price per unit

6. Courier
Attributes:

courier_id (PK, UUID) - unique identifier

first_name (VARCHAR(50)) - first name

last_name (VARCHAR(50)) - last name

phone (VARCHAR(20)) - phone number

vehicle_type (VARCHAR(20)) - vehicle type

is_available (BOOLEAN) - availability status

rating (DECIMAL(3,2)) - rating

7. Payment
Attributes:

payment_id (PK, UUID) - unique identifier

order_id (FK, UUID) - order

amount (DECIMAL(10,2)) - amount

payment_method (VARCHAR(20)) - payment method

payment_status (VARCHAR(20)) - payment status

payment_date (TIMESTAMP) - payment date

transaction_id (VARCHAR(100)) - transaction identifier

8. Review
Attributes:

review_id (PK, UUID) - unique identifier

order_id (FK, UUID) - order

customer_id (FK, UUID) - customer

rating (INTEGER) - rating (1-5)


Relationships Description
Customer places Order (1:N)

One customer can place many orders

One order belongs to one customer

Restaurant offers MenuItem (1:N)

One restaurant can have many menu items

One menu item belongs to one restaurant

Order contains OrderItem (1:N)

One order can contain many order items

One order item belongs to one order

MenuItem included in OrderItem (1:N)

One menu item can be in many order items

One order item references one menu item

Courier delivers Order (1:N)

One courier can deliver many orders

One order is delivered by one courier

Order has Payment (1:1)

One order has one payment

One payment references one order

Order receives Review (1:1)

One order can have one review

One review references one order

Customer writes Review (1:N)

One customer can write many reviews

One review belongs to one customer
comment (TEXT) - comment

review_date (TIMESTAMP) - review date
