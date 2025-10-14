# AWS Security and Optimization Tools

## AWS Trusted Advisor

**When to use (Application Level):**
- **Cost Optimization**: When you want to identify unused or underutilized resources that are costing money unnecessarily
- **Performance**: When your applications are running slowly and you need recommendations for improving performance
- **Security**: When you need to ensure your AWS resources follow security best practices
- **Fault Tolerance**: When you want to improve the reliability and availability of your infrastructure
- **Service Limits**: When you're approaching AWS service limits and need to plan for scaling

**Key features:**
- Provides real-time guidance to help provision resources following AWS best practices
- Offers 7 core checks for all customers (cost optimization, security, performance, fault tolerance)
- Premium support customers get access to additional checks
- Continuously monitors your environment and provides actionable recommendations
- **Focus**: Application-level optimization and best practices

## AWS GuardDuty

**When to use (AWS Resource Level):**
- **Threat Detection**: When you need continuous monitoring for malicious activity and unauthorized behavior
- **Security Monitoring**: When you want to detect threats like compromised EC2 instances, S3 buckets, or AWS accounts
- **Incident Response**: When you need detailed findings and remediation steps for security incidents
- **Compliance**: When you need to meet security compliance requirements with automated threat detection
- **Multi-Account Security**: When managing multiple AWS accounts and need centralized threat detection

**Key features:**
- Uses machine learning, anomaly detection, and integrated threat intelligence
- Monitors VPC Flow Logs, DNS logs, and CloudTrail event logs
- Detects threats like cryptocurrency mining, data exfiltration, and unauthorized API calls
- Provides detailed findings with severity levels and recommended remediation steps
- Integrates with other AWS services like CloudWatch Events and Lambda for automated responses
- **Focus**: AWS resource-level security monitoring and threat detection

## Amazon Inspector

**When to use (Application Vulnerability Assessment):**
- **Vulnerability Assessment**: When you need to assess applications for vulnerabilities and deviations from best practices
- **Compliance Requirements**: When you need to meet compliance standards that require regular vulnerability assessments
- **Security Hardening**: When you want to identify and fix security issues in your applications before deployment
- **Continuous Security**: When you need ongoing security assessment of your applications running on EC2 instances
- **Container Security**: When you need to assess container images for vulnerabilities before deployment

**Key features:**
- Automatically assesses applications for exposure, vulnerabilities, and deviations from best practices
- Provides detailed findings with severity levels and remediation recommendations
- Supports both EC2 instances and container images (ECR)
- Uses AWS knowledge base of security research and best practices
- Integrates with AWS Security Hub for centralized security findings
- Can be scheduled to run assessments automatically
- Provides risk scores and detailed reports for compliance documentation
- **Focus**: Application-level vulnerability assessment and security compliance
 