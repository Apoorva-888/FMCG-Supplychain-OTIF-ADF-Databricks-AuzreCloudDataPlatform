# FMCG-Supplychain-OTIF-ADF-Databricks-AuzreCloudDataPlatform
Enterprise Azure Data Engineering platform for an FMCG supply chain to track On-Time, In-Full (OTIF) service levels. The solution ingests data from MySQL and SFTP using Azure Data Factory, transforms data using Azure Databricks, and stores curated Bronze, Silver, and Gold datasets in ADLS Gen2 with logging, alerts, and CI/CD support.

---

## 📌 Project Overview
This project is designed for an FMCG manufacturing client operating in India who aims to improve customer service levels before expanding into new cities.The key challenge identified was **poor service levels caused by delayed and incomplete deliveries**, leading to loss of key customer contracts.To address this, the Supply Chain Analytics team implemented a **scalable Azure-based data platform** to track:
- **On-Time Delivery (OT %)**
- **In-Full Delivery (IF %)**
- **On-Time In-Full (OTIF %)**
on a **daily basis per customer**, compared against defined service-level targets.

---

## 🎯 Business Objectives
- Identify delivery delays and short shipments early
- Improve customer satisfaction and contract renewals
- Enable data-driven supply chain decisions
- Build a future-ready analytics platform for expansion
---

## 🏗️ High-Level Architecture
**Source Systems**
- MySQL (Order & Delivery data)
- SFTP (Partner / logistics files)
**Azure Services Used**
- Azure Data Factory (Orchestration)
- Azure Databricks (Transformations)
- Azure Data Lake Gen2 (Storage)
- Azure Key Vault (Secrets)
- Azure Logic Apps (Email Alerts)
- Azure DevOps (CI/CD)
**Data Layers**
- Landing
- Bronze
- Silver
- Gold
---

## 🔄 Data Flow Summary
```
MySQL / SFTP
     ↓
ADF Ingestion Pipelines
     ↓
ADLS Gen2 (Landing)
     ↓
Databricks Transformations
     ↓
Bronze → Silver → Gold
     ↓
OT / IF / OTIF Metrics
```

---
## 📂 Repository Structure
- **adf/** → Azure Data Factory pipelines, datasets, linked services
- **databricks/** → PySpark notebooks for transformations
- **infra/** → Azure infrastructure configuration references
- **cicd/** → Azure DevOps YAML pipelines
- **sql/** → Source and reference SQL scripts
- **docs/** → Architecture and execution documentation
---

## 🚀 Sprint-wise Implementation
#### Sprint 1 – Infrastructure Setup
- Resource groups and environments
- VNet with public/private subnets
- Databricks workspace
- ADLS Gen2, Key Vault, Logic App
- ADF Git integration
#### Sprint 2 – Connectivity Setup
- Self-hosted Integration Runtime
- Linked services (MySQL, SFTP, ADLS, Databricks)
- Secure secrets in Key Vault
- SPN setup for Databricks access
#### Sprint 3 – Source Data Ingestion
- MySQL source table creation
- ADF pipelines: MySQL → Landing
- Metadata-driven ingestion
- Logging and parameterization
#### Sprint 4 – Landing to Bronze
- SFTP ingestion pipelines
- Header handling and data cleansing
- Audit columns (load_id, timestamps)
- Budget configuration
#### Sprint 5 – Transformations
- Bronze → Silver normalization
- Deduplication and validations
- Silver → Gold OT / IF / OTIF calculations
- Archiving processed files
#### Sprint 6 – Automation & Alerts
- Scheduled triggers
- Logic App email notifications:
  - Pipeline start
  - Success
  - Failure
  - Count mismatch
- Unit and end-to-end testing
#### Sprint 7 – Production Deployment
- Prod environment setup
- SHIR configuration
- CI/CD pipelines for:
  - ADF
  - Databricks
- Release validation
---

## 🔐 Security & Governance
- Secrets stored in Azure Key Vault
- Managed identities & SPNs
- Network isolation using VNets
- Parameterized pipelines
- Centralized logging and monitoring
---

## 👨‍💻 Author
**Azure Data Engineer**  
Experience: **5+ years**  
Specialization:
- Azure Data Factory
- Databricks (PySpark)
- ADLS Gen2
- CI/CD with Azure DevOps
- Enterprise Data Platforms
---

## 📎 Notes
This project follows **industry best practices** for:
- Scalable data ingestion
- Layered lakehouse design
- Secure credential management
- Production-grade CI/CD pipelines
