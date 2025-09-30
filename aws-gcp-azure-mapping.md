# AWS ↔ GCP ↔ Azure Service Mapping

This document provides a quick mapping of cloud services across **AWS**, **Google Cloud Platform (GCP)**, and **Microsoft Azure**.

---

## 🌐 Core Compute
| **Category** | **AWS** | **GCP** | **Azure** |
|--------------|---------|---------|------------|
| Virtual Machines | EC2 | Compute Engine | Virtual Machines |
| Containers (managed) | ECS / EKS | GKE | AKS (Azure Kubernetes Service) |
| Serverless | Lambda | Cloud Functions | Azure Functions |
| Batch Jobs | AWS Batch | Cloud Batch | Azure Batch |

---

## 💾 Storage
| **Category** | **AWS** | **GCP** | **Azure** |
|--------------|---------|---------|------------|
| Object Storage | S3 | Cloud Storage | Blob Storage |
| Block Storage | EBS | Persistent Disk | Managed Disks |
| File Storage | EFS | Filestore | Azure Files |
| Archival Storage | Glacier | Coldline/Archive | Azure Archive Storage |

---

## 🗄️ Databases
| **Category** | **AWS** | **GCP** | **Azure** |
|--------------|---------|---------|------------|
| Relational DB | RDS | Cloud SQL | Azure SQL Database |
| NoSQL | DynamoDB | Firestore / Datastore | Cosmos DB |
| Data Warehouse | Redshift | BigQuery | Synapse Analytics |
| Caching | ElastiCache | Memorystore | Azure Cache for Redis |

---

## 🔐 Identity & Access
| **Category** | **AWS** | **GCP** | **Azure** |
|--------------|---------|---------|------------|
| Identity & Access | IAM | IAM | Azure RBAC (Role-Based Access Control) |
| Directory Services | AWS Directory Service | Cloud Identity | Azure Active Directory (AAD) |

---

## 📡 Networking
| **Category** | **AWS** | **GCP** | **Azure** |
|--------------|---------|---------|------------|
| Virtual Network | VPC | VPC | Virtual Network (VNet) |
| Load Balancer | ELB / ALB / NLB | Cloud Load Balancing | Azure Load Balancer / App Gateway |
| CDN | CloudFront | Cloud CDN | Azure CDN |
| DNS | Route 53 | Cloud DNS | Azure DNS |

---

## 📊 Analytics & AI
| **Category** | **AWS** | **GCP** | **Azure** |
|--------------|---------|---------|------------|
| Data Lake | S3 + Lake Formation | BigLake | Data Lake Storage |
| Stream Processing | Kinesis | Dataflow / Pub/Sub | Event Hubs / Stream Analytics |
| ML Services | SageMaker | Vertex AI | Azure Machine Learning |

---

## 🛠️ DevOps & Infra
| **Category** | **AWS** | **GCP** | **Azure** |
|--------------|---------|---------|------------|
| Infra as Code | CloudFormation | Deployment Manager | ARM / Bicep |
| CI/CD | CodePipeline | Cloud Build | Azure DevOps Pipelines |
| Monitoring | CloudWatch | Cloud Monitoring | Azure Monitor |
| Logging | CloudWatch Logs | Cloud Logging | Azure Log Analytics |

---

## ⚡ Takeaway
Since you already know AWS and GCP, just translate the **names + slight usage differences**.  

The **biggest Azure-specific parts** are:  
- **Azure Active Directory (AAD)** → tightly tied to Microsoft ecosystem.  
- **ARM/Bicep** → for infra automation (similar to CloudFormation / Deployment Manager).  
- **Hybrid & enterprise tools** → Azure Arc, strong Windows/Office integrations.  
