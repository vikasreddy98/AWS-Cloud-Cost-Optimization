
# Troubleshooting

## Issue 1

### Error

Task timed out after 3.00 seconds

### Root Cause

Default Lambda timeout was insufficient for snapshot analysis.

### Resolution

Increased timeout from 3 seconds to 10 seconds.

## Issue 2

### Error

UnauthorizedOperation when calling DescribeInstances

### Root Cause

IAM role lacked EC2 read permissions.

### Resolution

Added:

- ec2:DescribeInstances
- ec2:DescribeVolumes

to the Lambda execution role.

---

## Issue 3

### Potential Issue

Snapshot not deleted.

### Root Cause

Snapshot still associated with an active EC2 instance.

### Resolution

Terminate the instance and rerun the Lambda function.
