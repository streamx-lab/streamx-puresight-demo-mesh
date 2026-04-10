# StreamX Commerce Accelerator

This repository provides a **Commerce Accelerator built on StreamX**, designed to quickly deliver a fully functional e-commerce frontend powered by a **microservices-based mesh architecture**.

The accelerator enables you to **launch an e-commerce experience with minimal or no custom development**, while still allowing full flexibility through integration with your own data sources (e.g. PIM systems).

---

# Overview

The StreamX Commerce Accelerator delivers:

* A ready-to-use **e-commerce frontend architecture**
* A **microservices mesh**
* Built-in support for:

  * **Product Detail Pages (PDP)**
  * **Product Category Pages (PCP)**
  * **Search and filtering (faceted search)**

The system is designed to work with **external data sources**, allowing you to plug in your own **Product Information Management (PIM)** system.

---

# Data Ingestion & Custom Sources

## Ingesting Data Using StreamX CLI

To quickly load sample or prepared data into the system, you can use the StreamX CLI.

### 1. Install StreamX CLI

```bash
brew install streamx-com/tap/streamx
```

### 2. Configure ingestion endpoint

1. Go to **Gateways** in the StreamX Console
2. Copy the **REST Ingestion URL**
3. Set it in CLI:

```bash
streamx settings set streamx.ingestion.url <INGESTION_URL>
```

### 3. Configure authentication

1. Go to **Sources** tab in the StreamX Console
2. Copy the **CLI token** (recommended due to wide permissions)
3. Set it in CLI:

```bash
streamx settings set streamx.ingestion.auth-token <TOKEN>
```

### 4. Publish data

```bash
sh scripts/publish-all.sh
```

### 5. Open your storefront

1. Go to **Gateways** in the StreamX Console
2. Open the URL for:

```
web-server-sink
```

---

## Connecting Your Own Data Source

To integrate your own data (e.g. external PIM):

* Use one of the available **StreamX connectors**, or
* Build a **custom connector**

### How integration works

Integration with external systems follows the same pattern as CLI ingestion:

* You need to provide:

  * **Ingestion URL**
  * **Authentication token**

These should be configured inside your connector instead of the CLI.

Your connector is responsible for:

* Fetching data from your external system
* Transforming it into StreamX-compatible events
* Sending it to the ingestion endpoint

---

# Architecture Overview

```
PIM (emulate or external one)
     │
     │ (Cloud Events)
     ▼
StreamX Ingestion
     │
     ├── Product & Content Storage
     ├── Search Index
     └── Delivery Services
             │
             ▼
        E-commerce Frontend
```

---

# Additional docs
Checkout docs folder for more information

# Result

You can launch a fully functional e-commerce site **in a very short time**, with the flexibility to extend and customize as needed.
