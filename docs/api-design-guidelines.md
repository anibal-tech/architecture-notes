# API Design Guidelines

## Purpose

This document provides lightweight guidelines for designing APIs that are clear, consistent, secure, and easy to maintain.

The goal is to support communication between systems while keeping business rules, data contracts, and technical responsibilities understandable.

## Design Principles

Good APIs should be:

- Clear
- Consistent
- Predictable
- Secure
- Versioned when needed
- Easy to document
- Easy to test
- Aligned with business use cases

## Resource Naming

Use nouns for resources.

Examples:

```text
/emails
/users
/tasks
/reports
```

Avoid action-based names when a resource-based name is clearer.

Less preferred:

```text
/getEmails
/createTask
/sendReport
```

Preferred:

```text
GET /emails
POST /tasks
POST /reports
```

## HTTP Methods

Use HTTP methods according to their intent:

```text
GET     Retrieve information
POST    Create a new resource or trigger a process
PUT     Replace a resource
PATCH   Update part of a resource
DELETE  Remove a resource
```

## Example Endpoints

```text
GET /emails
GET /emails/{email_id}
POST /emails/{email_id}/analysis
POST /emails/{email_id}/draft-response
GET /reports/email-priority
```

## Request Example

```json
{
  "email_id": "email-001",
  "subject": "Project deadline update",
  "body": "Could you confirm the delivery date for the pending report?"
}
```

## Response Example

```json
{
  "email_id": "email-001",
  "priority": "High",
  "summary": "The sender is requesting confirmation of a delivery date.",
  "suggested_action": "Prepare follow-up response",
  "human_review_required": true
}
```

## Error Handling

Error responses should be clear and consistent.

Example:

```json
{
  "error": {
    "code": "INVALID_REQUEST",
    "message": "The email body is required."
  }
}
```

## Security Considerations

APIs should consider:

- Authentication
- Authorization
- Input validation
- Rate limiting
- Sensitive data protection
- Logging without exposing private information

## Documentation Checklist

API documentation should include:

- Endpoint path
- HTTP method
- Purpose
- Request example
- Response example
- Error examples
- Authentication requirements
- Business rules
- Known limitations

## Final Principle

An API is a contract between systems.

A good API should be easy to understand by both technical teams and business stakeholders.
