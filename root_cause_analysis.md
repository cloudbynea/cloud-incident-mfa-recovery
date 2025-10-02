## Root Cause Analysis (RCA)

The issue was caused by improper credential lifecycle management:
- MFA was configured on a personal device rather than a corporate-controlled authenticator.
- No backup IAM administrators or roles were in place.
- The organization lacked a documented offboarding process for IT staff.

This led to a critical access lockout when the IT employee left the company.