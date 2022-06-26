# Stash-o-Matic Database
`TAGS:`

---
## Quick links
(All in [[command line]])
- Root user using [[SSH]]
	- `ssh -t root@64.225.115.43`
	- pw: `h.xC42e_7G`
- PJN
	- `ssh pjn@64.225.115.43`
	- pw: old style, no letters though. Just the numbers. 
- Get from server to logs: `pm2 logs`
- Restart server: `pm2 restart app.js --no-daemon`

## Introduction
We need to determine what info we need, and how we can collect that information and store it. The raw QuickBooks information is in a [[MongoDB]] structure, but a lot of calculations have been done on the stashomatic website. 

I can use [[PyMongo]] to get the data into [[Python]]. 

## 1. Collection prefixes
`dear` prefix indicates that this is sourced from the DEAR inventory management system. 

`param` prefix indicates that this is an assumption about the future. This includes sales figures. 

## 2. MongoDB Collections
- `param_channel_items `= has item IDs, baseline sales numbers per day (estimated), also has item defaults which override channel defaults (such as discount).
- `param_channels` = has default discount and default growth. Growth is just the educated guess at future sales growth. It acts as a modifier to current sales levels on a daily basis. 
- `param_events` = events are associated with a calendar. These include discount events like holidays, or growth.
- `param_expenses` = assumed non-inventory expenses. 
- `bundles` = refers to bundled items, such as jars that have three components. 
- `dear_purchases` = inventory purchases from DEAR.
- `param_financings` = nearly the same as expenses, but has loans and investments.
- `param_pos` = assumed purchase orders in the future. Not being used right now. 
- `param_valid_items` = this is a way of saying that for each channel, which products are available to be sold. This saves time parsing through all products for calculation.
- `param_warehouses` = not used
- `projectionparams` = not used
- `qbo_ars` = quickbooks online ARs. Account recieveable records, meaning records of money owed to Stashlogix. Sales that haven't been paid yet. Sales can take a few weeks if it was through Amazon. 

## 3. Limitations to historical data
- Out of stock events
- Whenever products are in stock they sell out fast

## 4. Data structure for projection_inputs collection
SKUs are found at products -> 0,1,2,3,etc... -> sku.

Locations are found within the numbered objects, in a locations field that has a numbered list within it. 