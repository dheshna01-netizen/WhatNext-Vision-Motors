WhatNext Vision Motors: Shaping the Future of Mobility
Overview
WhatNext Vision Motors is a Salesforce CRM implementation designed to enhance customer experience and operational efficiency in the automotive sector. The platform integrates vehicle inventory, dealer locations, customer management, and order processing. By replacing manual processes with automated workflows, real-time validations, and batch updates, the system ensures accurate stock management and streamlined fulfillment.
Key Features
Real-Time Stock Validation: Apex triggers prevent out-of-stock orders and adjust inventory levels upon confirmation.
Automated Dealer Assignment: Assigns new orders to the nearest dealer based on customer geolocation.
Automated Order Tracking: Marks orders as Pending or Confirmed based on current inventory, auto-updating pending orders when stock is refilled.
Automated Notifications: Sends email alerts for order updates and test-drive reminders.
Scheduled Batch Updates: Uses scheduled Batch Apex jobs to process pending bulk orders and reconcile daily inventory.
Data Model & Custom Objects
The core functionality rests on custom Salesforce objects that structure the business workflow:

Object API Name
Custom Object Label
Description
Vehicle__c


Vehicle
Stores vehicle details (model, price, status, stock quantity).
Vehicle_Dealer__c


Vehicle Dealer
Holds authorized dealer information, locations, and contact info.
Vehicle_Customer__c


Vehicle Customer
Maintains customer profile details and vehicle preferences.
Vehicle_Order__c


Vehicle Order
Tracks purchase orders, dates, order total, and order statuses.
Vehicle_Test_Drive__c


Vehicle Test Drive
Records test drive bookings, schedules, and statuses.
Vehicle_Service_Request__c


Vehicle Service Request
Logs vehicle servicing requests, dates, and progress.

Technical Architecture
Salesforce Core Platform: Custom Lightning App grouping relevant tabs and records.
Record-Triggered Flows: Automates dealer assignments and sends email reminders one day before scheduled test drives.
Apex Triggers & Handlers: Validates inventory before order save (addError for zero stock) and recalculates totals and stock quantities.
Batch Apex & Scheduled Jobs: Nightly batch processing (VehicleOrderBatch) updates pending orders as stock becomes available.
End-to-End Workflow Example
Customer Registration: Customer registers with email validation rules ensuring proper formatting.
Inventory Creation: Admin enters vehicle details with validation rules blocking negative stock values.
Order Placement & Stock Check:
When an order is placed, an Apex trigger calculates total cost and verifies stock.
Stock > 0 $\rightarrow$ Order status set to Confirmed, stock decreases by order quantity.
Stock = 0 $\rightarrow$ Order status set to Pending.
Stock Refill & Auto-Confirmation: When new inventory arrives, an After Update trigger automatically processes pending orders.
Scheduled Reconciliation: Daily scheduled jobs review remaining pending orders and send batch status logs to admins.
Customer Alerts: Record-Triggered Flows dispatch email notifications for status updates and drive schedules.
Future Enhancements
Salesforce Experience Cloud: Customer portal for self-service order tracking and loyalty points.
Mobile SDK: Dedicated app for store managers to adjust inventory on the go.
Einstein AI Integration: Intelligent vehicle recommendations based on purchase history.
Omnichannel Messaging: WhatsApp/SMS notifications via Twilio or Salesforce Digital Engagement.

