# Azure Infrastructure as Code

This directory will contain the Bicep templates used to deploy the Azure Secure Landing Zone and Threat Detection Lab.

The infrastructure code is intended to provide a repeatable, documented and security-focused deployment process.

## Planned Resources

- Resource group deployment configuration
- Virtual network
- Management and workload subnets
- Network security groups
- Storage account
- Azure Key Vault
- Log Analytics workspace
- Diagnostic settings
- Monitoring resources
- Optional Microsoft Sentinel resources

## Planned Structure

- `main.bicep` – Main deployment entry point
- `modules/` – Reusable Bicep resource modules
- `parameters/` – Environment-specific parameter files

## Design Principles

- Least privilege
- Secure defaults
- Network segmentation
- Centralised logging
- Consistent naming
- Reusable modules
- Parameterised deployment
- Minimal unnecessary public exposure
- Cost-conscious resource selection

## Current Status

The Bicep templates have not yet been implemented. Infrastructure code will be added after the architecture and security requirements are defined.
