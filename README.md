# ASG Airlines – End-to-End Data Engineering

## 1. Project Overview

This project implements an end-to-end data engineering pipeline for ASG Airlines. It transforms raw flight, booking, passenger, and payment data into clean, validated, privacy-aware datasets for operational analysis and Power BI reporting.

**Pipeline:**  
`Ingestion → Quality Assessment → Cleaning → Transformation → PII Protection → Validation → KPI Preparation → Power BI`

## 2. Problem Statement

The raw airline datasets contain data-quality challenges including missing values, duplicates, inconsistent values, timestamp issues, invalid records, and sensitive passenger information.

The objective is to build a reliable data pipeline that addresses these issues and produces trustworthy data for business analysis.

## 3. Objectives

- Ingest and assess the provided airline datasets.
- Identify and resolve data-quality issues.
- Standardize and transform the datasets.
- Handle flight-duration and temporal inconsistencies.
- Protect sensitive passenger information.
- Validate data quality and referential integrity.
- Prepare analytical KPIs.
- Develop an interactive Power BI dashboard.
- Document the architecture, data flow, data model, and assumptions.

## 4. Dataset

| Dataset | Purpose |
|---|---|
| Flights | Flight, airline, route and timing information |
| Bookings | Booking and passenger-flight relationships |
| Passengers | Passenger information |
| Payments | Booking payment information |

## 5. Solution Architecture
Raw CSV Files
      ↓
Python / Pandas
      ↓
Data Quality & Cleaning
      ↓
Transformation & PII Protection
      ↓
Validation
      ↓
Cleaned Analytical Data
      ↓
Power BI Dashboard

6. Data Quality & Transformation

Key processing steps include:

Duplicate detection and removal
Missing-value handling
Flight ID validation
Data standardization
Timestamp conversion and validation
Flight-duration calculation
Overnight-flight handling
Invalid temporal-record handling
Referential-integrity validation
Payment amount validation

Detailed processing logic and validation results are available in the project notebook.

7. PII Protection

Sensitive information is protected before analytical use:

Aadhaar → SHA-256 hashing
Passport number → SHA-256 hashing
Email → Masking
Phone → Masking
Date of birth → Birth year
Emergency contact details → Removed

Raw PII-containing datasets are not included in the repository.

8. Key KPIs
Total Flights: 1,004
Average Flight Duration: 2.74 hours
Total Bookings: 999
Cancelled Bookings: 314
Cancellation Rate: 31.43%
Total Payment Amount: ~₹7.37M
Route-wise Traffic
Flights by Airline
Statistical Duration Anomalies

Traditional flight-delay calculation was not performed because scheduled flight timestamps were not available in the supplied data.

9. Power BI Dashboard

The dashboard provides interactive analysis through:

KPI cards
Flights by Airline
Average Flight Duration by Airline
Booking Status Distribution
Top Routes by Traffic
Flight Volume by Date
Airline filtering
10. Data Model
DimFlightID ──→ Flights
     │
     └────────→ Bookings ←── DimPassenger
                       │
                       ↓
                   Payments

Dedicated dimensions are used to maintain reliable relationships and avoid incorrect aggregations.

11. Technology Stack

Python · Pandas · Jupyter Notebook · Power BI · GitHub

12. Project Structure
ASG-AIRLINES-ANALYTICS-PIPELINE/
│
├── README.md
├── ASSIGNMENT_NEOSTAT.ipynb
├── cleaned_data/
├── powerbi/
└── docs/
13. Deliverables
Data engineering notebook
Cleaned analytical datasets
Power BI dashboard
Dashboard screenshot
Architecture and data-flow documentation
Data model
Assumptions and transformation documentation
14. Conclusion

The project delivers a validated and privacy-aware data pipeline for ASG Airlines, enabling reliable operational analysis through Power BI while following data-quality, modelling, and governance practices.
