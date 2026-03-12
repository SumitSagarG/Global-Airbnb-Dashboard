
# Global Airbnb Performance Dashboard (Power BI)

A **data analytics project built in Power BI** to analyze global Airbnb market trends, listing growth, pricing patterns, customer behavior, and trust signals across major cities.

The goal of this project is to **demonstrate end-to-end BI skills** including:

* Data modeling
* DAX calculations
* Business insight generation
* Interactive dashboard design

📄 Dataset: https://mavenanalytics.io/data-playground/airbnb-listings-reviews


---

# Business Problem

Airbnb operates in a complex global marketplace where supply, pricing, reviews, and seasonality vary across cities.

Key questions addressed in this analysis:

* How has Airbnb listing supply evolved over time?
* Which cities dominate the global market?
* How do pricing patterns differ across property types?
* What factors influence customer ratings?
* How frequently do customers review listings?
* Are there seasonal patterns in travel demand?
* How strong are trust signals (profile picture + identity verification)?

The dashboard provides **data-driven insights to understand marketplace dynamics**. 

---

# Dataset Overview

The dataset contains global Airbnb listing information including hosts, reviews, pricing, and ratings.

**Core metrics analyzed:**

| Metric         | Value        |
| -------------- | ------------ |
| Listings       | 279,712      |
| Hosts          | 182,000      |
| Reviews        | 5.37 Million |
| Cities         | 10           |
| Property Types | 144          |

These metrics provide a large sample size for analyzing platform trends. 

---

# Dashboard Features

The dashboard includes several analytical sections:

### 1. Listing Growth Lifecycle

Tracks Airbnb's platform expansion from **2008–2022**, highlighting:

* Growth phase
* Regulatory slowdown
* COVID-19 impact

The data shows that **2015 was the peak year for new listings**, followed by regulatory tightening and later recovery. 

---

### 2. Market Share by City

Analyzes listing distribution and cumulative market share.

Key finding:

* **Paris, New York, and Sydney account for nearly 50% of listings and reviews**

This shows a strong **market concentration in major tourism hubs**. 

---

### 3. Property Pricing Analysis

Average pricing by property type:

| Property Type | Avg Price |
| ------------- | --------- |
| Hotel Room    | $800      |
| Entire Place  | $673      |
| Shared Room   | $580      |
| Private Room  | $462      |

This reveals the **price premium for hotel listings relative to Airbnb private rooms**. 

---

### 4. Ratings Analysis

Ratings were analyzed across:

* Accuracy
* Cleanliness
* Communication
* Location
* Value

Key insights:

* **Top rated cities:** Mexico City, Rio de Janeiro
* **Lowest rated:** Hong Kong, Istanbul
* **Lowest scoring category overall:** Value for money

These insights help hosts understand **service quality drivers**. 

---

### 5. Review Frequency Analysis

Review frequency helps measure **customer engagement**.

Findings:

* **86.3% of customers leave only one review**
* **98.8% leave 3 or fewer reviews**

This indicates most Airbnb users interact with the platform **infrequently rather than repeatedly reviewing listings**. 

---

### 6. Travel Seasonality

The dashboard identifies seasonal tourism patterns:

* **Paris and Rome dominate April–August reviews**
* **New York spikes during November–December holidays**

This reveals how **tourism demand varies by geography and season**. 

---

### 7. Trust Indicators

Trust signals evaluated include:

* Profile pictures
* Identity verification

Findings:

* **66.9% of hosts have both profile picture and verified identity**
* Only **0.3% lack both**

This indicates high levels of **platform trust and verification compliance**. 

---

# Data Model

The project uses a **star-like schema** with fact tables and dimension tables.

**Main tables:**

Fact Tables

* Listings
* Reviews

Dimension Tables

* Hosts
* Cities
* Property Types
* Ratings

Relationships were optimized to enable **fast aggregations and interactive filtering**.

---

# Key DAX Measures

Examples of measures used in the dashboard:

### Reviews Per Reviewer

```DAX
Reviews Per Reviewer =
CALCULATE(
    COUNT(Reviews[review_id]),
    ALLEXCEPT(Reviews, Reviews[reviewer_id])
)
```

---

### Cumulative Reviewers

```DAX
Cumulative Reviewers =
VAR CurrentReviews =
    MAX(Reviews[Reviews Per Reviewer])
RETURN
CALCULATE(
    DISTINCTCOUNT(Reviews[reviewer_id]),
    FILTER(
        ALL(Reviews[Reviews Per Reviewer]),
        Reviews[Reviews Per Reviewer] <= CurrentReviews
    )
)
```

---

### Cumulative % Review Frequency

```DAX
Cumulative % Review Frequency =
DIVIDE([Cumulative Reviewers], [Total Reviewers])
```

These measures power the **review frequency distribution analysis** in the dashboard.

---

# Skills Demonstrated

This project highlights the following skills:

**Data Analysis**

* Exploratory data analysis
* Behavioral analysis
* Trend analysis

**Power BI**

* Data modeling
* Interactive dashboards
* Visual storytelling

**DAX**

* Cumulative measures
* Context manipulation
* Aggregations

**Business Intelligence**

* KPI identification
* Insight generation
* Data-driven decision support

---

# Key Takeaways

This project demonstrates how **data analytics can reveal platform dynamics**:

* Airbnb supply growth is strongly affected by regulation and global events.
* Listings are heavily concentrated in major tourism cities.
* Pricing varies significantly by property type.
* Most users leave very few reviews.
* Tourism demand shows strong seasonal patterns.

---

# Project Structure

```
Airbnb-PowerBI-Dashboard
│
├── dashboard.pdf
├── dataset
├── README.md
└── images

