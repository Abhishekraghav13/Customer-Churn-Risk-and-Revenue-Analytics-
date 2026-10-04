# Customer-Churn-Risk-and-Revenue-Analytics-

##  Project Overview

Customer retention is a critical business challenge for subscription-based businesses, where understanding **who is likely to churn, why they churn, and when they become high-risk** can directly influence revenue and customer lifetime value.

This project presents an end-to-end **Churn Analysis and Customer Intelligence** workflow for an OTT subscription platform. The analysis integrates customer demographics, subscription information, and customer-support interactions to identify churn patterns, quantify revenue exposure, segment customers by risk, and develop actionable retention strategies.

The project combines **SQL, Python, exploratory data analysis, feature engineering, visualization, and business analytics** to transform raw relational data into actionable customer insights.

---

##  Business Objective

The primary objective is to understand customer churn from three perspectives:

* **Who** – Which customers and customer segments are most likely to churn?
* **Why** – What customer, subscription, or support-related factors are associated with churn?
* **When** – When do customers enter a high-risk or "danger zone" before cancellation?

The analysis focuses on identifying high-risk customer segments and translating those findings into **revenue-focused retention strategies**.

---

##  Technology Stack

## Tools & Technologies

- **Programming:** Python
- **Database:** SQL, SQLite
- **Data Analysis:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Analytics:** EDA, Feature Engineering, KPI Analysis
- **Business Analysis:** Churn Analysis, Customer Segmentation, Risk Analysis
---

##  Dataset Structure

The analysis uses three relational tables from the `customer_churn` database.

### 1. Customer Table — `db_customer`

Contains customer demographic and profile information.

| Column       | Description                |
| ------------ | -------------------------- |
| `customerid` | Unique customer identifier |
| `name`       | Customer name              |
| `country`    | Customer country           |
| `state`      | Customer state             |
| `gender`     | Customer gender            |
| `dob`        | Date of birth              |
| `interests`  | Customer interests         |
| `pincode`    | Customer postal code       |

### 2. Subscription Table — `db_subscription`

Contains subscription and revenue-related information.

| Column                    | Description                  |
| ------------------------- | ---------------------------- |
| `customerid`              | Customer identifier          |
| `subscription_start_date` | Subscription start date      |
| `subscription_type`       | Subscription category        |
| `renewal_date`            | Renewal date                 |
| `plan_type`               | Basic / Standard / Premium   |
| `contract_type`           | Monthly / Annual             |
| `cancellation_date`       | Cancellation date            |
| `cancellation_reason`     | Reason for cancellation      |
| `monthly_charges`         | Monthly subscription revenue |
| `cltv`                    | Customer Lifetime Value      |
| `churn_score`             | Customer churn-risk score    |

### 3. Support Table — `db_support`

Contains customer-support interaction data.

| Column           | Description                       |
| ---------------- | --------------------------------- |
| `customerid`     | Customer identifier               |
| `complaint_date` | Date of complaint                 |
| `escalations`    | Number / indicator of escalations |
| `csat_score`     | Customer satisfaction score       |
| `comment`        | Support interaction comments      |

---

## Project Workflow

```text
Relational Database
        ↓
SQL Data Extraction
        ↓
Python + Pandas Integration
        ↓
Data Cleaning & Quality Checks
        ↓
Feature Engineering
        ↓
Exploratory Data Analysis
        ↓
Customer Segmentation & Risk Analysis
        ↓
Revenue & Churn Impact Analysis
        ↓
Visualization
        ↓
Business Insights
        ↓
Retention Recommendations
```

---

## 1 Data Extraction

The first stage involved connecting Python to the SQL database and extracting relevant information from multiple relational tables.

Key activities included:

* Connecting Python with the SQL database
* Writing SQL queries for data extraction
* Joining customer, subscription, and support datasets
* Selecting relevant attributes for analysis
* Creating an integrated customer-level analytical dataset

The relational structure allowed customer behavior to be analyzed across **demographics, subscription characteristics, revenue, and support interactions**.

---

## 2️ Data Cleaning & Quality Checks

The extracted data was cleaned and prepared for analysis using **Pandas and NumPy**.

Key preprocessing steps included:

* Inspecting data types
* Renaming columns where required
* Selecting relevant variables
* Checking duplicate records
* Identifying missing and null values
* Performing data-quality checks
* Converting date fields into appropriate formats
* Validating calculated metrics

This ensured that downstream analysis and KPI calculations were based on consistent and reliable data.

---

## 3️ Feature Engineering

Additional analytical features were created to capture customer behavior and risk.

Examples include:

* Customer tenure
* Churn indicators
* Churn-risk categories
* Contract-type segmentation
* Revenue-at-risk indicators
* Customer aging metrics
* Support escalation indicators

A **multi-dimensional churn-risk approach** was used by combining signals such as:

* Subscription tenure
* Plan type
* Contract structure
* Churn score
* Support escalations
* Customer complaints

Customers were subsequently segmented into different risk categories to identify high-priority retention opportunities.

---

## 4️ Key Business KPIs

The project calculated more than **20 analytical KPIs** covering churn, retention, revenue, customer value, and support behavior.

### Churn Rate

```text
Churn Rate =
Number of Churned Customers / Total Customers
```

### Retention Rate

```text
Retention Rate = 1 - Churn Rate
```

### Churn by Plan Type

Churn rates were calculated separately for:

* Basic
* Standard
* Premium

### Churn by Geography

Customer churn was analyzed across:

* Country
* State

This helped identify geographic concentration of churn.

### ARPU

```text
ARPU =
Total Monthly Charges / Number of Active Customers
```

### Average Customer Tenure

Average duration of customer relationships was calculated using subscription start and cancellation/current dates.

### Revenue at Risk

Customers with high churn scores were used to estimate potential monthly revenue exposure.

```text
Revenue at Risk =
SUM(Monthly Charges)
WHERE Churn Score > 70
```

### Escalation Rate

```text
Escalation Rate =
Total Escalations / Total Complaints × 100
```

### Average Complaints per Customer

```text
Average Complaints =
Total Complaints / Distinct Customers
```

### Support–Churn Relationship

Churn rates were compared between customers:

* With support escalations
* Without support escalations

This helped assess whether support issues were associated with higher churn risk.

---

##  Key Findings

### Overall Churn

* **Overall churn rate:** 28.6%
* **Retention rate:** 71.4%

Approximately 3 out of every 10 customers in the analyzed dataset had churned.

### Contract-Type Churn

One of the strongest patterns identified was the difference between monthly and annual subscribers:

| Contract Type | Churn Rate |
| ------------- | ---------: |
| Monthly       |      55.6% |
| Annual        |       8.3% |

Monthly subscribers showed approximately **6.7× higher churn** than annual subscribers.

This indicates that contract structure is a significant factor associated with customer retention.

### Revenue Impact

The analysis identified:

* **₹73.94/month** in MRR leakage associated with the identified high-risk customers
* **₹2,047** in CLTV erosion
* Approximately **18% revenue loss** relative to the analyzed revenue base
* **₹395** total revenue in the analyzed dataset

### Customer Tenure

* **Average customer tenure:** 1,451 days

### Geographic Concentration

* The highest concentration of observed churn occurred in **Karnataka**.
* September 2024 showed a notable concentration of cancellation activity.

These patterns suggest the need for further investigation into regional pricing, customer experience, technical issues, and competitive factors.

---

##  Customer Risk Analysis

The project used a composite approach to identify customers with elevated churn risk.

Risk signals included:

```text
Customer Risk
    ├── Tenure
    ├── Contract Type
    ├── Plan Type
    ├── Churn Score
    ├── Complaints
    └── Support Escalations
```

Customers were categorized into risk tiers to help prioritize retention efforts.

Rather than treating every customer equally, the analysis focuses on identifying customers where intervention is likely to generate the greatest **revenue and lifetime-value impact**.

---

##  Revenue & Customer Lifetime Value Analysis

Churn analysis was extended beyond simply measuring the number of customers lost.

The analysis examined:

* Monthly recurring revenue leakage
* Customer Lifetime Value erosion
* Revenue exposure among high-risk customers
* Differences between churned and retained customer cohorts
* Revenue implications of contract structure

This shifts the analysis from:

> **"How many customers are churning?"**

to:

> **"Which customers are churning, how much revenue is at risk, and where should the business intervene?"**

---

##  Business Insights

### 1. Monthly contracts represent a high-risk segment

The large difference between monthly and annual churn suggests that monthly subscribers should be a priority segment for retention initiatives.

### 2. Basic-plan churn should be interpreted through a revenue lens

Although the Basic plan contributes a large share of churned customers, its impact on total revenue needs to be evaluated based on customer value and revenue contribution rather than customer count alone.

### 3. Geographic churn concentration requires investigation

The concentration of churn in Karnataka suggests potential regional factors such as:

* Pricing changes
* Service or technical issues
* Customer-support problems
* Competitive activity
* Product/content preferences

### 4. Support interactions can provide early-warning signals

Customers experiencing complaints or escalations represent a potentially important group for proactive retention analysis.

### 5. Contract migration can be a retention lever

Given the substantially lower churn observed among annual subscribers, encouraging suitable monthly customers to migrate toward annual plans could potentially improve retention and long-term revenue stability.

---

##  Recommended Business Actions

Based on the analysis, the following actions were identified:

### 1. Prioritize High- and Medium-Risk Customers

Create targeted retention campaigns for customers with elevated churn scores.

Potential channels:

* Email
* SMS
* Phone outreach
* Personalized offers
* Customer-support intervention

### 2. Investigate Karnataka Churn

Conduct a deeper investigation into:

* Regional pricing
* Customer complaints
* Technical/service issues
* Cancellation reasons
* Competitor activity

### 3. Investigate September 2024

Analyze whether the September churn spike coincided with:

* Subscription price changes
* Product changes
* Content changes
* Technical disruptions
* Competitor campaigns
* Customer-support issues

### 4. Encourage Contract Migration

Identify suitable monthly subscribers and evaluate incentives for moving to annual contracts.

Potential benefits include:

* Improved retention
* More predictable recurring revenue
* Higher customer lifetime value
* Lower acquisition pressure

### 5. Prioritize Customers by Financial Impact

Retention resources should not be allocated solely based on churn probability.

A stronger prioritization framework is:

```text
Retention Priority =
Churn Risk × Customer Value × Revenue at Risk
```

This allows the business to focus on customers where successful intervention can create the greatest financial impact.

---

##  Business Impact

The analysis demonstrates how customer-level data can be transformed into actionable retention intelligence.

The project connects:

```text
Customer Behavior
       +
Subscription Data
       +
Support Interactions
       ↓
Churn Risk
       ↓
Revenue Exposure
       ↓
Retention Strategy
```

The key outcome is a shift from **descriptive churn reporting** toward **customer-level risk prioritization and revenue-focused decision-making**.

---

##  Key Analytical Questions

The project addresses questions such as:

1. What is the overall customer churn rate?
2. Which subscription plans have the highest churn?
3. Do monthly customers churn more than annual customers?
4. Which geographic regions have higher churn?
5. What is the average customer tenure?
6. How much revenue is exposed to high-risk customers?
7. How much CLTV is lost due to churn?
8. Are support escalations associated with higher churn?
9. Which customer segments should receive retention interventions?
10. How can contract migration improve customer retention?

---

##  Project Structure

```text
Churn-Analysis-Customer-Intelligence/
│
├── data/
│   └── customer_churn/
│
├── sql/
│   └── churn_analysis.sql
│
├── notebooks/
│   └── churn_analysis.ipynb
│
├── python/
│   └── data_analysis.py
│
├── visualizations/
│   └── charts/
│
├── presentation/
│   └── churn_insights.pptx
│
└── README.md
```

---

##  Skills Demonstrated

* SQL querying and relational data extraction
* Python-based data analysis
* Pandas and NumPy
* Data cleaning and preprocessing
* Feature engineering
* Exploratory Data Analysis
* Customer segmentation
* Churn and retention analysis
* Risk scoring
* KPI development
* Revenue-at-risk analysis
* Customer Lifetime Value analysis
* Data visualization
* Business insight generation
* Data-driven retention strategy

---

##  Author

**Abhishek Raghav**
B.Tech Civil Engineering | National Institute of Technology Warangal

