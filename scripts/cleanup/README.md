# Azure Cleanup Scripts

This directory contains scripts used to remove temporary Azure resources and reduce the risk of unexpected charges.

Cleanup scripts must be reviewed carefully before execution.

## Planned Functions

- Remove temporary test resources
- Delete the dedicated lab resource group
- Confirm the target subscription
- Confirm the target resource group
- List resources before deletion
- Require user confirmation before destructive actions
- Verify that cleanup completed successfully

## Safety Requirements

Cleanup scripts should:

- Never contain credentials
- Avoid hard-coded production resource names
- Display the active Azure subscription
- Require confirmation before deletion
- Clearly identify destructive commands
- Be tested only within the authorised lab environment

## Warning

These scripts may permanently delete Azure resources and associated data. They must only be used against the dedicated lab environment.

## Current Status

Cleanup scripts will be created after the first Azure resources are deployed.
