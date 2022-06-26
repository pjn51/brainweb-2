# Economic Order Quantity
`LINKS`: [wiki](https://en.wikipedia.org/wiki/Economic_order_quantity)

---
In inventory management, EOQ is the order quantity that minimizes the total holding costs and ordering costs. It is a very old production scheduling models. 

## Model assumptions
The basic model only applies when demand for a product is constant over the year, and each new order is delivered in full when inventory reaches zero. 

It also assumes that there is a fixed cost for each order placed, regardless of the size of the order. 

## Formula
$$
Q^* = \sqrt{\frac{2DK}{h}}
$$

- $Q^*$ = optimal order quantity
- $D$ = annual demand quantity
- $K$ = fixed cost per order
- $h$ = annual holding cost per unit

Once we find $Q*$, we can divide the total number of units needed in a year by $Q*$ to find the number of orders in a year. 

## Example
If we sell 10,000 units a year, with $40 in shipping per order, and a yearly carrying cost of $5 per unit, we can find that the ideal order quantity is 400 units. 

$$
\sqrt{\frac{2 \cdot 10000 \cdot 40 }{5}} = 400
$$