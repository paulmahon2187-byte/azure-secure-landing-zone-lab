# KQL Security Detections

This directory will contain Kusto Query Language queries developed for security monitoring and investigation within the Azure lab.

Each query will include an explanation of its purpose, required log source and expected output.

## Planned Queries

- Azure resource deletion events
- Network security group rule changes
- Privileged Azure RBAC assignments
- Key Vault access activity
- Storage account configuration changes
- Repeated authentication failures
- Unusual administrative activity
- Defender for Cloud security alerts
- Changes to logging or diagnostic settings

## Query Documentation

Each KQL file should document:

- Detection objective
- Required table or data source
- Query logic
- Known limitations
- Expected result
- Suggested investigation steps
- Potential false positives

## Current Status

KQL detections will be added after the required logs are connected to Log Analytics.
