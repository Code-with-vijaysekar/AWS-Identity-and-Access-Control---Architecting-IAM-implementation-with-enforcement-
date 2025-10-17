# AWS-Identity-and-Access-Control---Architecting-IAM-implementation-with-enforcement-
Designed and implemented secure AWS Identity and Access Management (IAM) architecture with role-based access control and compliance enforcement. Includes configuration of enterprise roles and policies, principle of least privilege validation through S3, EC2 and CloudWatch, and automation of compliance using AWS Config and Lambda.
Perfect — here’s a **ready-to-use `README.md` structure** for your GitHub repository titled

Overview:

This project implements and enforces "AWS Identity and Access Management (IAM)" using role-based access control and compliance automation.
The goal was to apply the "principle of least privilege", validate permissions across multiple AWS services, and enforce security compliance using "AWS Config" and "Lambda".

Key Objective:

- Implement IAM roles and policies for enterprise users (Analyst, Developer, Finance).
- Apply and test least privilege access using S3, CloudWatch, EC2, and Billing.
- Enforce compliance through a custom AWS Config rule and Lambda function.
- Design a visualization of IAM roles, policies, and permissions.

Roles and Policies Implemented:

| Role                          | Attached Policies                                           | Purpose                                                   |
| ----------------------------- | ----------------------------------------------------------- | ------------------------------------------
|   enterprise-analyst-role     | enterprise-analyst-policy, enterprise-restrictions-policy   | Read-only access to analytics data and    limited uploads                 |
|   enterprise-developer-role   | enterprise-developer-policy, enterprise-restrictions-policy | Developer-level access to legacy S3 bucket and CloudWatch |
|   enterprise-finance-role     | enterprise-finance-policy, enterprise-restrictions-policy   | Billing and Cost Explorer access for finance operations              |

S3 Access Validation:

1. Created and uploaded the following files for testing:

   * `non_obfuscated.txt`
   * `obfuscated.txt`
   * `analyst.txt`
   * `developer.txt`
2. Tagged objects appropriately:

   * `Stage: NonObfuscatedReport`
   * `Stage: ObfuscatedReportReady`
   * `Role: analyst`
   * `Role: developer`
3. Verified access and restrictions for each IAM role.

Testing Performed:

- Enterprise Analyst Role:

  * Access denied for `non_obfuscated.txt`
  * Successful download of `obfuscated.txt`
  * Uploaded `analyst.txt` to legacy bucket

- Enterprise Developer Role:

  * Uploaded and downloaded `developer.txt` successfully
  * Accessed CloudWatch Metrics and EC2 Security Groups

- Enterprise Finance Role:

  * Accessed Billing → Cost Explorer Dashboard

Compliance Enforcement:

* Updated the `config-rule-enforcement` Lambda function to restrict access to:
  `arn:aws:s3:::super-secret-bucket`
* Re-evaluated the "ConfigRulePolicyEnforcement" rule.
* Verified that the `bad-policy-that-breaks-enterprise-restrictions` was marked "non-compliant".

Deliverables:

- Screenshots of:

  * S3 access attempts
  * Upload/download tests
  * CloudWatch and EC2 access
  * Cost Explorer dashboard
  * Lambda code update
  * Config rule evaluation
* Organizational visualization diagram (draw.io)

Technologies Used:


* AWS S3 – Object-level access testing
* draw.io – IAM architecture visualization
* AWS IAM – Role-based access and policy creation
* AWS Lambda – Automated compliance enforcement
* AWS Config – Continuous monitoring of policy compliance
* AWS CloudWatch – Metrics and resource visibility validation
* AWS EC2 – Security Group access validation and resource visibility testing
* AWS Billing & Cost Explorer – Financial dashboard access validation for enterprise finance role


Visualization:

Final IAM role and policy visualization designed in "draw.io", mapping:

* Roles → Policies → Resources
* Permissions → Compliance checks



