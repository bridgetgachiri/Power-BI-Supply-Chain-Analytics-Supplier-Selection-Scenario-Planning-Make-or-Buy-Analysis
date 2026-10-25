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

## Preliminary Findings

### Part P0604 — Scenario Volume: 60,000 Units

The initial cost comparison indicates that internal manufacturing may be the more cost-effective option for part P0604 at a selected scenario volume of 60,000 units.

- **Estimated Make Full Cost:** $382,540.00
- **Estimated Buy Scenario Full Cost:** $2,532,285.54
- **Absolute Cost Difference:** $2,149,745.54

Based on these estimates, internal manufacturing has a substantially lower calculated cost than purchasing from a supplier. This result highlights the importance of evaluating capital investment and production costs alongside supplier quotes when making procurement decisions.

### Key Finding: Make vs. Buy — Part P0604

At a selected scenario volume of 60,000 units, the estimated internal manufacturing cost for part P0604 was $382,540, compared with $2,532,285.54 for the lowest-cost eligible supplier quote. This represents an estimated cost difference of $2,149,745.54, or approximately 84.9% lower cost for the make option.

The manufacturing estimate includes $280,000 in capital investment for additional production capacity and $102,540 in estimated variable production costs. These results suggest that internal manufacturing may be the more cost-effective option under this scenario, subject to validating that the two alternatives have comparable cost coverage and assumptions.
