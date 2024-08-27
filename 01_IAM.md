# AWS IAM (Identity and Access Management) - Global Service

## Basics
- **Root Account**: Automatically created.
- **Users**: People in your organization; can be in groups.
- **Groups**: Only contain users, not other groups. Users can be in one or more groups.
- **Policies**: Rules in JSON format that give permissions to users or groups.
- **Roles**: Permissions given to services so they can do tasks for you.

## Policy Structure
- **Version**: Specifies the version of the policy language (e.g., 2012-10-17).
- **Id**: Identifier (Optional)
- **Statement**: A list of rules that includes:
  - **Sid**: A unique identifier for individual statements (Optional)
  - **Effect**: What the policy does—`Allow` or `Deny`.
  - **Principal**: Who the policy applies to (e.g., accounts, users, roles).
  - **Action**: What actions are allowed or denied (e.g., `s3:GetObject`, `s3:PutObject`).
  - **Resource**: The resources the policy applies to (e.g., `arn:aws:s3:::mybucket/*`).
  - **Condition**: Specifies when the policy applies (Optional)

### Sample JSON Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "1",
      "Effect": "Allow",
      "Principal": {"AWS": ["arn:aws:iam::123456789012:root"]},
      "Action": ["s3:GetObject", "s3:PutObject"],
      "Resource": ["arn:aws:s3:::mybucket/*"]
    }
  ]
}
```

## MFA Devices
- **Authenticator Apps**: Like Google Authenticator, Microsoft Authenticator, etc.
- **Security Keys**: Like YubiKey or other FIDO keys.
- **Hardware TOTP Tokens**: Physical devices that generate time-based codes.

## Accessing AWS
- **AWS Management Console**: Secured with password + MFA.
- **AWS CLI**: Open source, secured with an access key.
- **AWS SDK**: Supports many platforms (Android, iOS, Python, JS, etc.); AWS CLI is built on the Python SDK.

## Roles
- Give permissions to AWS services (like EC2, Lambda) using IAM Roles.

## IAM Security Tools
- **IAM Credentials Report**: Lists all users and their credential statuses.
- **IAM Access Advisor**: Shows when a user last used a service to help refine permissions.
