# DAX Measures Documentation
## Make vs. Buy Analysis | Power BI

This document explains the DAX measures developed for the Make vs. Buy Analysis project. The measures support supplier cost comparison, internal manufacturing cost estimation, capacity planning, and make-or-buy evaluation.

Each measure includes its formula, purpose, explanation, and business application.

---

## 1. Buy Scenario Full Cost

**Business purpose:** Estimate the total purchasing cost for a selected production volume using eligible supplier quotes.

### DAX formula

```dax
Buy Scenario Full Cost =
MINX(
    FILTER(
        Quotes,
        Quotes[Volume] <= 'Scenario Volume'[Scenario Volume Value]
    ),
    (
        [Scenario Volume Value] * Quotes[Unit_Cost]
        / Quotes[Yield Rate]
    )
    + Quotes[Non_recurring_expenses]
)
```

### How it works

- `FILTER` selects supplier quotes where the quoted volume is less than or equal to the selected scenario volume.
- The selected scenario volume is multiplied by the supplier's unit cost and divided by the yield rate.
- Non-recurring expenses are added to the calculated production cost.
- `MINX` evaluates the eligible quotes and returns the minimum calculated cost.

### Business application

This measure supports supplier selection by comparing estimated total purchasing costs rather than relying on unit cost alone. It accounts for yield rate and non-recurring expenses, which can affect the overall cost of a supplier's quote.

**Used in:** Scenario Analysis and Make vs. Buy Analysis.

---

## 2. Make Full Cost

**Business purpose:** Estimate the total cost of manufacturing a selected production volume internally.

### DAX formula

```dax
Make Full Cost =
MINX(
    Internal_Mfg_Resource_Estimates,
    [Capital Investment Required (Make)]
        + Internal_Mfg_Resource_Estimates[Cost_per_Unit]
            * 'Scenario Volume'[Scenario Volume Value]
)
```

### How it works

For each evaluated manufacturing resource estimate, the measure combines:

- The capital investment required for additional capacity.
- The manufacturing cost per unit multiplied by the selected scenario volume.

`MINX` returns the minimum calculated result across the manufacturing resource estimates evaluated in the current filter context.

### Business application

This measure estimates the cost of internal production and supports comparison with the lowest calculated supplier purchasing cost. Including capital investment helps account for the potential cost of expanding production capacity.

**Used in:** Make vs. Buy Analysis.

---

## 3. Capital Investment Required (Make)

**Business purpose:** Estimate the investment needed to obtain additional manufacturing capacity.

### DAX formula

```dax
Capital Investment Required (Make) =
MINX(
    Internal_Mfg_Resource_Estimates,
    ROUNDUP(
        [Additional Unit Capacity Required]
            / MIN(Internal_Mfg_Resource_Estimates[Unit_Capacity]),
        0
    )
        * Internal_Mfg_Resource_Estimates[Machine_Fixed_Cost]
)
```

### How it works

- The additional capacity requirement is divided by the unit capacity used in the calculation.
- `ROUNDUP` rounds the result up to a whole number of machines, since a partial machine cannot be purchased.
- The resulting machine count is multiplied by the fixed cost per machine.
- `MINX` returns the minimum calculated investment across the manufacturing resource estimates evaluated.

### Business application

This measure helps assess whether internal manufacturing requires additional investment. If existing capacity is sufficient and the additional capacity requirement is zero, the calculated investment can be zero.

**Used in:** Make vs. Buy Analysis and as an input to Make Full Cost.

**Validation note:** The formula uses `MIN(Internal_Mfg_Resource_Estimates[Unit_Capacity])` inside an iterator. The result depends on the active filter context. Confirm that this is the intended capacity value for each evaluated manufacturing resource before treating the measure as fully validated.

---

## 4. Additional Unit Capacity Required

**Business purpose:** Calculate how much additional manufacturing capacity is needed to meet the selected scenario volume.

### DAX formula

```dax
Additional Unit capacity required =
MINX(
    Internal_Mfg_Resource_Estimates,
    MAX(
        'Scenario Volume'[Scenario Volume Value]
            - Internal_Mfg_Resource_Estimates[Existing_Capacity],
        0
    )
)
```

### How it works

- The selected scenario volume is compared with existing manufacturing capacity.
- Existing capacity is subtracted from the scenario volume.
- `MAX(..., 0)` prevents the additional capacity requirement from becoming negative.
- `MINX` returns the minimum calculated additional capacity requirement across the manufacturing resource estimates evaluated.

### Business application

This measure helps determine whether existing production capacity can meet the scenario demand or whether additional capacity may be required. It contributes to the capital investment calculation and the overall manufacturing cost estimate.

**Used in:** Make vs. Buy Analysis and as an input to Capital Investment Required (Make).

**Validation note:** Because `MINX` returns the minimum result, confirm that taking the minimum across the evaluated manufacturing resource estimates reflects the intended capacity-planning logic for the business problem.

---

## 5. Cost Avoidance

**Business purpose:** Quantify the absolute cost difference between manufacturing internally and purchasing from a supplier.

### DAX formula

```dax
Cost Avoidance =
ABS(
    [Make Full Cost] - [Buy Scenario Full Cost]
)
```

### How it works

- The measure subtracts the estimated purchasing cost from the estimated manufacturing cost.
- `ABS` converts the result to a non-negative value.

### Business application

This measure quantifies the financial gap between the two alternatives. It can help communicate the magnitude of the difference to decision-makers.

However, because the measure uses `ABS`, it does not indicate which alternative is cheaper. The `Make Full Cost` and `Buy Scenario Full Cost` measures must be compared directly to determine the lower-cost option.

**Used in:** Make vs. Buy Analysis.

---

## Summary of Measures

| Measure | Primary purpose |
|---|---|
| `Buy Scenario Full Cost` | Estimates supplier purchasing cost |
| `Make Full Cost` | Estimates internal manufacturing cost |
| `Capital Investment Required (Make)` | Estimates additional manufacturing investment |
| `Additional Unit capacity required` | Estimates capacity needed beyond existing capacity |
| `Cost Avoidance` | Measures the absolute difference between make and buy costs |

## Project Takeaway

These measures demonstrate how DAX can translate supplier quotes, production assumptions, and capacity information into financial estimates for business analysis.

Together, they support an interactive approach to make-or-buy evaluation. Their outputs should be interpreted in the context of the underlying data, filter context, and model assumptions, and validated before being used for actual sourcing or production decisions.
