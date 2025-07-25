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

## 📁 Project Structure

```plaintext
azure-billing-optimizer/
│
├── infra/                        # Phase 1 – Infrastructure as Code
│   └── azuredeploy.json         # ARM template to provision all Azure resources
│
├── function/                     # Phase 2 – Python Function App
│   ├── archive_old_billing_records/
│   │   ├── __init__.py          # Archival logic (moves records > 3 months)
│   │   └── function.json        # Timer trigger config (runs hourly)
│   ├── host.json
│   ├── requirements.txt
│   └── local.settings.json      # Local development settings (excluded from repo)
│
└── README.md                     # Project instructions


## ⏰ Function Logic

- Triggered every **hour**
- Connects to primary Cosmos DB container
- Moves billing records **older than 90 days** to an **archive container**
- Deletes archived records from the original container

##✅ Constraints Met

| Constraint                  | Status  |
|----------------------------|---------|
| No downtime                | ✅ Yes  |
| No data loss               | ✅ Yes  |
| No API contract changes    | ✅ Yes  |
| Simplicity                 | ✅ Yes  |
| Serverless & scalable      | ✅ Yes  |


## 🧪 Testing

- Function tested by inserting sample data via Data Explorer
- Archive operation verified in Cosmos DB portal
- Logs available in Azure Monitor under the Function App resource

---

## 🤝 Acknowledgements

- Project architecture, logic, and deployment were implemented by me.
- Guidance and step-by-step instructions were supported using **ChatGPT by OpenAI** to ensure best practices and efficient implementation.
