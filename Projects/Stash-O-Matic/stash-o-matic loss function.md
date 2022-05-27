# Stash-O-Matic Loss Function
`TAGS:`

---
## Introduction
We want to maintain liquidity, prevent sell-outs, and maximize revenue given those conditions as part of the [[stash-o-matic model]] and ultimately the [[stash-o-matic project]] project. 

## 1. Initial attempt
I guess I could create an equation that we seek to *maximize* when we run the model. I could incorporate sell-outs by modeling them as lost revenue. By finding the profit margin on each product, and seeing how much demand we missed out on by having the product out-of-stock, we could punish the model for not having enough of a popular item.

$$
w_lL+w_rR-w_mM
$$

- $w_l$ = importance of maintaining liquidity (between 0 and 1)
- $L$ = liquidity, or cash on hand (dollars)
- $w_r$ = importance of maximizing revenue (between 0 and 1)
- $R$ = revenue (dollars)
- $w_m$ = importance of minimizing revenue lost due to sell-out (between 0 and 1)
- $M$ = missed revenue (dollars)

This model would just try and decrease missed revenue, increase liquidity, and increase revenue. 

## 2. Refining liquidity optimization
I don't just want to increase liquidity to infinity, we want liquidity within a specific range. How can I do that? Maybe take the inverse square of liquidity so that the value peaks at some number and then decreases in value as liquidity gets too high?

If I model the optimal value of liquidity as...

$$
-(L-i)^2+w_l
$$

- $L$ = liquidity, or cash on hand (dollars)
- $i$ = ideal amount of cash on hand (dollars)
- $w_l$ = importance of maintaining this liquidity (between 0 and 1)

This will create a downward-opening parabola that peaks at the value of $i$. If this is confusing, go to [desmos](https://www.desmos.com/calculator/ubkht6qz91) and play around with it. 

So now our overall [[loss function]] is...

$$
w_rR-w_mM-[(L-i)^2+w_l]
$$

- $w_l$ = importance of maintaining liquidity (between 0 and 1)
- $L$ = liquidity, or cash on hand (dollars)
- $i$ = ideal amount of cash on hand (dollars)
- $w_r$ = importance of maximizing revenue (between 0 and 1)
- $R$ = revenue (dollars)
- $w_m$ = importance of minimizing revenue lost due to sell-out (between 0 and 1)
- $M$ = missed revenue (dollars)