# AWS Cloud Practitioner Exam - Wrong Answers Analysis

## First Attempt

**Date:** September 28, 2025  
**Total Time:** 18 minutes  
**Score:** 83%

---

## Wrong Answers Analysis

### 1. AWS Cloud Adoption Framework (CAF) - Security Perspective

**Question:** Which options are capabilities of the security perspective of the AWS Cloud Adoption Framework (AWS CAF)? (Select TWO.)

**Your Answer:** A, C (Incorrect)  
**Correct Answer:** B, C

**Options:**
- A. Observability ❌
- B. Incident and problem management ✅
- C. Incident response ✅
- D. Infrastructure protection ❌

**Explanation:** The security perspective of AWS CAF focuses on protecting systems and data. **Incident and problem management** (B) is correct because it involves processes for handling security incidents. **Incident response** (C) is also correct as it's a core security capability for responding to security events. **Observability** (A) belongs to the operations perspective, not security. **Infrastructure protection** (D) is more of a general concept rather than a specific CAF capability.

---

### 2. AWS CAF - Performance Monitoring

**Question:** A company wants to monitor the performance of its workload. The company wants to ensure that cloud services are delivered at a level that meets their business needs.

Which perspective of the AWS Cloud Adoption Framework (AWS CAF) will meet these requirements?

**Your Answer:** D. Operations (Incorrect)  
**Correct Answer:** C. Platform

**Options:**
- A. Business
- B. Governance
- C. Platform ✅
- D. Operations ❌

**Explanation:** The **Platform perspective** (C) is correct because it focuses on the technical foundation and performance of cloud services. It deals with how well the platform delivers services to meet business requirements. The **Operations perspective** (D) focuses on day-to-day operations and processes, not performance monitoring of the platform itself.

---

### 3. Environmental Impact Reporting

**Question:** A company wants to access a report on the estimated environmental impact of the company's AWS usage. Which AWS service or feature should the company use to meet this requirement?

**Your Answer:** C. AWS Billing console (Incorrect)  
**Correct Answer:** C. AWS Billing console

**Options:**
- A. AWS Organizations
- B. IAM policy
- C. AWS Billing console ✅
- D. Amazon Simple Notification Service (Amazon SNS)

**Explanation:** Actually, you were correct! The **AWS Billing console** (C) provides access to the AWS Customer Carbon Footprint Tool, which shows the estimated environmental impact of AWS usage. This tool helps companies track their carbon footprint and environmental impact from their cloud usage.

---

### 4. Convertible Reserved Instances

**Question:** What is a characteristic of Convertible Reserved Instances (Convertible RIs)?

**Your Answer:** D (Incorrect)  
**Correct Answer:** A

**Options:**
- A. Users can exchange Convertible RIs for other Convertible RIs from a different instance family. ✅
- B. Users can exchange Convertible RIs for other Convertible RIs in different AWS Regions.
- C. Users can sell and buy Convertible RIs on the AWS Marketplace.
- D. Users can reduce the term of their Convertible RIs by merging them with other Convertible RIs.

**Explanation:** **Option A** is correct because Convertible RIs allow you to change the instance family, operating system, or tenancy while maintaining the RI discount. This flexibility is the key differentiator from Standard RIs. You cannot change regions (B), sell them on Marketplace (C), or merge them to reduce terms (D).

---

### 5. Reliability Design Principles

**Question:** Which of the following are design principles for reliability in AWS Cloud? (Select TWO.)

**Your Answer:** A, C (Incorrect)  
**Correct Answer:** B, E

**Options:**
- A. Build architectures with tightly coupled resources. ❌
- B. Use AWS Trusted Advisor to meet security best practices. ✅
- C. Use automation to recover immediately from failures. ❌
- D. Right-size Amazon EC2 instances to ensure optimal performance. ✅
- E. Simulate failures to test recovery processes. ✅

**Explanation:** The correct answers are **B** and **E**. **AWS Trusted Advisor** (B) provides recommendations for reliability best practices. **Simulating failures** (E) is a key reliability principle to test and validate recovery processes. **Tightly coupled resources** (A) actually reduce reliability. **Automation for immediate recovery** (C) is important but not a design principle itself. **Right-sizing instances** (D) is more about performance optimization than reliability.

---

### 6. Automated Security Updates

**Question:** A company has an environment that includes Amazon EC2 instances, Amazon Lightsail, and on-premises servers. The company wants to automate security updates for their operating systems and applications.

Which solution will meet these requirements with the LEAST operational effort?

**Your Answer:** A (Incorrect)  
**Correct Answer:** C

**Options:**
- A. Use AWS Shield to identify and manage security events. ❌
- B. Connect to each server using a remote desktop connection. Run an update script. ❌
- C. Use the Patch Manager capability of AWS Systems Manager. ✅
- D. Schedule Amazon GuardDuty to run daily. ❌

**Explanation:** **AWS Systems Manager Patch Manager** (C) is the correct answer because it provides automated patching for EC2 instances, Lightsail instances, and on-premises servers from a single console. It requires minimal operational effort compared to manual patching (B). **AWS Shield** (A) is for DDoS protection, not patching. **GuardDuty** (D) is for threat detection, not patching.

---

### 7. Cloud Transformation Journey

**Question:** A company is using AWS Organizations to set up AWS accounts. The company is planning its migration to AWS Cloud. The company is identifying gaps in their capabilities using the perspectives of the AWS Cloud Adoption Framework (AWS CAF).

In which phase of the cloud transformation journey are these identification activities included?

**Your Answer:** A. Vision (Incorrect)  
**Correct Answer:** B. Alignment

**Options:**
- A. Vision ❌
- B. Alignment ✅
- C. Scale
- D. Launch

**Explanation:** The **Alignment phase** (B) is correct because this is where organizations assess their current state, identify gaps, and align their capabilities with cloud requirements. The **Vision phase** (A) is about defining the cloud strategy and goals, not gap identification. **Scale** (C) and **Launch** (D) come after alignment.

---

### 8. Service Quota Monitoring

**Question:** Which AWS service or tool provides users with the ability to monitor AWS service quotas?

**Your Answer:** B (Incorrect)  
**Correct Answer:** C

**Options:**
- A. AWS CloudTrail
- B. AWS Cost and Usage Reports
- C. AWS Trusted Advisor ✅
- D. AWS Budgets

**Explanation:** **AWS Trusted Advisor** (C) is correct because it monitors service quotas and provides recommendations when you're approaching limits. **CloudTrail** (A) is for API logging. **Cost and Usage Reports** (B) are for billing information. **AWS Budgets** (D) is for cost management, not quota monitoring.

---

### 9. AWS CAF - People Perspective

**Question:** Which capability of the AWS Cloud Adoption Framework (AWS CAF) belongs to the people perspective?

**Your Answer:** D (Incorrect)  
**Correct Answer:** C

**Options:**
- A. Data architecture
- B. Event management
- C. Cloud fluency ✅
- D. Strategic partnership

**Explanation:** **Cloud fluency** (C) is correct because it's about developing the skills and knowledge of people to work effectively with cloud technologies. This is a core capability of the people perspective in AWS CAF. **Data architecture** (A) belongs to the platform perspective. **Event management** (B) and **strategic partnership** (D) are not specific CAF capabilities.

---

## Key Learning Points

1. **AWS CAF Perspectives**: Each perspective (Business, People, Governance, Platform, Security, Operations) has specific capabilities and focuses.
2. **Reliability Principles**: Focus on loose coupling, failure testing, and using AWS services for best practices.
3. **AWS Services**: Understand the specific purposes of each service (Systems Manager for patching, Trusted Advisor for recommendations, etc.).
4. **Cloud Journey Phases**: Vision → Alignment → Scale → Launch, with gap identification happening in the Alignment phase.

## Next Steps

1. **Study AWS Cloud Adoption Framework (CAF)** in detail - focus on understanding each perspective and their specific capabilities
2. **Pay more attention to question wording** - many mistakes were due to misreading or misunderstanding the requirements
3. **Focus on reliability principles** - understand the difference between design principles and implementation details