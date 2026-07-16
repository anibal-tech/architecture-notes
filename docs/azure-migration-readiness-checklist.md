# Azure Migration Readiness Checklist

## Purpose

This checklist helps teams assess whether an application, platform, or workload is ready to migrate from an on-premises environment to Microsoft Azure.

The focus is on readiness, risk control, architecture visibility, operational continuity, and business alignment before executing a cloud migration.

## When to Use This Checklist

Use this checklist for:

- On-premises to Azure migration
- Azure Landing Zone readiness review
- Business-critical workload migration
- Infrastructure modernization
- Application migration planning
- ERP or business application migration
- Integration-heavy system migration
- Data platform migration
- Pre-cutover cloud readiness review
- Operational readiness and BAU handover planning

## Migration Readiness Overview

```text
Application inventory
      ↓
Business criticality assessment
      ↓
Dependency mapping
      ↓
Data and integration review
      ↓
Security and compliance review
      ↓
Landing zone readiness
      ↓
Operational readiness
      ↓
Cutover and rollback planning
      ↓
Hypercare and BAU handover
```

## 1. Application Inventory

Before planning a migration, the team should understand what is being moved.

- [ ] Application name is documented.
- [ ] Business owner is identified.
- [ ] Technical owner is identified.
- [ ] Application owner is identified.
- [ ] Current hosting model is documented.
- [ ] Current infrastructure components are listed.
- [ ] Application architecture is documented.
- [ ] Current environment types are identified.
- [ ] Production, non-production, and disaster recovery environments are listed.
- [ ] Application lifecycle status is known.
- [ ] Current support model is documented.
- [ ] Licensing considerations are identified.
- [ ] Current operational pain points are documented.

Recommended inventory fields:

| Field | Description |
|---|---|
| Application name | Name of the application or workload |
| Business area | Business unit or process supported |
| Business owner | Accountable business stakeholder |
| Technical owner | Accountable technical contact |
| Hosting model | On-premises, hybrid, cloud, or other |
| Environment | Production, QA, UAT, development, DR |
| Technology stack | Operating system, runtime, database, middleware |
| Current SLA | Availability or support expectation |
| Migration strategy | Rehost, replatform, refactor, rebuild, replace, retire, or retain |
| Criticality | Business impact classification |
| Dependencies | Systems, data, integrations, teams, vendors |
| Compliance needs | Regulatory, contractual, or internal policy requirements |

## 2. Business Criticality

Assess how important the workload is to the business.

- [ ] Business criticality is classified.
- [ ] Impact of downtime is understood.
- [ ] Revenue, operational, or regulatory impact is documented.
- [ ] Business peak periods are identified.
- [ ] Maximum acceptable downtime is defined.
- [ ] Recovery time expectations are documented.
- [ ] Recovery point expectations are documented.
- [ ] Business continuity requirements are reviewed.
- [ ] Business owner has approved the migration priority.
- [ ] Stakeholders understand migration risk.

Suggested criticality levels:

| Level | Description |
|---|---|
| Critical | Business operations are blocked if unavailable |
| High | Major business process is degraded |
| Medium | Noticeable impact, but workaround may exist |
| Low | Limited business impact |

Useful questions:

- What happens if this application is unavailable?
- How many users or business areas are affected?
- Does the workload support customer-facing operations?
- Does the workload support financial, operational, or regulatory processes?
- What is the acceptable outage window?
- What is the required recovery time?

## 3. Migration Strategy

Define the migration approach for the workload.

- [ ] Migration strategy is selected.
- [ ] Strategy rationale is documented.
- [ ] Alternatives were considered.
- [ ] Risks and trade-offs are documented.
- [ ] Business owner understands impact.
- [ ] Technical owner confirms feasibility.
- [ ] Cost and operational impact are reviewed.

Common migration strategies:

| Strategy | Description |
|---|---|
| Rehost | Move the workload with minimal changes |
| Replatform | Move and make limited platform changes |
| Refactor | Modify the application to better fit cloud capabilities |
| Rearchitect | Significantly redesign the application architecture |
| Rebuild | Build a new solution using cloud-native capabilities |
| Replace | Replace the current solution with another product or SaaS |
| Retain | Keep the workload where it is for now |
| Retire | Decommission the workload |

## 4. Dependencies

Dependencies are one of the most important areas to review before migration.

- [ ] Application dependencies are documented.
- [ ] Database dependencies are documented.
- [ ] Integration dependencies are documented.
- [ ] Batch jobs or scheduled processes are identified.
- [ ] File transfers are documented.
- [ ] Network dependencies are known.
- [ ] Identity and authentication dependencies are documented.
- [ ] Third-party vendor dependencies are identified.
- [ ] Reporting dependencies are documented.
- [ ] Operational dependencies are listed.
- [ ] Dependency owners are assigned.
- [ ] Dependency validation plan is defined.

Recommended dependency table:

| Dependency | Type | Owner | Criticality | Migration Impact | Validation Required |
|---|---|---|---|---|---|
|  | Application / Database / API / File / Network / Vendor |  | Critical / High / Medium / Low |  | Yes / No |

Dependency types to consider:

- Internal applications
- External applications
- Databases
- APIs
- Messaging or queues
- File shares
- ETL processes
- Reporting tools
- Authentication providers
- Firewalls
- DNS
- Certificates
- Monitoring tools
- Backup tools
- Vendors
- Business teams

## 5. Data and Integration Points

Data and integrations must be clearly understood before migration.

- [ ] Source data stores are identified.
- [ ] Target data stores are identified.
- [ ] Data volume is estimated.
- [ ] Data sensitivity is classified.
- [ ] Data retention requirements are documented.
- [ ] Data migration approach is defined.
- [ ] Data reconciliation approach is defined.
- [ ] Integration inventory is complete.
- [ ] API integrations are documented.
- [ ] File-based integrations are documented.
- [ ] Batch processing windows are reviewed.
- [ ] Integration owners are assigned.
- [ ] Integration validation criteria are defined.

Recommended integration fields:

| Field | Description |
|---|---|
| Integration name | Name or short description |
| Source system | System sending data |
| Target system | System receiving data |
| Pattern | API, file, batch, event, database, middleware |
| Frequency | Real-time, scheduled, daily, weekly, ad hoc |
| Criticality | Business impact if unavailable |
| Owner | Responsible team or person |
| Validation method | How integration success will be confirmed |

Key questions:

- What data moves in and out of the workload?
- Which integrations are business-critical?
- Are there hard-coded IP addresses, server names, or file paths?
- Are certificates or secrets involved?
- Are there firewall rules or allowlists to update?
- Are there batch windows that could be affected?
- How will successful data flow be validated after migration?

## 6. Security Considerations

Security must be reviewed before migration.

- [ ] Identity and access model is documented.
- [ ] Authentication approach is understood.
- [ ] Authorization model is documented.
- [ ] Privileged access requirements are reviewed.
- [ ] Secrets and credentials are identified.
- [ ] Sensitive data is classified.
- [ ] Encryption requirements are documented.
- [ ] Network security requirements are documented.
- [ ] Logging and audit requirements are known.
- [ ] Compliance requirements are reviewed.
- [ ] Security approval process is defined.
- [ ] Security risks are tracked.

Security areas to review:

- Identity and access management
- Role-based access control
- Network segmentation
- Firewall rules
- Private endpoints or connectivity requirements
- Secrets management
- Encryption at rest
- Encryption in transit
- Vulnerability management
- Security monitoring
- Audit logging
- Compliance obligations

## 7. Azure Landing Zone Readiness

Confirm whether the target Azure environment is ready to host the workload.

- [ ] Subscription strategy is defined.
- [ ] Resource group structure is defined.
- [ ] Naming standards are available.
- [ ] Tagging standards are available.
- [ ] Network topology is approved.
- [ ] Connectivity to on-premises is available, if required.
- [ ] Identity integration is ready.
- [ ] Security policies are configured.
- [ ] Monitoring baseline is available.
- [ ] Backup and recovery approach is defined.
- [ ] Cost management approach is defined.
- [ ] Governance controls are understood.
- [ ] Required Azure services are approved for use.

Landing zone areas to review:

| Area | Readiness Question |
|---|---|
| Identity | Are users, groups, roles, and access controls ready? |
| Network | Is connectivity, routing, firewall, and DNS ready? |
| Security | Are policies, monitoring, and controls ready? |
| Governance | Are naming, tagging, subscriptions, and management groups defined? |
| Operations | Is monitoring, backup, alerting, and support ready? |
| Cost | Is cost tracking and ownership defined? |

## 8. Operational Readiness

The migration should not only move technology. It should prepare operations.

- [ ] Support model is defined.
- [ ] Support team is identified.
- [ ] Monitoring approach is documented.
- [ ] Alerting approach is defined.
- [ ] Backup process is documented.
- [ ] Restore process is validated or planned.
- [ ] Incident process is defined.
- [ ] Escalation path is documented.
- [ ] Operational runbooks are prepared.
- [ ] Access management process is defined.
- [ ] Maintenance process is documented.
- [ ] Knowledge transfer is planned.
- [ ] BAU ownership is confirmed.

Operational readiness questions:

- Who will support the workload after migration?
- How will incidents be handled?
- What alerts matter?
- Who receives alerts?
- What runbooks are required?
- How will changes be managed after migration?
- What documentation must be handed over?

## 9. Monitoring and Observability

Confirm how the workload will be observed after migration.

- [ ] Application monitoring approach is defined.
- [ ] Infrastructure monitoring approach is defined.
- [ ] Logs are collected where needed.
- [ ] Alerts are defined.
- [ ] Dashboards are available or planned.
- [ ] Business-critical transactions are monitored.
- [ ] Integration monitoring is defined.
- [ ] Error reporting is available.
- [ ] Support team knows how to review operational signals.

Monitoring should help answer:

- Is the application available?
- Are critical transactions working?
- Are integrations processing correctly?
- Are errors increasing?
- Is performance within expectations?
- Are users affected?

## 10. Backup, Resiliency, and Recovery

Review the ability to recover from failure.

- [ ] Backup requirements are defined.
- [ ] Backup schedule is documented.
- [ ] Restore process is defined.
- [ ] Recovery time objective is documented.
- [ ] Recovery point objective is documented.
- [ ] Disaster recovery approach is defined.
- [ ] High availability requirements are documented.
- [ ] Resiliency expectations are reviewed.
- [ ] Recovery testing is planned.
- [ ] Business continuity impact is understood.

Key terms:

```text
RTO: Recovery Time Objective
RPO: Recovery Point Objective
```

## 11. Cutover Strategy

Define how the migration will move into production.

- [ ] Cutover window is defined.
- [ ] Cutover activities are documented.
- [ ] Cutover roles are assigned.
- [ ] Technical validation steps are defined.
- [ ] Business validation steps are defined.
- [ ] Communication plan is ready.
- [ ] Go / No-Go criteria are defined.
- [ ] Rollback criteria are defined.
- [ ] Hypercare plan is prepared.

Cutover overview:

```text
Pre-cutover readiness
      ↓
Go / No-Go decision
      ↓
Migration execution
      ↓
Technical validation
      ↓
Business validation
      ↓
Go-live confirmation
      ↓
Hypercare
```

## 12. Rollback Strategy

A rollback strategy protects the business if migration does not succeed.

- [ ] Rollback owner is defined.
- [ ] Rollback decision criteria are documented.
- [ ] Technical rollback steps are documented.
- [ ] Data rollback considerations are reviewed.
- [ ] Communication steps are documented.
- [ ] Maximum rollback decision time is defined.
- [ ] Business impact of rollback is understood.
- [ ] Rollback validation steps are defined.

Rollback may be considered if:

- Critical business process cannot be executed.
- Data migration fails validation.
- Integration failures block operations.
- Performance is unacceptable.
- Security control failure is identified.
- Production stability cannot be confirmed.
- Business owner does not accept the outcome.

## 13. Hypercare Plan

Hypercare should be planned before go-live.

- [ ] Hypercare start and end dates are defined.
- [ ] Support hours are documented.
- [ ] Hypercare lead is assigned.
- [ ] Support team is confirmed.
- [ ] Business validation checkpoints are defined.
- [ ] Issue triage process is ready.
- [ ] Escalation path is documented.
- [ ] Daily status cadence is agreed.
- [ ] Known issues process is defined.
- [ ] Exit criteria are documented.

Hypercare should include:

- Daily checkpoints
- Issue log
- Known issues list
- Business validation
- Technical monitoring
- Support escalation
- Executive updates when needed
- BAU transition preparation

## 14. BAU Handover

BAU means Business As Usual. It represents the normal operating model after migration and stabilization.

- [ ] BAU owner is identified.
- [ ] Support team accepts ownership.
- [ ] Runbooks are handed over.
- [ ] Monitoring documentation is shared.
- [ ] Known issues are transferred.
- [ ] Open actions are assigned.
- [ ] Escalation path is confirmed.
- [ ] Access and support processes are documented.
- [ ] Lessons learned are captured.
- [ ] Hypercare closure is approved.

BAU handover package should include:

- Final architecture notes
- Support runbook
- Monitoring and alerting notes
- Known issues
- Open actions
- Access model
- Backup and recovery notes
- Escalation path
- Vendor contacts, if applicable
- Business validation summary
- Lessons learned

## Migration Readiness Decision

Use this section to summarize readiness.

```text
Readiness decision:
Ready / Ready with conditions / Not ready

Key conditions:
Decision owner:
Decision date:
Next review:
```

## Recommended Readiness Criteria

Migration can proceed when:

- [ ] Application inventory is complete.
- [ ] Business criticality is understood.
- [ ] Dependencies are documented.
- [ ] Data and integrations are reviewed.
- [ ] Security considerations are addressed.
- [ ] Azure landing zone is ready.
- [ ] Operational support model is prepared.
- [ ] Monitoring and backup approach is defined.
- [ ] Cutover plan is ready.
- [ ] Rollback plan is ready.
- [ ] Hypercare plan is ready.
- [ ] BAU handover plan is defined.
- [ ] Business and technical owners approve readiness.

## Common Migration Risks

- Application dependencies are incomplete.
- Business criticality is underestimated.
- Network or firewall requirements are discovered late.
- Integrations fail after migration.
- Data validation is not clearly defined.
- Operational support model is not ready.
- Monitoring and alerting are missing.
- Rollback plan is not realistic.
- Hypercare is planned too late.
- BAU handover is incomplete.
- Cost ownership is unclear.
- Security approval is delayed.

## Recommended Artifacts

Useful artifacts for Azure migration readiness include:

- Application inventory
- Dependency map
- Current-state architecture
- Target-state architecture
- Migration strategy
- Security review
- Network connectivity plan
- Data migration plan
- Integration validation plan
- Cutover plan
- Rollback plan
- Hypercare plan
- BAU handover checklist
- Risk and issue log
- Executive status update

## Final Principle

A cloud migration is not only an infrastructure move.

It is a business and operational transition that requires architecture visibility, risk control, security review, cutover discipline, hypercare planning, and clean ownership transfer to BAU support.

## Related Microsoft Guidance

- Cloud Adoption Framework for Azure:
  https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/

- Plan your migration:
  https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/migrate/plan-migration

- Select cloud migration strategies:
  https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/plan/select-cloud-migration-strategy

- Azure Well-Architected Framework:
  https://learn.microsoft.com/en-us/azure/well-architected/
