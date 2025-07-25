# Azure Billing Optimizer – Serverless Cost Optimization Project

## 📘 Overview

This project provides a practical implementation of a **serverless cost optimization architecture** using **Azure Cosmos DB**, **Azure Functions**, and **Python**.

### ✅ Objective

To reduce costs in a read-heavy Cosmos DB workload by **archiving old billing records** (older than 3 months) to a lower-cost container while preserving availability.

---

## 🚀 Architecture

- **Serverless**: Azure Function with Timer trigger
- **Database**: Cosmos DB (original + archive containers)
- **Infrastructure**: ARM template for full resource provisioning
- **Automation**: Timer-based data archival (no manual trigger required)

---
## Screenshots

📌**Note:** Sensitive details like keys are partially blurred for security.

1. **Azure Function App in Azure Portal**  
   ![Function App in Portal](https://github.com/Prudhvi5442/Azure-billing-optimizer/blob/60a4ad551ab372756e617650182e82a1f46b3632/screenshots/Azure%20Function%20App%20in%20Azure%20Portal.png)

2. **Cosmos DB Container with Billing Records**  
   ![Cosmos DB Data](https://github.com/Prudhvi5442/Azure-billing-optimizer/blob/60a4ad551ab372756e617650182e82a1f46b3632/screenshots/Cosmos%20DB%20Container%20with%20Billing%20Records.png)

2. **storage account**  
   ![storage](https://github.com/Prudhvi5442/Azure-billing-optimizer/blob/60a4ad551ab372756e617650182e82a1f46b3632/screenshots/storage-account.png)

3. **Log Output of Function Executing**  
   ![Function Log Output](./screenshots/function-logs.png)

4. **App Settings with Cosmos Credentials (Blurred)**  
   ![App Settings](https://github.com/Prudhvi5442/Azure-billing-optimizer/blob/60a4ad551ab372756e617650182e82a1f46b3632/screenshots/App%20Settings%20with%20Cosmos%20Credentials%20(Blurred).png)

5. **Terminal Output After Successful Deployment**  
   ![Terminal Output](https://github.com/Prudhvi5442/Azure-billing-optimizer/blob/60a4ad551ab372756e617650182e82a1f46b3632/screenshots/Terminal%20Output%20After%20Successful%20Deployment.png)

---

## 🧱 Architecture Diagram

This diagram illustrates the serverless architecture used to optimize billing records by archiving data older than 3 months to reduce storage cost.

![Architecture Diagram](./screenshots/architecture.png)


---

## ⏰ Function Logic

- Triggered every **hour**
- Connects to primary Cosmos DB container
- Moves billing records **older than 90 days** to an **archive container**
- Deletes archived records from the original container

---

## ✅ Constraints Met

| Constraint                  | Status  |
|----------------------------|---------|
| No downtime                | ✅ Yes  |
| No data loss               | ✅ Yes  |
| No API contract changes    | ✅ Yes  |
| Simplicity                 | ✅ Yes  |
| Serverless & scalable      | ✅ Yes  |

---

## 🧪 Testing

- Function tested by inserting sample data via Data Explorer
- Archive operation verified in Cosmos DB portal
- Logs available in Azure Monitor under the Function App resource

---
## 🤝 Acknowledgements

- Project architecture, logic, and deployment were implemented by me.
- Guidance and step-by-step instructions were supported using **ChatGPT by OpenAI** to ensure best practices and efficient implementation.
