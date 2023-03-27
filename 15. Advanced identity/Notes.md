## AWS STS (Security Token Service)
* Enables you to create temporary, limited privileges credentials to access your AWS resources
* Short-term credentials: you configure expiration period
* Use cases
1. Identity federation: manage user identities in external systems, and provide them with STS tokens to access AWS resources
2. IAM roles for cross/ same account access
3. AM roles for Amazon EC2: provide temporary credentials for EC2 instances to access AWS resources

## AWS Cognito
* Provide identity for Web and Mobile application users (potentially millions)
* Instead of creating an IAM user, you create a user in Cognito
* Mobile and Web applications will login to AWS Cognito which interfaces with database of users, can log in with social identity provider such as Facebook, Google or Twitter too

## Microsoft Active Directory
* Found on any Windows Server with AD Domain services
* Database of objects: User Accounts, Computers, Printers, File Shares, Security Groups
* Centralized security management, create account, assign permissions
* Can log into any laptop within a network through the domain controller
* AWS Directory Services
1. AWS Managed Microsoft AD
* Create your own AD in AWS, manage users locally, supports MFA
* Establish "trust" connections with your on-premise AD
2. AD Connector
* Director Gateway (proxy) to redirect to on-premise AD, supports MFA
* Users are managed on the on-premise AD
3. Simple AD 
* AD-compatible managed directory on AWS
* Cannot be joined with on-premise AD

## AWS IAM Identity Center (successor to AWS Single Sign-on)
* One login (Single Sign on SSO) for all your AWS accounts in AWS organizations to access different AWS features for particular accounts
* One login for business cloud applications (Salesforce, Box, MS 365)
* One login for SAML2.0-enabled applications
* One login for EC2 windows instances
* Identity provider (where it's stored):
1. Built-in identity store in IAM Identity Center
2. Third party: Active directory (AD), OneLogin, Okta

## Summary
* IAM -> Identity and Access management inside your AWS account, for creating users that you trust and belong to your company
* Organizations -> Manage multiple AWS accounts by applying service control policies to create organizational units
* Single Token Service (STS) -> Temporary, limited-privileges credentials to access AWS resources
* Cognito -> create a database of users for mobile and web applications
* Directory Services -> Integrate Microsoft Active Directory in AWS
* IAM identity Center -> One login for multiple AWS accounts and applications