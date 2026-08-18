# AWS Cost Analysis - August 18, 2026

## Executive Summary

- **Total Spend (Last Month):** 
$0.00 billed — all usage is currently absorbed by AWS free-tier credits (~$80 remaining)

- **Change vs Previous Month:** 
No meaningful $ change (still $0 billed), but EC2-Other and Data Transfer usage are trending upward month-over-month

- **Top 3 Services (by usage/cost driver):** 
EC2-Other, Data Transfer, S3

- **Forecast Next Month:**
 $9.53 (80% confidence range: $3.78 – $15.28)

## Key Findings

1. Even though billed spend is $0.00 (covered by free-tier credits), EC2-Other and Data Transfer are the two fastest-growing cost drivers, with S3 as the third-largest, based on the 6-month service breakdown (Feb–Aug 2026).
2. Within EC2, `t3.micro` is the most expensive instance type, and daily costs generally drop on weekends. Except for one project weekend where costs stayed elevated due to working through Saturday and Sunday.
3. The 3-month forecast shows costs rising from $9.53 (September) with an uncertainty range that widens over time (up to $0.06–$19.07 by November), but this stays comfortably within the ~$80 of remaining credits.
4. Data transfer costs are real but small: $0.2036 in July (driven ~84% by NAT Gateway data processing) and $0.0416 so far in August, consistently under 1% of total AWS costs. well below the 10% threshold that would flag it for optimization.

## Optimization Opportunities

1. **Activate cost allocation tags now, before credits run out.** 
Tag-based allocation (Environment/Owner) currently returns no data because tags were never activated/applied. Setting this up early avoids losing historical visibility once real billing starts.

2. **Watch NAT Gateway usage as the account scales.**
 NAT Gateway data processing already accounts for ~84% of data transfer costs in July; this is the most likely line item to grow disproportionately once free-tier credits are exhausted.

## Screenshots

- See `forecast-screenshot.png`
- See `service-breakdown-screenshot.png`

---

## 1. Monthly Spending by Service (Last 6 Months: Feb–Aug 2026)

A complete breakdown of AWS costs from the past 6 months, monthly granularity, grouped by service.

**Q: What are your top 3 services by cost?**
A: As of now, because I'm using the free tier, all of my expenses are deducted from the free credits given. But per the chart, my top 3 are:
1. EC2-Other
2. Data Transfer
3. S3

**Q: Which service has grown the most month-over-month?**
A: EC2-Other and Data Transfer.

**Q: Are there any unusual spikes?**
A: None.

## 2. Daily EC2 Costs (Last 30 Days)

A daily breakdown of the past month, filtered to EC2 instances, daily granularity, grouped by instance type.

**Q: Which instance types cost the most?**
A: `t3.micro`.

**Q: Are there weekend patterns (costs drop on weekends)?**
A: Most weekends had lower costs, except one project weekend where I worked through Saturday/Sunday to finish it, so costs stayed elevated that weekend.

**Q: Any unusual daily spikes?**
A: None.

## 3. Tag-Based Cost Allocation

**Q: Which environment (prod/dev/staging) costs the most?**
A: Not able to determine — I haven't activated/used cost allocation tags up to this point, so no data is available for this view.

## 4. Cost Forecast (Next 3 Months)

Forecasted cost for the upcoming 3 months.

**Q: What is the forecasted cost for next month?**
A: $9.53

**Q: Is it within your budget?**
A: Yes — available credits are still over $80.

**Q: What is the uncertainty range?**
A:
- September: $3.78 – $15.28
- October: $1.80 – $17.84
- November: $0.06 – $19.07

## 5. Data Transfer Costs (Last 3 Months)

This month's (August 2026) data transfer breakdown.

**Q: Which services have high data transfer?**
A: EC2-Other — $0.04

**Q: Is data transfer growing?**
A: July 2026 was the first month with measurable data transfer costs at $0.2036, driven primarily by:
- NAT Gateway data processing (~84% of costs, $0.1721)
- Regional data transfer (~15% of costs, $0.0315)

August 2026 is still in progress (through Aug 18) with $0.0416 so far — entirely from NAT Gateway charges.

**Q: Does data transfer represent more than 10% of the costs?**
A: No. My data transfer costs do not represent more than 10% of total AWS costs — they're well under 1% of total spend in both July and August 2026.

## 6. learning reflection 

What was your biggest cost surprise? 
It was realizing how easily stray resources get left behind. After finishing a lab or project, EC2 instances and S3 buckets I forgot to stop or delete kept accumulating cost in the background. 
NAT Gateway was the second surprise: even without touching it directly, ~84% of my data transfer bill in July came from NAT Gateway data processing alone.

Which report would be most useful for your team? 
For engineering, the daily EC2 cost view grouped by instance type would be the most useful. It makes it easy to spot instance types that shouldn't still be running.

How would you explain the forecast to non-technical stakeholders? 
I'd compare it to a phone or utility bill: there's a baseline charge you pay just to keep the line active. In AWS that's infrastructure like NAT Gateway or minimum storage that runs regardless of how busy you are and then there are usage charges that scale with how much you actually use, like compute hours and data transferred. The forecast is really just projecting how much of that "usage" portion is likely to grow based on the last few months, with a range attached because AWS can't know exactly how much you'll use next month. 
The key point for stakeholders: the baseline part is mostly fixed and hard to shrink, but the usage part especially unused instances left running is the lever we actually control, and that's where optimization happens.

What optimization opportunities did you identify?
 At this stage, the clearest opportunity is enabling cost allocation tags. Right now, without tags, there's no way to tell which instances or buckets belong to an active project versus which ones are leftovers from a finished lab. 
 Tagging by Owner or Environment would make it easy to spot and clean up those stray resources before they add real cost once the free-tier credits run out.