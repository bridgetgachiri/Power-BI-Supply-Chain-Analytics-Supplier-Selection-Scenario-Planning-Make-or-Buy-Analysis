# Make vs. Buy Analysis | Power BI

## Project Overview

Should a business manufacture a product internally or purchase it from an external supplier?

This project explores that procurement decision using Power BI. It compares estimated internal manufacturing costs including required capital investment with supplier purchasing costs across different volume scenarios.

The goal is to evaluate both options and identify which is more cost-effective under the selected scenario.

## Business Questions

- How do supplier costs compare across quoted volumes?
- How does the required capital investment affect the cost of manufacturing internally?
- How does the cost comparison change as the selected volume scenario changes?
- Which option offers the lower estimated total cost?

## Tools & Methods

**Tool:** Microsoft Power BI

**Key skills demonstrated:**
- Data visualization and interactive dashboard development
- DAX measures for scenario-based cost calculations
- Supplier quote and procurement cost comparison
- Manufacturing capacity and capital investment analysis
- Make-versus-buy cost modelling

### DAX & Business Logic

I developed DAX measures to evaluate procurement and manufacturing costs under different volume scenarios, including:

- **Buy Scenario Full Cost:** Calculates the minimum estimated purchasing cost among eligible supplier quotes.
- **Additional Unit Capacity Required:** Estimates the extra manufacturing capacity needed after accounting for existing capacity.
- **Capital Investment Required (Make):** Estimates the investment needed to provide additional manufacturing capacity.
- **Make Full Cost:** Combines estimated capital investment with variable manufacturing costs.
- **Cost Avoidance:** Calculates the absolute difference between the estimated making and buying costs.

## Dashboard Preview

### 1. Supplier Selection
Review supplier quotes, costs, and the factors that influence supplier selection.

![Supplier Selection Dashboard](screenshots/supplier-selection.png)

### 2. Scenario Analysis
Explore how estimated purchasing costs change across different volume scenarios.

![Scenario Analysis Dashboard](screenshots/scenario-analysis.png)

### 3. Make vs. Buy Analysis
Compare estimated internal manufacturing costs with supplier purchasing costs to support procurement decisions.

![Make vs Buy Analysis Dashboard](screenshots/make-vs-buy-analysis.png)
