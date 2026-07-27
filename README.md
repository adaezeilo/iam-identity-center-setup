# iam-identity-center-setup
## AWS IAM Identity Center Setup — SSO Access Management
Overview

This project demonstrates setting up AWS IAM Identity Center (formerly AWS SSO) to manage user access to AWS accounts through a centralized identity provider, rather than relying on individual IAM users per account.

# Why This Matters

Managing individual IAM users across multiple AWS accounts doesn't scale and creates security risk credentials get duplicated, offboarding becomes error prone, and there's no single place to enforce access policy. AWS recommends IAM Identity Center as the standard approach for managing human access at scale:

Centralized identity: one set of credentials per person, not one per account
Least privilege by design: access is granted through reusable permission sets, not ad-hoc IAM policies
Easier offboarding: disable one identity instead of hunting through every account
Foundational for landing zones: this is the access layer that sits on top of a multi account AWS Organization structure
# What I Built
Enabled IAM Identity Center at the AWS Organizations level
Created a test user (test-devops-user) to simulate a real employee onboarding
Built a custom permission set (TestReadOnlyAccess) based on the ReadOnlyAccess predefined policy — demonstrating least-privilege thinking even in a test setup
Assigned the test user to an AWS account using that permission set
Verified the full SSO flow by logging in through the AWS access portal as the test user
## Steps and Evidence
# Step 1: Enable IAM Identity Center

Enabled the service at the organization level, which automatically creates an AWS Organization if one doesn't already exist.

Show Image

# Step 2: Create a Test User

Created a test identity to represent a new hire being onboarded.

Show Image

# Step 3: Create a Permission Set

Built a permission set defining exactly what the test user can do once assigned — in this case, read-only access, to keep the test safe and demonstrate least-privilege principles.

Show Image

# Step 4: Assign User to Account

Linked the test user to a specific AWS account using the permission set — this is the step that actually grants access.

Show Image

# Step 5: Verify End-to-End

Logged in as the test user through the AWS access portal to confirm the SSO flow works — from identity to permission set to account access.

Show Image

# Key Takeaway

This setup shows the difference between granting access (IAM policies/permission sets) and managing identity (IAM Identity Center)  two separate concerns that AWS deliberately keeps decoupled. Understanding this distinction is foundational for designing secure, scalable AWS environments.

Related Projects
IAM Least Privilege Walkthrough  a deeper dive into writing custom least-privilege IAM policies, which pairs naturally with the permission sets configured here
AWS Security Compliance Remediation  broader account hardening practices
