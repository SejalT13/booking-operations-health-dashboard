# Booking Operations Health Dashboard

## Project Overview
This project analyzes booking performance and operational health across properties. 
The objective is to identify revenue leakage, operational inefficiencies, and data quality issues using Looker Studio.

## Business Problem
Operations teams lacked visibility into:
- Bookings with missing checkout data
- Revenue at risk due to incomplete records
- Property-level operational issues
- Resolution time for booking issues

This dashboard centralizes KPIs to enable faster decision-making.

## Data Sources
- bookings.csv (Booking details and revenue data)
- ops_issues.csv (Operational issue records and resolution time)
- properties.csv (Property metadata)

## Data Model
- bookings joined with properties on property_id (1:M)
- bookings joined with ops_issues on booking_id (1:M)

## Key KPIs
- Total Bookings
- Checkout Missing Rate
- Revenue at Risk (estimated one-night revenue for bookings with missing checkout data)
- Average Stay (Nights)
- Average Resolution Time
- Revenue by Property
- Data Issues Trend

## Calculated Fields
Revenue at Risk:
CASE WHEN checkout_date IS NULL 
THEN total_amount / DATEDIFF(checkout_date, checkin_date)
ELSE 0 END

Checkout Missing Rate:
COUNT(CASE WHEN checkout_date IS NULL THEN booking_id END) / COUNT(booking_id)

## Key Insights
- Harbor Apartment shows highest operational risk.
- 11% of bookings have missing checkout data.
- Revenue at risk spikes mid-month.
- Resolution time varies significantly across properties.

## Live Dashboard
https://lookerstudio.google.com/...
## Dashboard Preview

![Dashboard Preview](images/Dashboard_Preview.png)
