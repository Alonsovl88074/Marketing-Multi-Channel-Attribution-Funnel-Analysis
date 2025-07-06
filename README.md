# Marketing-Multi-Channel-Attribution-Funnel-Analysis
This project tackles a classic and critical problem in digital marketing: understanding how different marketing channels contribute to sales. It simulates a BI workflow where a Data Analyst receives regular CSV exports from multiple platforms (Google Ads, Facebook Ads, web analytics, CRM).

**Live Demo:** [https://colab.research.google.com/drive/1ICm4wy__0NqHR2vHofqOkGTgdwrs2TX0?usp=sharing]

## Project Overview

This project tackles a classic and critical problem in digital marketing: understanding how different marketing channels contribute to sales. It simulates a BI workflow where a Data Analyst receives regular CSV exports from multiple platforms (Google Ads, Facebook Ads, web analytics, CRM). The project's core is an ETL pipeline that cleans, integrates, and models this data to provide a unified view of marketing performance, including a last-touch attribution model and a full-funnel visualization.

## Business Problem

A company's marketing team invests its budget across several channels but struggles to measure the true effectiveness of each one. Their data lives in silos:
1.  **Ad Platforms (Google/Facebook):** Provide CSVs with spend, impressions, and clicks.
2.  **Web Analytics:** Provides a CSV of user sessions, including their traffic source.
3.  **Sales CRM:** Provides a CSV of all completed orders, linked to a User ID.

The CMO's key question is: "When we get a sale, which marketing effort should get the credit?" Without an answer, they risk over-investing in channels that seem to drive traffic but don't convert, and under-investing in channels that are crucial in the final steps of a customer's journey.

## Solution Architecture

The solution is a Python-based pipeline that performs data integration and attribution modeling. It's designed to be automated weekly to provide fresh insights to the marketing team.


## Attribution Modeling

To solve the core business problem, a **Last-Touch Attribution** model was implemented.

*   **Logic:** For each sale, the model looks back in time for that specific user and assigns 100% of the credit for the sale to the very last marketing channel they interacted with before making the purchase.
*   **Implementation:** This was achieved efficiently using `pandas.merge_asof`, which is specifically designed for these types of time-series lookups.
*   **Why Last-Touch?** While more complex models exist (e.g., linear, time-decay), last-touch is the industry standard starting point. It's simple to understand, implement, and provides a clear baseline for which channels are "closers." This project demonstrates the foundational skill upon which more complex models can be built.

## Key Skills & Technologies Demonstrated

*   **ETL from Disparate Sources:** Ingesting, cleaning, standardizing, and merging data from multiple CSV formats using **Pandas**.
*   **Attribution Modeling:** Implementing a programmatic last-touch attribution model to link marketing spend to revenue.
*   **Business Logic Implementation:** Translating a complex business need into a robust Python script.
*   **Data Aggregation:** Using `groupby` to create summary tables for analysis.
*   **KPI Calculation:** Calculating essential marketing metrics like **Return on Investment (ROI)**.
*   **Data Visualization for Storytelling:**
    *   Creating a **Funnel Chart** with **Plotly** to visualize customer drop-off at each stage.
    *   Building a clear **Bar Chart** to compare ROI across channels.
*   **Data Warehousing Concepts:** Structuring the final output in a way that's ready to be loaded into a data warehouse (e.g., SQLite).

## Key Insights & Visualizations

### Conversion Funnel

 <!-- Replace with a screenshot of your funnel chart -->

This funnel instantly highlights the efficiency of the marketing and sales process. It allows the team to ask critical questions like: "We get a lot of clicks, but why are so few turning into website sessions?" or "Where is the biggest drop-off in our customer journey?"

### ROI by Channel

 <!-- Replace with a screenshot of your ROI bar chart -->

This is the ultimate "money" chart for the CMO. It moves beyond vanity metrics like clicks and impressions to show which channels are actually generating a positive return.

**Insights:**

*   **High-ROI Channels (e.g., Google Ads):** Clearly profitable. The recommendation would be to see if the budget for this channel can be scaled while maintaining a similar ROI.
*   **Low/Negative-ROI Channels (e.g., Facebook Ads):** These channels are currently losing money. The recommendation is not necessarily to cut them, but to investigate *why*. Are we targeting the wrong audience? Is the ad creative ineffective? This chart pinpoints exactly where the marketing team needs to focus their optimization efforts.

## How to Run the Project

1.  Clone this repository.
2.  Open the `marketing_attribution_analysis.ipynb` file in Google Colab or a local Jupyter environment.
3.  The notebook is self-contained and generates its own sample data.
4.  Run all cells to execute the ETL pipeline, attribution model, and generate the final dashboards.
