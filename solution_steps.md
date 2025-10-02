## Step-by-Step Recovery Process

1. **Identify the scenario**
   - MFA device tied to ex-employee’s personal phone.
   - Root account and main IAM admin inaccessible.
   - Email associated with MFA also tied to the ex-employee.

2. **Check for alternate IAM users or Roles**
   - In the AWS Console (if accessible) or via CLI:
     ```sh
     aws iam list-users
     aws iam list-roles
     aws iam list-attached-user-policies --user-name AdminUser
     ```

3. **Attempt MFA reset via IAM role**
   - If an active IAM user has sufficient privileges:
     ```sh
     aws iam deactivate-mfa-device --user-name AdminUser --serial-number arn:aws:iam::123456789012:mfa/AdminUser
     aws iam enable-mfa-device --user-name AdminUser --serial-number arn:aws:iam::123456789012:mfa/NewDevice --authentication-code1 123456 --authentication-code2 654321
     ```

4. **Console route attempt**
   - `IAM > Users > Security credentials > Manage MFA device`

5. **If both fail: initiate internal verification**
   - Provide:
     - Company legal docs
     - Domain ownership proof
     - Billing history

6. **Escalation path**
   - If no active IAM admin: internal AWS verification resets MFA.

7. **Post-resolution hardening**
   - Add backup IAM admins.
   - Enforce offboarding policy.
   - Rotate credentials and audit IAM.