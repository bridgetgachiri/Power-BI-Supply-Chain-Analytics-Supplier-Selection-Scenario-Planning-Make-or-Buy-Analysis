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

## Key Findings

### 1. The preferred option varies by part

The analysis showed that the more cost-effective option differed across the parts evaluated. For P0604, internal manufacturing had a lower estimated cost at the tested scenario volumes of 15,000, 30,000, and 60,000 units. For P0830, purchasing was cheaper at the tested volumes of 15,000 and 28,000 units. For P0914, manufacturing was cheaper at both 15,000 and 30,000 units.

These comparisons suggest that a single make-or-buy policy may not be appropriate for every part. Product-level cost comparisons can help procurement teams evaluate each decision individually.

### 2. Production volume affects the cost comparison

Testing different scenario volumes helped show how the estimated costs change as demand increases. The results for P0604 continued to favor manufacturing across the tested volumes. For P0914, manufacturing also remained cheaper in the two scenarios examined.

### 3. Capital investment is part of the manufacturing decision

The manufacturing calculation includes estimated capital investment for additional production capacity as well as variable production costs. This is important because comparing only unit prices could overlook the investment needed to manufacture a product internally.

### 4. Supplier Selection Requires More Than Comparing Unit Prices

The Supplier Selection page compares suppliers using unit cost and non-recurring expenses, while the supplier cost calculation also accounts for yield rate.

For part P1010 at a scenario volume of 5,000 units, the Lowest Cost Supplier card identified Ringo Nova. Ringo Nova had a quoted unit cost of $34.29, non-recurring expenses of $9,972 and a yield rate of 83%.

Widgetmakers Inc. had a higher unit cost of $44.71, lower non-recurring expenses of $8,289.91 and a yield rate of 72%.

Using the project's supplier cost formula, the estimated total cost was approximately $216,538.27 for Ringo Nova and $318,776.02 for Widgetmakers Inc. This represents an estimated difference of $102,237.76 in favor of Ringo Nova for this comparison.

The result demonstrates how a supplier with higher one-time expenses can still have a lower estimated total cost when unit cost and yield rate are considered together. The manual calculation compares these two suppliers; it does not independently establish the cost ranking of every supplier in the dataset.

## Preliminary Recommendation

Use the analysis as a decision-support tool to compare manufacturing and supplier purchasing costs by part and production volume. Before making an operational decision, validate the assumptions behind the cost estimates and consider factors such as production capacity, supplier reliability, lead times, and any costs not represented in the model.
