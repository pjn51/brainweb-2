# Stash-o-Matic Model
`TAGS:` 

---
## Introduction
This model is part of the [[stash-o-matic project]]. 

## 1. General goals
I want to maximize business performance. This means maintaining liquidity, preventing sell-outs, and maximizing revenue and ultimately profit. 

## 1.1. Input
This tool will take the [[loss function]] [[hyperparameters]], as well as sales forecasts for each SKU. 

## 1.2. Output
This tool should output the date, quantity, and contents of the ideal purchase order. This means there are really three optimization problems that are interconnected. 

## 1.2.1. Ideal order date
This should take into account the lead time needed for the factory, about one month. 

## 1.2.2. Ideal order contents
This is more complicated. 

## 1.2.3. Ideal order quantity per item

## 2. Assumptions
This model is going to have a lot of assumptions. The user inputs assume that the user is roughly aware of future sales, which is a big one.

## 3. Loss function
See my note, [[stash-o-matic loss function]], for details. 

## 4. Baseline model
I want to create a very naive baseline model that I can compare candidate models to. 

## 4.1. Baseline purchase date
I could just have a baseline recommendation to order more products every 30 days. 

## 4.2. Baseline order quantity per product
I could just recommend that items be replaced.

## 4.3. Baseline SKU mixture
This is harder to make a baseline for. Maybe just recommend that items be purchased in the same proportions as they were sold in the last 30 days?

## 5. Optimizing purchase date
Let's start with a single product. That means we want to tell the user when to order more of product $X$ before selling out, with a certain buffer period. We are given daily estimated sales of product $X$. 

$$
\text{order more when} \ \ \ I = S_x \cdot B
$$

- $I$ = inventory
- $S_x$ = daily sales of product $X$ (units)
- $B$ = buffer period (days)

The buffer period, $B$, should include shipment time and a little extra, so that if the model is off we don't sell out. 

## 6. Optimizing order quantity per product
Starting with a single product, I feel like we can use [[economic order quantity]] to figure this out. The standard EOQ formula is...

$$
Q^* = \sqrt{\frac{2DK}{h}}
$$

- $Q^*$ = optimal order quantity
- $D$ = annual demand quantity
- $K$ = fixed cost per order
- $h$ = annual holding cost per unit

...but we should make some changes to this. I can just have a maximum order quantity so that we don't really need $h$. I also need to ask my Dad if there's a fixed shipping cost or if that's variable depending on the size of the order. 

## 7. Optimizing SKU mixture
This seems like the most complex problem to me. We need to determine *which* products to buy in order to maximize our loss function. 