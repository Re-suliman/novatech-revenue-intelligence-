# NovaTech Revenue Intelligence & Executive Analytics Solution

## 📌 Executive Summary
This project delivers a unified enterprise analytics architecture and dashboard suite for **NovaTech**, eliminating business data silos across Marketing, Sales, and Customer Success domains. Built on **Amazon QuickSight**, the solution integrates raw CRM deals, marketing campaigns, and customer support tickets into an aligned data model coupled with conversational AI query capabilities (**Amazon Q Topics**).

---

## 🏗️ Architecture & Data Strategy
* **Primary Anchor:** `novatech_crm_deals.csv`
* **Joins Applied:**
  * **Join 1 (Left Join):** CRM Deals $\rightarrow$ Marketing Campaigns via `lead_id`
  * **Join 2 (Left Join):** Joined Deals Output $\rightarrow$ Support Tickets via `account_id`
* **Key Calculated Fields:**
  * **Conversion Rate:** `distinct_count({opportunity_id}) / distinct_count({lead_id})`
  * **Is Won:** `ifelse({Deal Outcome} = 'Won', 1, 0)`
  * **Ticket Resolution Days:** `dateDiff({ticket_created_date}, {ticket_resolved_date}, 'DD')`
  * **Open Tickets:** `ifelse({is_resolved} = 0, 1, 0)`

---

## 📊 Key Business Insights & Findings

### 1. Marketing Funnel
* Achieved an overall lead-to-opportunity conversion rate of **23.73%** (496 opportunities from 2,090 leads).
* **Organic Search** drives high raw volume, whereas **Partner Referral** demonstrates superior lead quality and downstream conversion speed.

### 2. Sales Pipeline
* Demonstrated a robust **63.75% Win Rate** across closed deals.
* Realized **$101.87M** in Closed-Won Deal Value out of a total evaluated pipeline of **$159.18M**.

### 3. Customer Health & Retention
* Identified **1,060 unresolved support tickets** with an average resolution velocity of **1.97 days**.
* **AlphaCore Technologies** represents the top retention risk, combining 171 unresolved support tickets with **$2.54M** in total deal exposure.

---

## 💡 Strategic Recommendations for VP Sarah Chen
1. **Marketing Optimization:** Reallocate acquisition budget toward **Organic Search** and **Partner Referrals** to decrease CAC while maintaining high conversion quality.
2. **Sales Acceleration:** Implement targeted closing interventions for mid-pipeline deals to capture the remaining **36.25%** ($57.3M) in uncaptured revenue potential.
3. **Customer Success Task Force:** Deploy a rapid-response support team dedicated to clearing support backlogs for high-value accounts, prioritizing **AlphaCore Technologies** to safeguard recurring revenue.

---

## 📁 Repository Structure
* `NovaTech_Revenue_Intelligence_Executive_Report.docx`: Complete Udacity submission report including Data Quality & Q Exploration Logs.
* `/dashboards/`: PDF exports of the 3-page interactive QuickSight dashboard (Marketing Funnel, Sales Pipeline, Customer Health).
* `/screenshots/`: Technical evidence including Data Join diagrams, Calculated Fields, and Amazon Q Before/After Topic validation logs.
