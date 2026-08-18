## AWS Cost Analysis - README

# Analysis Process
1. Enabled Cost Explorer in AWS Billing Dashboard.
2. Built monthly report, last 6 months, grouped by service → identified top 3 cost drivers.
3. Built daily report, last 30 days, filtered to EC2, grouped by instance type → checked cost trends and weekend patterns.
4. Checked tag-based allocation → no data, cost allocation tags not activated.
5. Generated 3-month forecast → next month's cost + 80% confidence range.
6. Built report filtered to Data Transfer usage, last 3 months, grouped by service → checked growth and % of total cost.
7. Saved 2 reports: "Monthly Spend by Service" and "Daily EC2 Costs".
8. Documented findings, executive summary, and reflection in cost-analysis.md.


# Files
cost-analysis.md — full analysis, findings, forecast, reflection
forecast-screenshot.png — cost forecast screenshot
service-breakdown-screenshot.png — top services screenshot
README.md — this file