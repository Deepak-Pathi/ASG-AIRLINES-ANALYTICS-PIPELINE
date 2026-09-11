# ASG Airlines – End-to-End Data Engineering

## 1. Project Overview

This project implements an end-to-end data engineering pipeline for ASG Airlines. It transforms raw flight, booking, passenger, and payment data into clean, validated, privacy-aware datasets for business intelligence and operational reporting.

**Pipeline:**  
`Ingestion → Quality Assessment → Cleaning → Transformation → PII Protection → Validation → KPI Preparation → Power BI`

---

## 2. Problem Statement

The raw airline data contains data-quality challenges such as missing values, duplicates, inconsistent values, problematic timestamps, cross-day flight records, and sensitive passenger information.

The objective is to build a reliable pipeline that resolves these issues and produces trustworthy data for operational analysis and reporting.

---

## 3. Objectives

- Ingest and understand the provided airline datasets.
- Identify and resolve data-quality issues.
- Standardize and transform flight, booking, passenger, and payment data.
- Handle flight-duration and overnight-flight scenarios.
- Protect sensitive passenger information.
- Validate data quality and referential integrity.
- Prepare business KPIs and analytical datasets.
- Develop an interactive Power BI dashboard.
- Document architecture, data flow, data model, and assumptions.

---

## 4. Dataset

The project uses four datasets:

| Dataset | Purpose |
|---|---|
| **Flights** | Flight, route, airline and timing information |
| **Bookings** | Booking and passenger-flight relationships |
| **Passengers** | Passenger information |
| **Payments** | Booking payment information |

---

## 5. Solution Architecture

```text
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
Power BI
      ↓
Operational Dashboard
```

The solution is implemented locally using Python/Pandas. The architecture can be migrated to Azure Data Factory, Databricks, Spark, or Microsoft Fabric for larger-scale processing.

---

## 6. Data Quality & Transformation

Key processing steps include:

- Removal of exact duplicate records.
- Validation of flight identifiers.
- Handling of missing and unknown airline values.
- Standardization of airline and route values.
- Conversion and validation of timestamps.
- Flight-duration calculation.
- Handling of valid overnight flights.
- Removal of an invalid temporal flight record.
- Referential integrity validation.
- Numeric validation of payment amounts.

All transformation decisions are documented in the project notebook.

---

## 7. PII Protection

Sensitive information is protected before analytical use:

- Aadhaar → SHA-256 hash
- Passport number → SHA-256 hash
- Email → Masked
- Phone → Masked
- Date of birth → Birth year
- Emergency contact details → Removed

Raw PII-containing datasets should not be committed to the public repository.

---

## 8. Key KPIs

The solution supports the required KPIs:

- **Average Flight Duration:** 2.74 hours
- **Total Flights:** 1,004
- **Total Bookings:** 999
- **Cancelled Bookings:** 314
- **Cancellation Rate:** 31.43%
- **Total Payment Amount:** ~₹7.37M
- Route-wise Traffic
- Flights by Airline
- Flight Duration Anomalies

Traditional flight-delay calculation is not performed because scheduled timestamps are not available in the supplied data.

---

## 9. Power BI Dashboard

The dashboard provides interactive operational insights through:

- KPI cards
- Flights by Airline
- Average Flight Duration by Airline
- Booking Status Distribution
- Top Routes by Traffic
- Flight Volume by Date
- Airline slicer and interactive filtering

---

## 10. Data Model

The Power BI model uses dedicated dimensions to maintain reliable relationships:

```text
DimFlightID ──→ Flights
     │
     └────────→ Bookings ←── DimPassenger
                       │
                       ↓
                   Payments
```

This structure prevents incorrect aggregations caused by one-to-many relationships.

---

## 11. Project Structure

```text
ASG-Airlines-Data-Engineering/
│
├── README.md
├── notebooks/
│   └── ASSIGNMENT_NEOSTAT.ipynb
├── data/
│   └── cleaned/
├── powerbi/
│   ├── ASG_Airlines_Dashboard.pbix
│   └── dashboard_screenshot.png
├── docs/
│   ├── architecture.png
│   ├── data_flow_diagram.png
│   └── data_model.png
└── .gitignore
```

---

## 12. Technology Stack

**Python · Pandas · Jupyter Notebook · Power BI · GitHub**

---

## 13. Deliverables

- Working data engineering notebook
- Cleaned analytical datasets
- Power BI dashboard
- Dashboard screenshot
- Architecture, DFD and data model
- Project documentation and assumptions

---

## 14. Conclusion

The project delivers a validated and privacy-aware analytical pipeline for ASG Airlines, enabling reliable operational insights through Power BI while maintaining clear data-quality, modelling, and governance practices.
