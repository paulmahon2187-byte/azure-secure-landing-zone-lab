# Design Requirements

## 1. Purpose

This document defines the business, technical and security requirements for the Azure Secure Landing Zone and Threat Detection Lab.

The requirements will guide the architecture, implementation, testing and security assessment of the environment.

The project represents a small fictional technology company migrating a limited workload into Microsoft Azure.

---

## 2. Fictional Organisation

### Company Name

**Northstar Technology Services**

### Company Profile

Northstar Technology Services is a small UK-based technology consultancy with approximately 40 employees.

The company provides cloud support, software services and technical consultancy to small and medium-sized businesses.

Northstar is beginning to adopt Microsoft Azure and requires a secure foundation for hosting internal systems and test workloads.

### Current Challenges

The organisation currently lacks:

- A standard Azure deployment model
- Consistent resource naming and tagging
- Centralised security logging
- Formal role-based access control
- Network segmentation
- Documented security monitoring procedures
- Repeatable infrastructure deployment
- Reliable cost-monitoring controls

The company wants to address these weaknesses before deploying more important workloads.

---

## 3. Project Scope

The project will design and deploy a small Azure environment containing:

- A dedicated Azure resource group
- A segmented virtual network
- Management and workload subnets
- Network security groups
- A secure storage account
- Azure Key Vault
- Microsoft Entra ID security groups
- Azure role-based access control
- A Log Analytics workspace
- Azure Monitor diagnostic settings
- Microsoft Defender for Cloud configuration
- KQL security-monitoring queries
- Bicep infrastructure-as-code templates
- A temporary test workload where required

Microsoft Sentinel may be included as an optional component if it can be deployed safely within the project budget.

---

## 4. Users and Administrative Roles

The lab will model the following organisational roles.

| Role | Responsibility | Intended Access |
|---|---|---|
| Cloud Administrator | Deploys and manages Azure resources | Administrative access to the lab resource group |
| Security Analyst | Reviews logs, alerts and security findings | Read access to resources and access to monitoring data |
| Application Team | Manages approved workload resources | Contributor access limited to the workload area |
| Auditor | Reviews configuration and evidence | Read-only access |
| General User | Uses approved services | No administrative Azure access |

Access should be assigned through Microsoft Entra ID groups rather than directly to individual users wherever practical.

---

## 5. Security Principles

The design will follow these principles:

1. **Least privilege**  
   Users and services should receive only the permissions required for their responsibilities.

2. **Defence in depth**  
   Security controls should exist across identity, networking, resources, monitoring and administration.

3. **Secure by default**  
   Resources should avoid unnecessary public access and insecure default settings.

4. **Network segmentation**  
   Management and workload resources should be separated into dedicated subnets.

5. **Centralised visibility**  
   Relevant logs should be sent to a central Log Analytics workspace.

6. **Repeatable deployment**  
   Core resources should be deployable through Bicep rather than relying entirely on manual configuration.

7. **Cost awareness**  
   Resources should be selected and operated with a limited personal lab budget in mind.

8. **No real sensitive data**  
   The environment must contain only fictional, test or non-sensitive information.

---

## 6. Functional Requirements

| ID | Requirement |
|---|---|
| FR-01 | The environment must use a dedicated Azure resource group. |
| FR-02 | The environment must include a virtual network with separate management and workload subnets. |
| FR-03 | Each subnet must have an appropriate network security group. |
| FR-04 | The project must include a secure Azure Storage account. |
| FR-05 | The project must include an Azure Key Vault for demonstrating secret-management controls. |
| FR-06 | Administrative access must be represented through Microsoft Entra ID groups and Azure RBAC. |
| FR-07 | Relevant Azure logs must be sent to a central Log Analytics workspace. |
| FR-08 | The project must include KQL queries for security monitoring and investigation. |
| FR-09 | Core infrastructure must be represented through Bicep templates. |
| FR-10 | The project must include documented deployment and cleanup procedures. |
| FR-11 | Security weaknesses and remediation actions must be recorded as formal findings. |
| FR-12 | The environment must include cost-monitoring controls and documented cost considerations. |

---

## 7. Identity and Access Requirements

| ID | Requirement |
|---|---|
| IAM-01 | Permissions should be assigned to groups rather than directly to users wherever practical. |
| IAM-02 | Owner-level access must be avoided unless it is specifically required. |
| IAM-03 | Administrative, security and read-only responsibilities must be separated. |
| IAM-04 | RBAC assignments must be made at the narrowest practical scope. |
| IAM-05 | Privileged role assignments must be documented. |
| IAM-06 | Secrets, passwords and access keys must not be stored in the GitHub repository. |
| IAM-07 | Key Vault must use Azure RBAC or another clearly documented access-control model. |
| IAM-08 | Authentication and administrative activity should be logged where available. |

---

## 8. Network Security Requirements

| ID | Requirement |
|---|---|
| NET-01 | Management and workload resources must use separate subnets. |
| NET-02 | Network security group rules must follow least-privilege principles. |
| NET-03 | Unrestricted inbound access from the internet must not be permitted without a documented test requirement. |
| NET-04 | Administrative ports such as SSH and RDP must not be permanently exposed to the entire internet. |
| NET-05 | Network rules must include meaningful names and descriptions. |
| NET-06 | Default Azure network security rules must be reviewed and documented. |
| NET-07 | Public IP addresses should be avoided unless required for a controlled lab exercise. |
| NET-08 | Any temporary public exposure must be removed after testing. |

---

## 9. Data Protection Requirements

| ID | Requirement |
|---|---|
| DATA-01 | Only fictional or non-sensitive test data may be stored in the environment. |
| DATA-02 | Storage accounts must require secure transfer. |
| DATA-03 | Public blob access must be disabled unless temporarily enabled for a documented security test. |
| DATA-04 | Storage encryption must remain enabled. |
| DATA-05 | Key Vault secrets must not appear in screenshots, logs or GitHub files. |
| DATA-06 | Resource access keys and connection strings must not be committed to source control. |
| DATA-07 | Data-retention settings must be documented. |

---

## 10. Logging and Monitoring Requirements

| ID | Requirement |
|---|---|
| LOG-01 | A central Log Analytics workspace must be deployed. |
| LOG-02 | Relevant resource diagnostic settings must be enabled where supported. |
| LOG-03 | Azure administrative activity must be available for investigation. |
| LOG-04 | The project must include a query for Azure resource deletion events. |
| LOG-05 | The project must include a query for network security group changes. |
| LOG-06 | The project must include a query for privileged role assignments. |
| LOG-07 | The project must include a query for changes to logging or diagnostic settings. |
| LOG-08 | Each KQL query must document its purpose, data source and limitations. |
| LOG-09 | Monitoring evidence must be captured without exposing sensitive account information. |

---

## 11. Infrastructure-as-Code Requirements

| ID | Requirement |
|---|---|
| IAC-01 | The main Azure resources must be represented in Bicep. |
| IAC-02 | Reusable resources should be separated into modules where practical. |
| IAC-03 | Environment-specific values must be parameterised. |
| IAC-04 | Credentials and secrets must not be hard-coded. |
| IAC-05 | Resources must use consistent naming and tagging. |
| IAC-06 | Templates should use secure configuration defaults. |
| IAC-07 | Deployment commands and prerequisites must be documented. |
| IAC-08 | Bicep files must be validated before deployment. |

---

## 12. Cost Requirements

| ID | Requirement |
|---|---|
| COST-01 | The Azure subscription must have a budget and cost alerts where supported. |
| COST-02 | Expensive resources must not remain deployed unnecessarily. |
| COST-03 | Temporary workloads must be stopped or deleted after testing. |
| COST-04 | The project must document resources that may generate ongoing charges. |
| COST-05 | Optional Microsoft Sentinel components and paid Defender plans must not be enabled without reviewing their cost implications. |
| COST-06 | The environment must support removal through deletion of the dedicated resource group. |
| COST-07 | Cost alerts must not be treated as automatic spending limits. |

---

## 13. Documentation Requirements

The repository must include:

- Architecture documentation
- An architecture diagram
- Implementation records
- Infrastructure-as-code files
- KQL queries
- Security findings
- Before-and-after remediation evidence
- Screenshot evidence
- Cost and cleanup guidance
- Lessons learned
- Final project summary

Screenshots must be reviewed before upload to remove unnecessary personal or sensitive information.

---

## 14. Constraints and Assumptions

The project is subject to the following constraints:

- It is a personal learning environment rather than a production system.
- The available Azure budget is limited.
- Some features may require Microsoft Entra or Azure licences that are not available.
- Some monitoring data may require time to populate.
- Resources may be deployed temporarily and removed after evidence is collected.
- The design represents a small environment and is not intended to reproduce a full enterprise landing zone.
- No customer, employer or university systems will be tested.
- All activity will remain within an authorised personal Azure subscription.

---

## 15. Out of Scope

The following are outside the initial project scope:

- Production customer workloads
- Real personal or commercial data
- Penetration testing of third-party systems
- Hybrid connectivity to an on-premises network
- Multi-region disaster recovery
- Enterprise-scale management groups
- Azure ExpressRoute
- Production-grade continuous availability
- Permanent internet-facing workloads
- Full regulatory certification or compliance auditing

These may be discussed as future improvements but will not be presented as completed features.

---

## 16. Success Criteria

The project will be considered successful when:

- The Azure architecture is documented and diagrammed.
- The core environment can be deployed successfully.
- Network and identity controls reflect least-privilege principles.
- Logs are collected centrally.
- Useful KQL security queries have been tested.
- At least three security findings are documented and remediated.
- Core resources are represented through Bicep.
- Deployment and cleanup steps are reproducible.
- No secrets or sensitive identifiers are exposed through GitHub.
- The repository clearly demonstrates practical Azure security knowledge to a recruiter or technical interviewer.

---

## 17. Future Enhancements

Possible future improvements include:

- Optional Microsoft Sentinel analytics rules
- Automated deployment through GitHub Actions
- Private endpoints
- Azure Policy
- Conditional Access
- Privileged Identity Management
- Microsoft Defender workload-protection plans
- Automated Bicep security scanning
- Additional incident-response scenarios
- A second environment representing development and production
