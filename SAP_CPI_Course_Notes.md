# SAP BTP Cloud Integration (CPI) — Course Notes

**Course Coverage:** Cloud Integration, APIM, Event Mesh, Groovy, Open Connectors, Transportation (with Practicals)

---

## 1. Introduction to SAP Cloud Integration

### What is SAP Cloud Integration?
- SAP Cloud Integration supports **end-to-end process integration** through the **exchange of messages**
- It is built on the **open-source Apache Camel framework** from the Apache Software Foundation
- It is one of the **core capabilities of SAP BTP Integration Suite**
- Development, deployment, and monitoring are done using **graphical tools** — no server setup required
- It is a **low-code / no-code** tool — you subscribe and start using it immediately

---

## 2. Why Cloud Integration is Required

### The Problem: Multiple Systems in a Business
Modern businesses use many different software systems, for example:
- SAP ERP (core business operations)
- CRM (customer relationship management)
- JD Edwards (third-party ERP)
- SRM (supplier relationship management)
- Third-party HR systems
- Excel / simple databases (smaller companies)

All these systems store data in **different formats** with **different fields**. To run the business smoothly, data must flow between these systems accurately.

### What Cloud Integration Does
- **Connects** cloud and on-premise applications — both SAP and non-SAP
- **Transforms and cleanses** data between systems
- **Consolidates** data from multiple sources into one system
- **Migrates** data (e.g., from old ERP to S/4HANA)

---

## 3. Types of Integration

### A2A — Application to Application
- Communication between systems **within the same organization** (same firewall/landscape)
- Example: CRM sends customer lead data → SAP ERP creates a sales order

### B2B — Business to Business
- Communication between your organization and **external business partners**
- Examples: transportation, warehouse, order-to-cash, procure-to-pay, third-party logistics, financials
- Data is sent in a **secured way** to trading partners outside the company

> Both A2A and B2B are covered in this course.

---

## 4. Brief History of SAP Integration Tools

| Tool | Type | Notes |
|------|------|-------|
| XI (Exchange Infrastructure) | On-premise server | Early SAP integration server |
| PI (Process Integration) | On-premise server | Successor to XI |
| PO (Process Orchestration) | On-premise server | Latest on-premise integration tool |
| **Cloud Integration (CPI)** | **Cloud-based** | **No server purchase needed** |

Previously, companies had to **buy and maintain physical servers** for integration. Now with CPI, you just **subscribe** and use it.

---

## 5. SAP S/4HANA — Brief Background

Understanding S/4HANA helps you understand why integration matters:

- **Old ERP (R/3, ECC 6.0):** Used multiple databases (Oracle, SQL Server, DB2, Informix). RAM was limited (~128 GB). Most processing happened at the NetWeaver (ABAP) layer.
- **S/4HANA:** Uses only the **HANA in-memory database**. Supports terabytes of RAM (1 TB, 10 TB, up to 60 TB+). Processing is **pushed down to the database** using SQL Script — much faster.

### Why Move to Cloud?
- Buying and upgrading physical servers is expensive
- Cloud servers are **dynamically scalable** — you pay for what you use
- No need to hire Basis administrators for patching, restarts, user creation, version control

---

## 6. SAP BTP — Business Technology Platform

BTP is a **separate platform alongside SAP ERP**. The idea is to keep the ERP system "clean" and handle extensions, automation, and integrations on BTP.

### Key Capabilities of SAP BTP

| Area | Tools/Features |
|------|---------------|
| **App Development** | SAP Build Apps (low-code/no-code), Business Application Studio (BAS) |
| **Automation** | RPA, process monitoring, automated document processing |
| **Integration** | **Process Integration, API-led Integration, Event-driven Integration, B2B, Hybrid, Data Integration** |
| **Data & Analytics** | Operational databases, data warehouse, data lakes, analytics & planning |
| **AI / ML** | Machine learning and artificial intelligence tools |

> **This course focuses on: Process Integration + API-led Integration**

---

## 7. Cloud Infrastructure Providers (Hyperscalers)

SAP no longer uses only its own servers (formerly called **Neo servers**). SAP has collaborated with major cloud providers:

| Provider | Notes |
|----------|-------|
| **AWS** (Amazon Web Services) | Available in multiple global regions |
| **Microsoft Azure** | Available in multiple global regions |
| **Google Cloud** | Available in India (Mumbai), Australia, US, Frankfurt, etc. |
| **SAP (own servers)** | Available in select regions |
| **Alibaba Cloud** | Available in China only |

These providers are called **hyperscalers** — they have massive data centers worldwide.

To view available servers and regions:
> **URL:** `discovery.sap.com` → Filter services using a map

---

## 8. BTP Account Structure

When you purchase/subscribe to SAP BTP services, here is how the account hierarchy works:

```
Global Account
│
├── Directory (optional grouping)
│   ├── Sub Account 1 (e.g., Finance Apps — on AWS)
│   └── Sub Account 2 (e.g., XYZ Company — on Azure)
│
└── Sub Account 3 (standalone, on Google Cloud)
```

### Global Account
- Top-level account created when you purchase a BTP license
- All services, subscriptions, and memory allocations are managed here

### Sub Account
- Created under the global account
- You choose: which region, which cloud provider (AWS / Azure / Google Cloud / SAP)
- Each sub account is linked to a specific infrastructure

### Directory (Optional)
- Used to **group sub accounts** logically (e.g., by department or project)
- You can assign memory limits at the directory level to **control resource usage**
- Example: 20 GB total → 10 GB to Finance Directory, 10 GB to Sales Directory

### Memory/Resource Allocation
- Billing is based on usage: memory consumed, hours run, or number of users (varies by service)
- Memory is allocated at the global account level and distributed to sub accounts
- Sub accounts cannot exceed the memory assigned to them

---

## 9. API Management in BTP

### Why APIs?
SAP ERP (like S/4HANA) contains sensitive business data. Exposing this directly to the outside world is a security risk.

### Solution: API Proxy
1. Create an **API** (Application Programming Interface) that exposes only the required operations (Create, Read, Update, Delete)
2. A **proxy server** sits in front — it creates a separate URL for external users
3. External users authenticate with the proxy first
4. Once authenticated, the proxy internally redirects to the actual S/4HANA endpoint
5. The real URL of S/4HANA is **never exposed**

> API development is covered in this course alongside cloud integration.

---

## 10. Getting Started — Free Trial Account

### Steps to Register
1. Open **Chrome browser**
2. Go to the **BTP login page** (BTP Cockpit)
3. Click **Register** — provide your company or personal Gmail ID, username, and other details
4. An **activation link** is sent to your email — activate it
5. Use this email/password to log in to BTP going forward

### Trial Account Details
- Free for the first **30 days**
- Can be extended up to **90 days**
- Includes access to Cloud Integration (CPI) and other BTP services

---

## 11. Course Topics Overview

Based on the course syllabus, the following topics will be covered:

| Topic | Description |
|-------|-------------|
| **Cloud Integration (CPI)** | Core process integration — A2A and B2B message flows |
| **API Management (APIM)** | Creating and managing API proxies and endpoints |
| **Event Mesh** | Event-driven integration between systems |
| **Groovy Scripting** | Writing custom logic/scripts within integration flows |
| **Open Connectors** | Connecting third-party (non-SAP) applications |
| **Transportation** | Moving integration artifacts across landscapes (Dev → QA → Prod) |

All topics include **practical hands-on exercises**.

---

## Key Takeaways from Session 1

- SAP Cloud Integration is the **modern replacement** for on-premise PI/PO servers
- It handles **A2A** (within organization) and **B2B** (between organizations) scenarios
- It runs on **SAP BTP**, which is hosted on hyperscalers (AWS, Azure, Google, SAP, Alibaba)
- BTP account structure: **Global Account → Directory (optional) → Sub Account**
- **No server investment** needed — subscribe, scale dynamically, and pay for usage
- APIs are used to **securely expose** only required ERP data to the outside world
- A **free 90-day trial** is available to practice everything in this course

---

*Document prepared from Udemy course transcript — SAP BTP Cloud Integration with APIM, Event Mesh, Groovy, Open Connectors, and Transportation.*
