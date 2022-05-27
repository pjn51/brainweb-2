# How can we manage Stashlogix POs?
When we're trying to automate this process, there are a few key parameters:
1. Cash on hand. We cannot place a PO that we cannot pay for.
2. Optimal order quantity. [[EOQ seeks to minimize holding and ordering costs]], so we could consider incorporating that. 
3. Optimal order frequency. Stashlogix can't handle placing orders daily, for instance. 
4. Demand projections. We have to know what the demand for products will be.

We need one PO per supplier. 

I think that we should determine a maximum order frequency so that we aren't placing orders each day. Let's say that is monthly. We just schedule a refill date based on the most at-risk product, and include every product that's going to hit the specified minimum quantity in the following month, making sure to include a quantity that will suffice until the next order. 

---
#question/stash-o-matic 