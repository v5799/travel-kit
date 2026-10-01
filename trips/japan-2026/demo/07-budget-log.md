# 07 budget-log (DRY RUN: budget.csv NOT written)
**Asked:** Show how three sample meals would be logged. Amounts below are made-up SAMPLES, not real spending.
Header: `date,category,item,amount_jpy,paid_by,notes`
```
2026-10-15,meal,Maruhana king crab dinner (SAMPLE amount),21000,Varun,3 guests; sample figure; verify against receipt
2026-10-20,meal,Unagi lunch Mejiro Zorome (SAMPLE amount),8700,Varun,3 guests at 2,900; sample
2026-10-22,meal,Sushi Ogawa uni bowl (SAMPLE amount),1500,Varun,1 guest; sample
```
Per-category summary shape: meal total 31,200 (sample); per person: Varun-paid 31,200, split TBD. Currency: JPY only; no conversion without stated rate/date.
**What it could not do:** no real receipts; who owes whom is OPEN (paid_by and split rules not stated); budget.csv untouched.
