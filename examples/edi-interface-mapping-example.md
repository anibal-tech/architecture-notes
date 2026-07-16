# EDI Interface Mapping Example

## Purpose

This document provides a fictional and sanitized example of an EDI interface mapping for enterprise integration validation.

The example focuses on a purchase order integration between an external customer, an EDI gateway, middleware, and an ERP system such as SAP R/3.

This example is intended for architecture and delivery documentation purposes. It does not represent a real company, real partner, real customer, or real production interface.

## Example Scenario

A customer sends purchase orders through an EDI gateway.

The integration flow receives the customer purchase order, validates the message, maps partner fields to internal fields, and creates a sales order in the ERP system.

## High-Level Flow

```text
Customer System
      ↓
Customer EDI Gateway
      ↓
Integration Middleware
      ↓
ERP System
      ↓
Sales Order Created
      ↓
Acknowledgment / Error Response
```

## Interface Summary

| Field | Value |
|---|---|
| Interface name | Customer Purchase Order Inbound |
| Business document | Purchase Order |
| Direction | Inbound |
| Source system | Customer EDI Gateway |
| Target system | ERP System |
| Middleware | Integration Middleware |
| Format | EDI X12 850 / Internal mapped structure |
| Transport | SFTP or AS2 |
| Frequency | Multiple times per day |
| Business owner | Order Management Lead |
| Technical owner | Integration Lead |
| ERP owner | ERP Application Owner |
| Support owner | Application Support Team |

## Source and Target

| Area | Description |
|---|---|
| Source system | External customer system through EDI gateway |
| Target system | ERP system for sales order creation |
| Source owner | Customer or partner integration contact |
| Target owner | ERP application owner |
| Integration owner | Middleware or integration team |
| Business process | Customer order intake |
| Expected outcome | Sales order created or transaction rejected with clear error |

## Example Business Rules

- Purchase order number must be present.
- Customer identifier must be mapped to an internal customer account.
- Ship-to location must be valid.
- Material or item code must be mapped to an internal material number.
- Quantity must be greater than zero.
- Unit of measure must be valid.
- Requested delivery date must be valid.
- Duplicate purchase orders must not create duplicate sales orders.
- Invalid transactions must be routed to an error queue.
- Failed transactions must be traceable and reprocessable.

## Example Field Mapping

| Source Field | Source Description | Target Field | Target Description | Required | Transformation / Mapping Rule | Validation Rule |
|---|---|---|---|---|---|---|
| BEG03 | Purchase order number | VBAK-BSTNK | Customer purchase order reference | Yes | Copy source value | Must not be empty and must be unique |
| BEG05 | Purchase order date | VBAK-AUDAT | Document date | Yes | Convert YYYYMMDD to target date format | Must be valid date |
| N1-ST | Ship-to party code | VBPA-KUNNR | Ship-to customer | Yes | Map external ship-to code to internal customer number | Must exist in customer master |
| N1-BT | Bill-to party code | VBPA-KUNNR | Bill-to customer | Yes | Map external bill-to code to internal customer number | Must exist in customer master |
| PO101 | Line item number | VBAP-POSNR | Sales order item number | Yes | Convert to target item numbering | Must be numeric |
| PO107 | Customer item code | VBAP-MATNR | Material number | Yes | Map customer item to internal material | Must exist in material master |
| PO102 | Ordered quantity | VBAP-KWMENG | Order quantity | Yes | Copy numeric value | Must be greater than zero |
| PO103 | Unit of measure | VBAP-VRKME | Sales unit | Yes | Convert partner UOM to internal UOM | Must be valid unit |
| CTT01 | Total line count | Control total | Line count validation | Yes | Compare with number of detail lines | Must match detail line count |
| REF02 | Customer reference | VBAK-IHREZ | Customer reference | No | Copy source value | Optional |

## Example Code Conversions

| Source Value | Target Value | Description |
|---|---|---|
| EA | Each | Unit of measure conversion |
| CS | Case | Unit of measure conversion |
| CUSTOMER-001 | 1000001 | Customer account mapping |
| SHIP-001 | 2000001 | Ship-to mapping |
| ITEM-A100 | MAT-100 | Material mapping |
| ITEM-B200 | MAT-200 | Material mapping |

## Required Fields

Required header fields:

- Purchase order number
- Purchase order date
- Customer identifier
- Ship-to party
- Bill-to party

Required line fields:

- Line item number
- Item or material code
- Quantity
- Unit of measure

Required control fields:

- Transaction identifier
- Partner identifier
- Line count or control total

## Validation Rules

| Rule ID | Rule | Error Handling |
|---|---|---|
| VAL-001 | Purchase order number is required | Reject transaction |
| VAL-002 | Duplicate purchase order is not allowed | Reject duplicate transaction |
| VAL-003 | Customer identifier must exist | Route to business correction |
| VAL-004 | Ship-to location must be valid | Route to business correction |
| VAL-005 | Material mapping must exist | Route to master data correction |
| VAL-006 | Quantity must be greater than zero | Reject transaction |
| VAL-007 | Unit of measure must be valid | Route to mapping correction |
| VAL-008 | Line count must match detail lines | Reject transaction |
| VAL-009 | Requested delivery date must be valid | Route to business correction |

## Error Handling Matrix

| Error Type | Example | Owner | Resolution Path |
|---|---|---|---|
| Format error | Invalid EDI structure | EDI provider / Integration team | Correct file format and resend |
| Mapping error | Partner UOM not mapped | Integration team | Add mapping and reprocess |
| Master data error | Unknown material | Master data team | Create or correct master data |
| Business rule error | Quantity is zero | Business owner | Correct transaction and resend |
| Duplicate error | PO already processed | Support team / Business owner | Validate duplicate and reject or close |
| Connectivity error | File not received | Infrastructure / EDI provider | Restore connection and resend |

## Reprocessing Process

Recommended reprocessing flow:

```text
Transaction fails validation
      ↓
Error is logged
      ↓
Owner is assigned
      ↓
Business or technical correction is completed
      ↓
Transaction is reprocessed
      ↓
Target document is validated
      ↓
Issue is closed
```

Reprocessing considerations:

- Do not reprocess without understanding the original error.
- Confirm whether the transaction already created a target document.
- Prevent duplicate sales orders.
- Keep an audit trail of corrections.
- Confirm successful processing with business users when needed.

## UAT Scenarios

| Scenario ID | Scenario | Expected Result |
|---|---|---|
| UAT-001 | Valid purchase order with one line | Sales order is created successfully |
| UAT-002 | Valid purchase order with multiple lines | Sales order is created with correct line items |
| UAT-003 | Missing purchase order number | Transaction is rejected with clear error |
| UAT-004 | Unknown customer identifier | Transaction is routed to business correction |
| UAT-005 | Unknown material code | Transaction is routed to master data correction |
| UAT-006 | Invalid quantity | Transaction is rejected |
| UAT-007 | Duplicate purchase order | Duplicate is prevented |
| UAT-008 | Partner UOM conversion | Target UOM is mapped correctly |
| UAT-009 | Reprocess corrected transaction | Sales order is created successfully |
| UAT-010 | Integration acknowledgment | Confirmation or error response is generated |

## Cutover Checklist

Before go-live:

- [ ] Partner test completed.
- [ ] EDI gateway connectivity validated.
- [ ] Middleware route configured.
- [ ] ERP target configuration confirmed.
- [ ] Mapping reviewed and approved.
- [ ] Master data loaded or validated.
- [ ] Error handling process tested.
- [ ] Reprocessing process tested.
- [ ] UAT sign-off completed.
- [ ] Support contacts confirmed.
- [ ] Hypercare window defined.
- [ ] Business owner approves go-live.
- [ ] Technical owner approves go-live.

## Hypercare Monitoring

During hypercare, monitor:

- Number of purchase orders received
- Number of purchase orders processed successfully
- Number of failed transactions
- Mapping errors
- Master data errors
- Duplicate purchase orders
- Reprocessed transactions
- Average time to resolve failed transactions
- Business-impacting errors

## Ownership Summary

| Area | Owner |
|---|---|
| Business process | Order Management Lead |
| Source system | Customer or partner integration contact |
| Integration middleware | Integration Lead |
| ERP processing | ERP Application Owner |
| Master data | Master Data Team |
| Error monitoring | Application Support Team |
| Reprocessing | Application Support Team with business approval |
| UAT sign-off | Business Owner |
| Go-live approval | Business Owner and Technical Owner |

## Acceptance Criteria

The interface can be considered ready when:

- [ ] Source and target systems are confirmed.
- [ ] Field mapping is approved.
- [ ] Required fields are validated.
- [ ] Error handling is tested.
- [ ] Reprocessing process is tested.
- [ ] UAT scenarios are passed or formally accepted.
- [ ] Business owner approves results.
- [ ] Technical owner approves readiness.
- [ ] Support model is ready.
- [ ] Hypercare monitoring is active.

## Privacy Notice

This example uses fictional and sanitized data only.

It does not include real partner names, customer numbers, material numbers, system names, credentials, file paths, network details, business volumes, financial information, or sensitive operational data.
