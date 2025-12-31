# Household Survey Tracking and Attrition Analysis 

This repository contains Stata code and datasets used to track households across **baseline and midline surveys**, analyze **survey attrition**, and classify **household and structure status** in a field-based survey setting.

---

## Overview

This project focuses on linking household records between **baseline and midline survey waves** and identifying reasons for **sample attrition**, such as:

- Households that could not be located
- Structures that were torn down
- Households that withdrew consent
- Successfully re-contacted and surveyed households

The analysis is implemented entirely in **Stata** and demonstrates practical skills in **data cleaning, merging, tracking survey outcomes, and fieldwork validation**.

---

## Project Motivation

Longitudinal surveys often face challenges such as household mobility, structural changes, and non-response.  
Accurately tracking households across survey rounds is critical for:

- Minimizing attrition bias
- Ensuring data quality
- Improving the credibility of impact evaluations and panel studies

This project demonstrates how to systematically identify and categorize these outcomes using administrative survey data.

---

## Data

### Survey Waves
- **Baseline survey data**
- **Midline survey data**

### Key Files
- `baseline_data.dta` — Baseline household listing and consent status  
- `midline_data.dta` — Midline visit results and tracking information  
- `linking_file.dta` — Structure and household status linking file  

### Key Identifiers
- `UHHID_bl` — Baseline household ID  
- `UHHID_midline` — Midline household ID  
- `StructureID` — Physical structure identifier  

---

## Data Processing Steps

The analysis includes the following steps:

- Validation of household availability and consent at baseline
- Identification of matched households across survey waves
- Detection and removal of duplicate household IDs
- One-to-one merging of baseline and midline data
- Classification of survey outcomes:
  - House located
  - Unable to locate household
  - Structure torn down
  - Household contacted but withdrawn
  - Survey successfully completed

Each step is documented and reproducible through Stata code.

---

## Key Outcomes

### Survey Tracking Results
- Majority of baseline households were successfully matched to midline records
- Attrition occurred due to:
  - Physical disappearance of structures
  - Inability to locate households
  - Withdrawal after contact

### Classification Variables Created
- `matched` — Household matched across waves
- `structure_no_exists` — Structure torn down
- `unable_to_locate` — Household not found
- `located_not_torndown` — Structure found and intact
- `survey_complete_located` — Successfully surveyed households
- `hh_contacted_withdrawn` — Contacted but withdrawn households

These variables enable transparent attrition accounting.

---

## Repository Structure

- `mig_codes.do` — Complete Stata do-file containing all data cleaning, merging, and classification logic
- `Stata_results.log` — Execution log with outputs and validation checks
- `baseline_data.dta` — Baseline household dataset
- `midline_data.dta` — Midline household tracking dataset
- `linking_file.dta` — Structure and household status linkage file

---

## How to Run the Analysis

### Requirements
- **Stata (any recent version)**

### Steps
1. Clone or download this repository
2. Open Stata
3. Set your working directory to the project folder
4. Run:
   ```stata
   do mig_codes.do
