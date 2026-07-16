# ADR-002: Migrate a Business-Critical Workload to Microsoft Azure Landing Zone

## Status

Accepted

## Context

A business-critical workload is currently hosted in an on-premises environment.

The current platform has limitations related to scalability, availability, operational resilience, and infrastructure flexibility. The organization needs to improve platform reliability and support future growth while maintaining business continuity during the transition.

The workload has dependencies with applications, databases, integrations, reports, infrastructure components, identity services, and business operations.

The migration must avoid unnecessary business disruption and should include readiness assessment, dependency validation, cutover planning, rollback strategy, hypercare support, and BAU handover.

## Decision

The workload will be migrated from the on-premises environment to a Microsoft Azure Landing Zone using a controlled and phased migration approach.

The migration will include:

- Application inventory
- Business criticality assessment
- Dependency mapping
- Data and integration review
- Security review
- Azure Landing Zone readiness validation
- Cutover planning
- Rollback planning
- Hypercare support
- BAU handover

The migration will not be executed as a blind lift-and-shift without readiness validation.

## Rationale

A phased and controlled migration approach reduces operational risk and improves visibility before go-live.

Using an Azure Landing Zone provides a structured target environment where identity, networking, governance, security, monitoring, and operational practices can be reviewed before onboarding the workload.

This approach supports:

- Better availability
- Improved scalability
- Operational resilience
- Clearer support model
- Better monitoring and governance
- Reduced cutover risk
- Improved stakeholder confidence

## Alternatives Considered

### Keep the workload on-premises

Rejected because it does not address current scalability, availability, and resilience limitations.

It may also continue increasing operational complexity and infrastructure dependency.

### Big-bang migration

Rejected because moving all components at once increases the risk of downtime, missed dependencies, and business disruption.

This option may be faster on paper, but riskier in execution.

### Basic lift-and-shift without readiness assessment

Rejected because it may move existing problems to the cloud without addressing dependency, security, operational, or support readiness.

### Controlled phased migration to Azure Landing Zone

Accepted because it balances speed, control, architecture visibility, risk reduction, and business continuity.

## Decision Drivers

The decision was influenced by the following drivers:

- Business continuity
- Availability improvement
- Scalability needs
- Operational resilience
- Security and governance requirements
- Dependency visibility
- Cutover risk reduction
- Support model readiness
- Long-term maintainability

## Quality Attributes Impacted

| Quality Attribute | Expected Impact |
|---|---|
| Reliability | Improved resilience and recovery options |
| Scalability | Better ability to grow compute, storage, or platform capacity |
| Security | Opportunity to strengthen identity, access, network, and monitoring controls |
| Operational excellence | Better monitoring, support model, and BAU handover |
| Performance efficiency | Opportunity to right-size resources and review bottlenecks |
| Cost management | Requires cost visibility, ownership, and governance |
| Maintainability | Improved documentation, ownership, and operational practices |

## Consequences

## Positive Consequences

- Better platform scalability
- Improved availability options
- More structured operational model
- Better monitoring and alerting possibilities
- Stronger governance and ownership
- Reduced dependency on legacy infrastructure
- Improved readiness for future modernization

## Negative Consequences

- Migration requires planning and coordination.
- Teams need Azure operational knowledge.
- Cutover planning must be carefully managed.
- Some application dependencies may require remediation.
- Costs must be monitored and governed.
- BAU support teams require knowledge transfer.

## Risks

- Hidden dependencies may be discovered late.
- Network or firewall changes may delay validation.
- Integrations may fail after migration.
- Data validation may take longer than expected.
- Security approvals may delay cutover.
- Business users may be unavailable for validation.
- Rollback may be complex if data changes occur after cutover.
- Support team may not be ready for BAU ownership.

## Risk Mitigation

| Risk | Mitigation |
|---|---|
| Hidden dependencies | Complete dependency mapping and validation |
| Integration failure | Prepare integration validation checklist |
| Business disruption | Plan cutover window and business validation |
| Security delay | Start security review early |
| Rollback complexity | Define rollback criteria and decision deadline |
| Operational support gap | Prepare runbooks and BAU handover |
| Cost uncertainty | Define cost ownership and monitoring approach |

## Implementation Notes

Recommended implementation stages:

```text
Discovery
      ↓
Readiness assessment
      ↓
Target architecture review
      ↓
Landing zone validation
      ↓
Migration planning
      ↓
Non-production migration
      ↓
Testing and validation
      ↓
Production cutover
      ↓
Hypercare
      ↓
BAU handover
```

## Follow-up Actions

- Complete application inventory.
- Confirm business criticality.
- Document application dependencies.
- Review data and integration points.
- Validate Azure Landing Zone readiness.
- Confirm security and compliance requirements.
- Prepare cutover plan.
- Prepare rollback plan.
- Define hypercare support window.
- Prepare BAU handover package.
- Capture lessons learned after migration.

## Architecture Review Checklist

Before final approval, review:

- Current-state architecture
- Target-state architecture
- Dependency map
- Security model
- Network connectivity
- Identity and access model
- Monitoring and alerting
- Backup and recovery
- Cutover plan
- Rollback plan
- Support model
- BAU handover plan

## Decision Outcome

The migration can proceed when readiness criteria are met and both business and technical owners approve the cutover plan.

The migration should not proceed if critical dependencies, security requirements, rollback strategy, or operational ownership remain unclear.

## Related Documentation

- Azure migration readiness checklist
- Application inventory
- Dependency map
- Cutover plan
- Rollback plan
- Hypercare plan
- BAU handover checklist

## Privacy Notice

This ADR is a fictional and sanitized example created for portfolio documentation purposes.

It does not include private company data, customer information, real system names, credentials, financial details, network details, or sensitive operational information.
