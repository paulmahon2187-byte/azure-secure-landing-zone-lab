# Azure Secure Landing Zone & Threat Detection Lab

## Overview

This project is being developed to demonstrate the design, secure deployment and security monitoring of a small Azure environment for a fictional technology company.

The planned environment is designed around the principles of least privilege, network segmentation, centralised logging, secure configuration and repeatable infrastructure deployment.

This is a small personal Azure security lab for learning and portfolio development. It is not a full enterprise-scale Microsoft Azure landing zone.

## Project Objectives

- Design a segmented Azure virtual network
- Apply least-privilege network security rules
- Configure Microsoft Entra ID groups and Azure RBAC
- Deploy Azure resources using Bicep
- Centralise platform and resource logs
- Review and remediate Defender for Cloud recommendations
- Develop KQL queries for security monitoring
- Create and document security detections
- Maintain cost controls and safe resource-cleanup procedures

## Planned Architecture

The planned environment will include:

- Dedicated Azure resource group
- Virtual network with separate management and workload subnets
- Network security groups
- Secure storage account
- Azure Key Vault
- Log Analytics workspace
- Azure Monitor diagnostic settings
- Microsoft Defender for Cloud
- Optional Microsoft Sentinel deployment
- Test workload deployed only during controlled lab sessions

## Technologies

- Microsoft Azure
- Microsoft Entra ID
- Azure RBAC
- Azure Virtual Network
- Network Security Groups
- Azure Monitor
- Log Analytics
- Microsoft Defender for Cloud
- Microsoft Sentinel (optional and planned)
- Kusto Query Language
- Bicep
- GitHub

## Repository Structure

- `infra/` – Bicep infrastructure-as-code files
- `docs/` – Architecture, implementation notes and security findings
- `detections/` – KQL queries and detection documentation
- `scripts/` – Deployment and cleanup utilities

## Project Status

**Phase 1: Planning and repository setup**

Current tasks:

- [ ] Create architecture diagram
- [x] Define security requirements
- [ ] Create Bicep project structure
- [ ] Configure Azure cost controls
- [ ] Deploy initial network resources
- [ ] Enable centralised logging
- [ ] Document security findings
- [ ] Develop KQL detections
- [ ] Complete final project report

## Security and Cost Notice

This project is planned for implementation only within an authorised personal Azure lab environment.

No production systems, third-party systems or real customer data will be used. Secrets and credentials must not be committed to this repository. Any Azure resources created for the lab will be deployed within a dedicated resource group and removed after testing where appropriate.
