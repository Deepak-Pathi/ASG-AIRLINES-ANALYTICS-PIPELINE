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
Power BI Dashboard
