# Auto Scaling Group Project

## Overview
Demonstrated the self-healing and dynamic scaling capabilities 
of AWS EC2 Auto Scaling Groups by manually terminating instances 
and adjusting desired capacity — proving ASG automatically 
maintains availability without human intervention.

## Architecture
Launch Template
↓
Auto Scaling Group (min: 2, max: 6)
↓
EC2 Instances (t3.micro) across multiple AZs
↓
CloudWatch (monitoring instance health)

## Services Used
- Amazon EC2
- EC2 Auto Scaling Groups
- Launch Templates
- Amazon CloudWatch
- AWS VPC & Subnets

## Objectives Completed

| Objective | Status |
|---|---|
| Create Launch Template | ✅ |
| Create ASG with minimum 2, maximum 6 instances | ✅ |
| Terminate one instance manually | ✅ |
| Verify ASG self-healed automatically | ✅ |
| Increase desired capacity to 4 instances | ✅ |
| Delete all resources after completion | ✅ |

## Steps Followed

### 1. Created Launch Template
- AMI: Amazon Linux 2023
- Instance type: t3.micro (Free Tier eligible)
- User data script to install and start Apache web server
- Security group with ports 22 and 80 open

### 2. Created Auto Scaling Group
- Name: my-asg-project
- Minimum capacity: 2
- Desired capacity: 2
- Maximum capacity: 6
- Deployed across 3 Availability Zones in ap-south-1

### 3. Verified Initial Launch
- ASG automatically launched 2 EC2 instances on creation
- Both instances passed status checks and entered Running state

### 4. Terminated One Instance Manually
- Manually terminated one running instance via EC2 console
- ASG detected instance count dropped below minimum
- ASG automatically launched replacement within 2 minutes
- Proved self-healing behavior of Auto Scaling Groups

### 5. Increased Desired Capacity to 4
- Edited ASG desired capacity from 2 to 4
- ASG launched 2 additional instances automatically
- All 4 instances confirmed Running with status checks passed

### 6. Cleaned Up All Resources
- Deleted ASG (automatically terminated all instances)
- Deleted Launch Template


### 7. Screenshots
<img width="944" height="396" alt="ec2-replacement" src="https://github.com/user-attachments/assets/b7767a35-b1ab-4d1c-a245-c8ca89a443f9" />
<img width="953" height="413" alt="asg-1" src="https://github.com/user-attachments/assets/7e389038-62e3-44b4-92d1-9ada99553af0" />
<img width="937" height="399" alt="asg-2" src="https://github.com/user-attachments/assets/14f94397-298a-4567-9756-c8583609487d" />
<img width="944" height="403" alt="asg-activity" src="https://github.com/user-attachments/assets/c53bb973-abb6-4fb1-97ce-00e263f5f32e" />
<img width="941" height="402" alt="asg-ec2-regen" src="https://github.com/user-attachments/assets/63bb91b6-0005-4814-8c74-1c63749b1255" />

## Key Results

| Action | Outcome |
|---|---|
| Instance manually terminated | ASG replaced it in ~2 minutes |
| Desired capacity increased to 4 | 2 new instances launched automatically |
| All instances | Passed 3/3 status checks |


## Key Learnings
- AWS retired Launch Configurations after May 2023 for new 
  accounts — Launch Templates are the modern equivalent
- ASG always maintains minimum capacity — self-healing is automatic
- Desired capacity can be changed anytime without downtime
- ASG Activity tab provides full audit trail of every scaling event
- Deleting ASG first automatically terminates all instances inside it

