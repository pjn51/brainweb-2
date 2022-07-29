# Stash-O-Matic
#hub #stash

---
## Introduction
The overall goal of this project is to automate the system of managing [[cash flow]] for Stashlogix. 

## Goals
We want to know when we should purchase new products, and how many to buy. We also want to know when to apply discounts for which products, and what channels to apply them to.

We want to determine what POs should be placed, on what days, and at what quantities. 

#### Cash management
We want to make sure that Stashlogix stays liquid.

#### Inventory management
See [[economic order quantity]]. We need to manage purchase orders (POs) monthly basically. We want to order just enough to stay in-stock before the next shipment arrives.

EOQ models don't take into account cash on hand. That's an issue.

## Data management
See my note, [[stash-o-matic database]], for details.

## Low balance alarm system
Goal: create an early warning system that will alert me if cash flow is about to go negative. It should return the date that the issue will occur.

I will need to have access to the cash balance per day, and the date.

## Sell-out alarm system
Goal: create an early-warning system that will alert a user if the quantity of a product is about to hit zero. Forecast horizon should be workable depending on lead time needed to order additional stock.

## Model 
- [[stash-o-matic model]]

---
## Timeline
- [[stash-o-matic timeline]]
- [[stash-o-matic trajectory]] for medium and long-term goals

## Further reading
- [[stash-o-matic model]]