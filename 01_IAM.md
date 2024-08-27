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
- **Authenticator Apps**: Examples include Google Authenticator, Microsoft Authenticator, Twilio Authy, Duo Mobile, Symantec VIP, LastPass Authenticator.
- **Security Keys**: Physical devices like YubiKey or other FIDO-compliant security keys.
- **Hardware TOTP Tokens**: Physical devices that generate time-based one-time passwords (TOTP).


## Accessing AWS
- **AWS Management Console**: Web-based interface secured with a password and MFA. Supports CloudShell for terminal access.
- **AWS CLI**: Command-line tool, secured with an access key. [GitHub repository](https://github.com/aws/aws-cli).
- **AWS SDK**: Software Development Kit supporting various platforms (e.g., Android, iOS, Python, JavaScript). The AWS CLI is built using the Python SDK.

## Roles
- **IAM Roles**: Assign permissions to AWS services (e.g., EC2, Lambda) to perform actions on your behalf.

## IAM Security Tools
- **IAM Credentials Report**: Generates a report of all users in your account and their credential statuses.
- **IAM Access Advisor**: Shows the last accessed times for services granted to a user, helping refine permissions to enforce the principle of least privilege.
