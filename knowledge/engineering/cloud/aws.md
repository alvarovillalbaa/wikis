# AWS Cloud Engineering

[Source: WORK/KNOWLEDGE/Programming/AWS/Startup_the_right_way_-_the_Well_Architected_approach.pdf]
[Source: WORK/KNOWLEDGE/Programming/AWS/From_Container_to_Startup__AWS_Container_Services_for_accelerating_modern_applications.pdf]
[Source: WORK/KNOWLEDGE/Programming/AWS/Optimize_cloud_storage_for_cost_and_performance.pdf]
[Source: WORK/KNOWLEDGE/Programming/AWS/AWS_Certified_Solutions_Architect_-_Professional__Official_Exam_Guide.pdf]

AWS architectural frameworks, container service selection, and storage optimization patterns.

## AWS Well-Architected Framework

Structure: **Pillars** + **Design principles** + **Questions**. Purpose: Learn → Measure → Improve workloads. Tool: AWS Well-Architected Tool (console) generates improvement plan with risk scoring per pillar.

### 6 Pillars

| Pillar | Definition | Key design principles |
|---|---|---|
| **Operational Excellence** | Support development, run workloads effectively, gain insight, continuously improve | Operations as code; frequent small reversible changes; refine procedures; anticipate failure; learn from failures |
| **Security** | Protect data/systems/assets using cloud technologies to improve security posture | Strong identity foundation; traceability; security at all layers; automate security; protect data in transit + at rest; keep people away from data; prepare for security events |
| **Reliability** | Workload performs intended function correctly and consistently when expected | Auto-recover from failure; test recovery procedures; scale horizontally; stop guessing capacity; manage change in automation |
| **Performance Efficiency** | Use computing resources efficiently as demand changes and technologies evolve | Democratize advanced tech; go global in minutes; use serverless; experiment more; mechanical sympathy |
| **Cost Optimization** | Run systems to deliver business value at the lowest price point | Cloud financial management; consumption model; measure efficiency; stop undifferentiated heavy lifting; analyze/attribute expenditure |
| **Sustainability** | Minimize environmental impact of running cloud workloads | Understand impact; set goals; maximize utilization; adopt efficient hardware; use managed services; reduce downstream impact |

### Shared Responsibility Model (Security)
- **AWS**: security *of* the cloud — compute, storage, database, networking, global infrastructure (regions, AZs, edge locations)
- **Customer**: security *in* the cloud — customer data, platform, applications, IAM, OS, network/firewall config, client-side encryption, server-side encryption, network traffic protection

### Shared Responsibility Model (Sustainability)
- **AWS**: servers, cooling, water, waste, data centers, electricity supply
- **Customer**: data design/usage, software application design, platform deployments/scaling, data storage, code efficiency, utilization/scaling

### Security — key architecture pattern
Internet → Route 53 → CloudFront → WAF → VPC (public subnet: ALB + NAT GW; private subnet: Aurora + Endpoints) with NACL + route tables. Encrypt at rest: KMS + S3. Encrypt in transit: CloudFront + ACM + SSL/TLS. Server-side: KMS + data encryption keys.

### Reliability — key architecture pattern
Multi-AZ (A/B/C) with Auto Scaling Groups for web tier and app tier; RDS primary + secondary replica. Auto-recovery services: Amazon RDS, Route 53, Auto Scaling, S3.

### Performance Efficiency — serverless stack
- Compute: AWS Lambda, AWS Fargate
- Data stores: Amazon S3, Amazon Aurora Serverless, Amazon DynamoDB
- Integration: Amazon API Gateway, Amazon EventBridge, Amazon SQS, Amazon SNS, AWS Step Functions
- Pattern: S3 (static) → API Gateway → Lambda → Lambda functions (fan-out)

### Cost Optimization — undifferentiated heavy lifting
Replace: ELB → EC2 instances → RDS with: API Gateway → Lambda → Aurora Serverless. Remove operational burden of managing servers.

### Sustainability — Graviton
AWS Graviton2/3: best performance per watt in EC2. Supported across Aurora, RDS, MemoryDB, ElastiCache, OpenSearch, EMR, Lambda, Fargate.

### SAP-C02 Exam Domain Framework (conceptual reference only)
4 domains weighted by exam score:
- Domain 1: Design Solutions for Organizational Complexity (26%) — network connectivity, security controls, resilient architecture, multi-account environments, cost optimization
- Domain 2: Design for New Solutions (29%) — deployment strategy, business continuity, security controls, reliability, performance, cost optimization
- Domain 3: Continuous Improvement for Existing Solutions (25%)
- Domain 4: Accelerate Workload Migration and Modernization (20%)

Key skills tested: RTO/RPO design, DR strategies (pilot light, warm standby, multi-site), IAM least privilege, IaC (CloudFormation), CI/CD, AWS Organizations + Control Tower.

---

## Container Services on AWS

### Container taxonomy (4 service relationship types)
1. **Runs generic images** (user provides image): ECS, EKS, Lambda, App Runner
2. **Provides value + runs generic images**: Amplify, IoT Greengrass, Elastic Beanstalk
3. **Provides value + uses images** (service provides image): SageMaker, EMR
4. **Provides value + produces/deploys images**: Amplify, App Runner (hidden image)

Only types 1 and 2 answer: "How do I run *my* container image on AWS?"

### Container architecture layers
- **Provisioning**: Docker Compose, App Runner, Copilot, IoT Greengrass, Elastic Beanstalk, Amplify, Lightsail, Batch
- **Orchestration**: Amazon ECS, Amazon EKS, ROSA
- **Capacity**: Amazon EC2, AWS Fargate, customer-managed (server/edge)
- **Cross-cutting**: AWS Lambda (spans provisioning + capacity)

### Container selection decision axes
- Simplicity (not an ops powerhouse) → App Runner, Elastic Beanstalk
- Flexibility (unique requirements) → ECS, EKS
- Agility (speed) → Fargate, Lambda
- Hybridity (regulatory) → EKS + Outposts, Greengrass

---

## S3 Storage Optimization

### S3 storage class taxonomy

| Class | Use case | Access latency | Notes |
|---|---|---|---|
| S3 Standard | Frequently accessed | Milliseconds | Multi-AZ ≥3 |
| S3 Standard-IA | Infrequently accessed | Milliseconds | Min object size; multi-AZ |
| S3 Glacier Instant Retrieval | Rarely accessed | Milliseconds | Min object size |
| S3 Glacier Flexible Retrieval | Archive | Minutes to hours | Free bulk retrieval |
| S3 Glacier Deep Archive | Long-term archive | Hours | Lowest cost |
| S3 One Zone-IA | Re-creatable, less-accessed | Milliseconds | Single AZ; retrieval charge/GB |
| S3 Outposts | On-premises data | Milliseconds | SSE-S3 encrypted |
| S3 Intelligent-Tiering | Unknown/changing access | Milliseconds | Automatic; no retrieval fees |

### Cost optimization decision tree

**Known/predictable access patterns** → use S3 Lifecycle policies:
- Objects >90 days → S3 Glacier Instant Retrieval
- Objects >365 days → S3 Glacier Deep Archive
- Lifecycle filters: object size (optimize transition costs), number of noncurrent versions (versioned buckets)
- S3 Storage Class Analysis: monitors access patterns, recommends transition point (30–730 day observation window)

**Unknown/changing access patterns** → use S3 Intelligent-Tiering:
- 5 tiers: Frequent Access → Infrequent Access → Archive Instant Access → Archive Access (optional) → Deep Archive Access (optional)
- Auto-moves objects between tiers; monitoring fee per object; no retrieval fees
- Archive Instant Access tier: up to 68% lower cost with no performance impact
- 99.9% availability, 11 9s durability
- Set via `x-amz-storage-class: INTELLIGENT_TIERING` in PUT header

### S3 economics fundamentals
- Two key variables: **frequency of access** + **duration of storage**
- Per-GB request cost decreases as object size increases (large objects cheaper per GB to request)
- Ingest directly to target class via `x-amz-storage-class` header — saves cost from day 0

### EBS cost optimization (covered in storage deck)
- Right-size volumes; delete unattached volumes; use snapshots lifecycle policies
- gp3 > gp2 for cost (same performance, cheaper)

## Sources
- AWS Innovate 2022: "Startup the right way – the Well-Architected approach" (Thiago de Faria)
- AWS Innovate 2022: "From Container to Startup: AWS Container Services for accelerating Modern Applications" (Natasha Wright, Robert Northard)
- AWS Innovate 2022: "Faster and lower-cost: Optimizing cloud storage for cost and performance" (Veliswa Boya)
- AWS Certified Solutions Architect – Professional (SAP-C02) Exam Guide, Version 1.0
