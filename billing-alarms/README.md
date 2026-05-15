# AWS Billing Alarms Project

## Overview
Created three CloudWatch billing alarms in AWS to monitor 
estimated charges and trigger SNS email notifications at 
multiple spend thresholds.

## Services Used
- AWS CloudWatch
- Amazon SNS
- AWS Billing and Cost Management

## Alarms Created

| Alarm Name | Threshold | Action |
|---|---|---|
| billing-alarm-new | $5 USD | SNS Email |
| 25USD_bill_alarm | $25 USD | SNS Email |
| 100USD_billing_alarm | $100 USD | SNS Email |

## Steps Followed
1. Enabled CloudWatch billing alerts in Billing Preferences
2. Switched to us-east-1 (billing metrics only available here)
3. Created SNS topic with email subscription
4. Created three CloudWatch alarms on EstimatedCharges metric
5. Verified alarms appear in CloudWatch console

## Screenshots
![Billing Alarms](<img width="955" height="406" alt="aws-billing-25" src="https://github.com/user-attachments/assets/935fbf94-7c9c-4a42-8e81-c3974ef8b44b" />
.png)
![Billing Alarms](<img width="951" height="419" alt="aws-bill-5" src="https://github.com/user-attachments/assets/b526c231-7a69-4bbe-98fd-23d69664fefa" />
)
## Key Learnings
- Billing metrics in CloudWatch only available in us-east-1
- SNS must be confirmed via email before alarms can notify
- Insufficient Data state is normal until threshold is crossed
