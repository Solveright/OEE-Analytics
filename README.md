## 🚀 Smart Factory OEE Analytics

### 🛠️ Tech Stack
- Databricks, Delta Lake, Databricks SQL, Azure Event Hub

### 📌 Highlights
- Built OEE analytics pipeline using Medallion Architecture
- Calculated Availability, Performance, and Quality KPIs
- Developed Databricks SQL dashboards for production monitoring
- Automated ETL with Delta Lake
  
### 📊 Dashboard Preview
<img width="1181" height="735" alt="image" src="https://github.com/user-attachments/assets/284732f5-14db-418f-82e6-290f24ca09e6" />

### 🏗️ Solution Architecture
```mermaid
flowchart TD

    subgraph OT[" "]
        OT_LABEL["Operational Technology"]
        OPC["OPC UA Simulator"]
        Kepware["Kepware"]

        OT_LABEL --> OPC
        OPC --> Kepware
    end

    subgraph ING[" "]
        ING_LABEL["Ingestion"]
        EH["Azure Event Hub"]
        DSS["Databricks Structured Streaming"]

        ING_LABEL --> EH
        EH --> DSS
    end

    subgraph LH[" "]
        LH_LABEL["Lakehouse"]

        Bronze["Bronze<br/>Raw Telemetry"]
        Silver["Silver<br/>Curated Telemetry"]
        Gold["Gold<br/>Production KPIs"]

        LH_LABEL --> Bronze
        Bronze --> Silver
        Silver --> Gold
    end

    subgraph AN[" "]
        AN_LABEL["Analytics"]

        OEE["OEE Dashboard"]
        Down["Downtime Analysis"]
        Throughput["Throughput Metrics"]
        Quality["Quality KPIs"]

        AN_LABEL --> OEE
    end

    Kepware --> EH
    DSS --> Bronze

    Gold --> OEE
    Gold --> Down
    Gold --> Throughput
    Gold --> Quality
```
