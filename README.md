# AWS CCP Interactive & Dense Study Guide

## 🚀 Final Review Checklist
- [ ] I can explain the 6 advantages of cloud computing.
- [ ] I know the difference between IaaS, PaaS, and SaaS.
- [ ] I can draw the Shared Responsibility Model (AWS vs. Customer).
- [ ] I know the difference between a User, Group, and Role in IAM.
- [ ] I can name at least 3 S3 storage classes and their use cases.
- [ ] I can explain the 4 main EC2 pricing models (On-Demand, RI, Spot, Dedicated).
- [ ] I know when to use RDS vs. DynamoDB.
- [ ] I can explain what a VPC, Subnet, and Security Group are.
- [ ] I know the purpose of CloudWatch vs. CloudTrail.
- [ ] I can name the 4 AWS Support Plan tiers.

---

## 🧠 Domain 1: Cloud Concepts (26%)

### ⚡ Quick-Fire Q&A

> **Q: What are the 6 advantages of cloud?**
**A:**
1.  **Variable Expense:** Trade CapEx for OpEx.
2.  **Economies of Scale:** Benefit from AWS's scale.
3.  **Stop Guessing Capacity:** Scale on demand.
4.  **Speed & Agility:** Deploy in minutes.
5.  **Stop Maintaining Data Centers:** Focus on your product.
6.  **Go Global in Minutes:** Deploy across regions easily.

> **Q: What are the 3 cloud deployment models?**
**A:**
1.  **Public Cloud:** (e.g., AWS)
2.  **Private Cloud:** (On-premises)
3.  **Hybrid Cloud:** (Mix of both)

### 📊 IaaS vs. PaaS vs. SaaS Comparison

| Category | IaaS (Infrastructure) | PaaS (Platform) | SaaS (Software) |
| :--- | :--- | :--- | :--- |
| **Analogy** | Renting land | Renting a workshop | Renting a furnished house |
| **You Manage** | OS, Middleware, App, Data | App, Data | Nothing (just use it) |
| **AWS Manages** | Hardware, Networking, Virtualization | OS, Middleware, Runtime... | Everything |
| **Example** | **EC2**, VPC, EBS | **Elastic Beanstalk**, Lambda | WorkSpaces, WorkMail |

---

## 🛡️ Domain 2: Security & Compliance (25%)

### 🤝 Shared Responsibility Model

| Responsibility | AWS (Security **OF** the Cloud) | YOU (Security **IN** the Cloud) |
| :--- | :--- | :--- |
| **Hardware** | ✅ AWS's Job | |
| **Global Infra** | ✅ AWS's Job | |
| **Patching Host OS** | ✅ AWS's Job | |
| **Patching Guest OS** | | ✅ Your Job |
| **Data Encryption** | | ✅ Your Job (Client & Server-side) |
| **IAM** | | ✅ Your Job |
| **Firewall Config** | | ✅ Your Job (Security Groups/NACLs) |

### 🔐 IAM: User vs. Group vs. Role

- **User:** A person or application. Has permanent credentials.
- **Group:** A collection of users. Simplifies permission management.
- **Role:** **Temporary** credentials. Assumed by users or services (like EC2). **BEST PRACTICE** for giving services permissions.

### 🚨 Security Services: Problem ➡️ Solution

> **Problem:** I'm being hit by a DDoS attack.
**Solution:** **AWS Shield** (Standard is free, Advanced is paid).

> **Problem:** I need to filter web traffic (e.g., block SQL injection).
**Solution:** **AWS WAF** (Web Application Firewall).

> **Problem:** I need to find security vulnerabilities on my EC2 instances.
**Solution:** **Amazon Inspector**.

> **Problem:** I need to detect threats by analyzing logs (VPC, DNS, CloudTrail).
**Solution:** **Amazon GuardDuty**.

> **Problem:** I need to find and protect sensitive data (PII) in S3.
**Solution:** **Amazon Macie**.

> **Problem:** I need access to AWS compliance reports (SOC, PCI).
**Solution:** **AWS Artifact**.

---

## 💻 Domain 3: Technology (33%)

### 🗺️ Global Infrastructure Hierarchy
**Global** -> **Region** (e.g., us-east-1) -> **Availability Zone (AZ)** (e.g., us-east-1a) -> **Edge Location** (for CloudFront)

### ⚙️ Compute Decision Tree

> **Start Here:** What are you trying to run?
>
> 1.  **Just code, no servers?** ➡️ **AWS Lambda** (Serverless, event-driven)
> 2.  **A web app, but I don't want to manage infrastructure?** ➡️ **AWS Elastic Beanstalk** (PaaS)
> 3.  **A simple virtual server (e.g., WordPress blog)?** ➡️ **Amazon Lightsail** (Fixed monthly price)
> 4.  **I need full control over a virtual server.** ➡️ **Amazon EC2** (The core IaaS compute service)

### 💰 EC2 Pricing Model - When to Use What

| Model | Use Case | Savings | Key Feature |
| :--- | :--- | :--- | :--- |
| **On-Demand** | Spiky, unpredictable workloads; testing | None | Pay-per-second, no commitment |
| **Reserved** | Steady-state, predictable usage | Up to 75% | 1 or 3-year commitment |
| **Spot** | Fault-tolerant, can be interrupted | Up to 90% | Bid on spare capacity; can be terminated |
| **Dedicated** | Compliance, licensing needs | Most Expensive | Your own physical server |

### 🗄️ Storage Decision Tree

> **Start Here:** What kind of data are you storing?
>
> 1.  **Files & Objects?** ➡️ **Amazon S3** (then choose a class below)
> 2.  **A hard drive for my EC2 instance?** ➡️ **Amazon EBS** (Block storage)
> 3.  **A shared network drive for multiple EC2s?** ➡️ **Amazon EFS** (File storage)
> 4.  **A hybrid solution to connect on-prem to AWS storage?** ➡️ **AWS Storage Gateway**

### 🧊 S3 Storage Classes - Cost vs. Access Time

| Class | Use Case | Retrieval Time | Cost (Storage) |
| :--- | :--- | :--- | :--- |
| **Standard** | Frequently accessed data | Milliseconds | Highest |
| **Standard-IA** | Infrequent access, needed fast | Milliseconds | Lower |
| **One Zone-IA** | Recreatable, infrequent data | Milliseconds | Lower |
| **Glacier Instant** | Archive, instant access | Milliseconds | Very Low |
| **Glacier Flexible** | Archive, no rush | Minutes to Hours | Very Low |
| **Glacier Deep Archive** | Long-term archive (7-10 yrs) | 12-48 Hours | **Lowest** |
| **Intelligent-Tiering** | Unknown/changing access patterns | Auto-moves data | Automated cost savings |

### 🗃️ Database: Relational vs. NoSQL

> **Problem:** I need a traditional database with tables, rows, and columns (SQL).
**Solution:** **Amazon RDS** (Managed MySQL, Postgres, etc.) or **Amazon Aurora** (High-performance version).

> **Problem:** I need a flexible, key-value database for high-traffic web apps (NoSQL).
**Solution:** **Amazon DynamoDB** (Serverless, single-digit ms latency).

> **Problem:** I need a database for analytics and data warehousing.
**Solution:** **Amazon Redshift**.

### 🌐 Networking Core Components

- **VPC (Virtual Private Cloud):** Your private, isolated section of AWS.
- **Subnet:** A segment of a VPC's IP address range where you can place resources.
  - **Public Subnet:** Has a route to an **Internet Gateway (IGW)**.
  - **Private Subnet:** Uses a **NAT Gateway** for outbound internet access.
- **Security Group:** A **stateful** firewall for your **EC2 instances**.
- **NACL (Network ACL):** A **stateless** firewall for your **subnets**.
- **Route 53:** DNS service. Routes users to applications.
- **CloudFront:** CDN. Caches content at **Edge Locations** for low latency.

---

## 💵 Domain 4: Billing & Pricing (16%)

### 🛠️ Cost Management Tools

> **Q: How can I visualize and forecast my costs?**
**A:** **AWS Cost Explorer**.

> **Q: How can I get an alert if I'm about to go over my budget?**
**A:** **AWS Budgets**.

> **Q: How can I get the most detailed billing data possible?**
**A:** **AWS Cost and Usage Report (CUR)**.

> **Q: How can I estimate the cost of a new architecture?**
**A:** **AWS Pricing Calculator**.

### 🤝 AWS Support Plans

| Plan | Cost | Use Case | Key Feature |
| :--- | :--- | :--- | :--- |
| **Basic** | Free | Personal use, learning | Documentation access |
| **Developer** | $29/mo+ | Testing, development | Business hours email support |
| **Business** | $100/mo+ | Production workloads | 24/7 phone/chat, <1hr response |
| **Enterprise** | $15k/mo+ | Mission-critical systems | <15min response, **TAM** |

### 🏢 AWS Organizations

- **Purpose:** Centrally manage multiple AWS accounts.
- **Key Benefits:**
  - **Consolidated Billing:** Get one bill for all accounts.
  - **Volume Discounts:** Pool usage to get cheaper pricing.
  - **Service Control Policies (SCPs):** Restrict what users can do in member accounts.

---

## 🔥 Final Cram Session: Must-Know Facts

- **Well-Architected Framework (5 Pillars):** `OSRPC` - Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization.
- **IAM Best Practice:** Use **Roles** for EC2 permissions, not access keys. Always enable **MFA** on the root account.
- **S3 Durability:** 99.999999999% (11 nines).
- **High Availability:** Achieved by deploying across multiple **Availability Zones (AZs)**.
- **Fault Tolerance:** The system can withstand component failure with no downtime.
- **Scalability:** **Vertical** (Scale Up = bigger instance) vs. **Horizontal** (Scale Out = more instances).
- **CloudWatch:** Monitors **performance** (metrics, logs, alarms).
- **CloudTrail:** Monitors **API activity** (who did what, when).
- **Trusted Advisor:** Provides recommendations on cost, performance, security, and fault tolerance. Full checks require Business or Enterprise support.

**You've got this! Good luck!** 🚀
