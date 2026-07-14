# Network Design

## 1. Purpose

This document defines the proposed network architecture for the Azure Secure Landing Zone and Threat Detection Lab.

The design supports the fictional organisation Northstar Technology Services and focuses on:

- Network segmentation
- Least-privilege communication
- Minimal public exposure
- Centralised monitoring
- Repeatable deployment through Bicep
- Cost-conscious operation

This document currently represents the planned design. It will be updated as resources are deployed, tested and refined.

---

## 2. Design Goals

The network must:

1. Separate management resources from application workloads.
2. Prevent unnecessary inbound access from the public internet.
3. Use network security groups to control traffic between subnets.
4. Avoid permanently exposing SSH or RDP.
5. Support centralised logging and investigation.
6. Allow temporary test workloads to be deployed safely.
7. remain simple enough for a small personal Azure lab.
8. Support future security improvements such as private endpoints.

---

## 3. Proposed Architecture

The initial environment will use one Azure virtual network containing two subnets:

- **Management subnet** – reserved for administrative or security-management resources.
- **Workload subnet** – used for temporary application or testing workloads.

Each subnet will have its own network security group.

```mermaid
flowchart TB
    Admin[Authorised Administrator]

    subgraph Azure["Microsoft Azure"]
        subgraph RG["Northstar Lab Resource Group"]
            subgraph VNet["vnet-northstar-lab - 10.10.0.0/16"]
                subgraph Mgmt["snet-management - 10.10.1.0/24"]
                    MgmtResource[Optional Management Resource]
                end

                subgraph Workload["snet-workload - 10.10.2.0/24"]
                    TestResource[Temporary Test Workload]
                end
            end

            NSGM[Management NSG]
            NSGW[Workload NSG]
            Storage[Secure Storage Account]
            KeyVault[Azure Key Vault]
            Logs[Log Analytics Workspace]
            TrafficAnalytics[Optional Traffic Analytics]
        end
    end

    Admin -. Controlled temporary access .-> MgmtResource
    MgmtResource --> TestResource
    NSGM --- Mgmt
    NSGW --- Workload
    Storage -. Diagnostic logs .-> Logs
    KeyVault -. Diagnostic logs .-> Logs
    VNet -. Virtual Network flow logs .-> Storage
    Storage -. Optional flow-log processing .-> TrafficAnalytics
    TrafficAnalytics -. Processed network insights .-> Logs
```

Virtual Network flow logs will be written to the secure Storage account rather than directly to Log Analytics. Traffic Analytics may optionally process the stored flow-log data and make network insights available through the Log Analytics workspace.

Virtual Network flow-log collection, Storage retention, optional Traffic Analytics processing and Log Analytics ingestion or retention may each generate charges. These features will be enabled only when required for a controlled lab exercise and after their cost implications have been reviewed.
