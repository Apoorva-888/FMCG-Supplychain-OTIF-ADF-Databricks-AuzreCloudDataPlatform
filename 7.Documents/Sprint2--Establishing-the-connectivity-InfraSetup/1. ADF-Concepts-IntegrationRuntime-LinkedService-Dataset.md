# Azure Data Factory (ADF) Concepts – Integration Runtime, Linked Service, Dataset

## 1️⃣ Introduction

In modern data engineering, moving data from **on-premises systems** to **cloud platforms** (or vice versa) is a core requirement. Azure Data Factory (ADF) is a **cloud-based ETL tool** that allows you to **orchestrate and automate data movement and transformation**.

---

## 2️⃣ Analogy: Bringing Water and Fruits Home

| Concept              | Analogy Example                        | Azure Term                        |
|---------------------|----------------------------------------|----------------------------------|
| Data                 | Water / Fruits                          | Dataset                          |
| Container / Structure| Water bottle / Bag                      | Dataset                          |
| Vehicle              | Four-wheeler / Two-wheeler             | Linked Service                   |
| Path / Road / Bridge | Bridge / Road                           | Integration Runtime (IR)         |

### Example 1: Moving Water (Data)

1. **Water** → The **data** we want to move.  
2. **Water Bottle** → Container (**Dataset**) for the data.  
3. **Four-wheeler** → Vehicle (**Linked Service**) to transport data.  
4. **Bridge / Road** → Path (**Integration Runtime**) connecting on-prem to cloud.

**Key Point:**  
- Integration Runtime is **shared** if the path is the same.  
- Dataset is **specific** to the type of data.  
- Linked Service may vary depending on the vehicle (e.g., MySQL vs SFTP).

---

### Example 2: Moving Fruits / Vegetables

1. **Fruits / Vegetables** → New data source.  
2. **Bag** → New container (**Dataset**) for this data.  
3. **Two-wheeler / Four-wheeler** → Vehicle (**Linked Service**) for transporting fruits.  
4. **Bridge / Road** → Same Integration Runtime (IR) can be reused.

**Observation:**  
- You **don’t need a new IR** if the location is the same.  
- **Linked Services** and **Datasets** are **specific** to data type or source.

---

## 3️⃣ Project Example (SFTP + MySQL)

| Component             | Count | Notes |
|-----------------------|-------|-------|
| Integration Runtime    | 1     | Shared for both sources |
| Linked Services        | 2     | One for MySQL, one for SFTP |
| Datasets               | 2     | One for MySQL, one for SFTP |

**Summary:**  
- **IR (Integration Runtime)** = bridge / path connecting on-prem to cloud  
- **Linked Service** = vehicle carrying the data  
- **Dataset** = container for the data  

---

## 4️⃣ Key Points / Best Practices

1. **Reuse Integration Runtime** when moving multiple data types from the same source/destination.  
2. **Use different Linked Services** for different source connections.  
3. **Datasets** should be specific to the data format (CSV, Parquet, SQL table, etc.).  
4. **Self-hosted IR** is needed for on-prem sources; **Azure IR** can be used for cloud-only data movement.  
5. Naming conventions and folder structures help maintain clarity in large projects.

---

## 5️⃣ Common Interview Questions & Short Answers

| Question | How to Answer Concisely |
|----------|-------------------------|
| What is Integration Runtime? | “IR is the bridge/path that allows ADF to connect on-prem or cloud sources and move data securely.” |
| What is a Linked Service? | “A Linked Service is a connection to a data source or destination, like a vehicle transporting the data.” |
| What is a Dataset in ADF? | “A Dataset represents the structure of data, like a container (CSV, Parquet, SQL table) used to hold the data.” |
| How many IR, Linked Services, Datasets are required? | “IR can be shared across multiple sources if location is same; Linked Services and Datasets are source-specific.” |
| Difference between Self-hosted IR and Azure IR? | “Self-hosted IR is installed on-prem to access local data; Azure IR runs in the cloud for cloud-to-cloud data movement.” |
| Can one IR be used for multiple datasets? | “Yes, as long as the IR connects the same source and destination.” |
| How do you move data from SFTP to Azure Data Lake? | “Create a Linked Service for SFTP, a Linked Service for ADLS, define Datasets for both, then use a Copy Activity via an IR.” |

---

## 6️⃣ References / Further Reading

- [Azure Data Factory Documentation](https://learn.microsoft.com/en-us/azure/data-factory/introduction)  
- [Self-hosted Integration Runtime](https://learn.microsoft.com/en-us/azure/data-factory/self-hosted-integration-runtime)  
- [ADF Pipeline Best Practices](https://learn.microsoft.com/en-us/azure/data-factory/monitor-visually)  

---

