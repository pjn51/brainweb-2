# Can I adapt EOQ to be more flexible?
[[EOQ seeks to minimize holding and ordering costs]], but [[EOQ has some assumptions]]. Can I get rid of them somehow?

The basic EOQ formula is as follows.
$$
Q*=\sqrt{\frac{2DK}{h}}
$$
... where $Q*$ is the optimal order quantity, $D$ is the annual demand quantity, $K$ is the fixed cost per order (such as shipping), and $h$ is the annual holding cost per unit. 

However, for the Stashlogix project (see [[How can we manage Stashlogix cash-flow?]]) we don't have a fixed cost per order. Can we accomodate a variable cost, such as a percentage of the order total?

If we set $S$ as shipping cost, expressed as a fraction of the total order price and $P$ as the , we could express EOQ as:
$$
Q*=\sqrt{\frac{2DSP}{h}}
$$

---
#question/stash-o-matic 