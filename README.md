# Northwind Traders Cloud Data Warehouse

## Introduction
Northwind Traders is a fictional trading company (created by Microsoft) that sells food, beverages, and other consumer goods. It operates a large distribution and supply network and requires a powerful Cloud Data Warehouse to efficiently analyze customers, sales, orders, and inventory data to make data-driven business decisions.

### Why a Cloud Data Warehouse?
A Cloud Data Warehouse enables Northwind Traders to consolidate and analyze data from multiple sources efficiently. This allows for better business insights and strategic decision-making.

#### Key Benefits of a Cloud Data Warehouse
✅ Improved Sales Analytics – Identify best-selling products, regions & customer behavior  
✅ Optimized Inventory Management – Prevent overstocking & shortages  
✅ Customer Insights – Understand purchasing patterns & preferences  
✅ Streamlined Shipping Processes – Track delivery times & shipping partners  
✅ Real-time Dashboards – Enable fast, data-driven business decisions  


## Implementation – Kimball Data Warehouse Lifecycle
Our implementation follows the Kimball Data Warehouse Methodology, focusing on business needs and efficient data modeling.

### Requirement Gathering
- Sales Overview: Comprehensive sales reports to understand what is selling, where it sells best, and what underperforms.
- Sales Agent Tracking: Track sales performance to adjust commissions and recognize high-performing sales agents.
- Product Inventory: Improve stock management by analyzing suppliers, purchases, and inventory levels.
- Customer Reporting: Allow customers to analyze their orders, track purchase history, and make data-driven buying decisions.

### Architecture Design
The Northwind Cloud Data Warehouse follows a layered architecture for scalability and efficient data processing:  

1️⃣ Data Sources (OLTP Systems) – Extracting data from relational databases, stored in BigQuery  
2️⃣ Staging Layer – Raw data storage in BigQuery Data Lake & initial transformations using dbt  
3️⃣ Dimensional Data Warehouse Layer – Transforming raw data into a Star Schema  
4️⃣ Reporting Layer (OBT – One Big Table) – Aggregated data for Business Intelligence    

### Data Modeling
#### 📍 Conceptual Data Modeling (Entity-Relationship Diagram, ERD)
Before implementation, we create an Entity-Relationship Diagram (ERD) using draw.io, defining relationships between key tables.  
🔗 [Conceptual Model](https://github.com/benigram/northwind_dwh/blob/main/northwind-conceptual.drawio.pdf)

#### 📍 Logical Data Modeling
Based on the ERD, a logical model is created to define the structure of tables and relationships.  
🔗 [Logical Model](https://github.com/benigram/northwind_dwh/blob/main/northwind-logical.drawio.pdf)

#### 📍 Physical Data Modeling
Once the logical model is finalized, the physical data warehouse is built in BigQuery.

## Setup & Implementation

### Requirements:
Python 3.8 or higher

### Setup
Install the virtual environment and the required packages by following commands:

```bash
python3 -m venv env
source env/bin/activate
```

### Project Structure
`dbt_project.yml` – dbt project configuration  
`dbt_profiles.yml` – Connection settings for BigQuery  
`models/` – Contains all dbt models (Staging, Dimensions, Facts)  
`snapshots/` – Stores historical changes  
`macros/` – Reusable Jinja scripts  