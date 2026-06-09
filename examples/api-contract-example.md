# API Contract Example

## Purpose

This document provides a lightweight API contract example for an AI-assisted email analysis workflow.

The goal is to show how an API can be documented clearly enough for business and technical review.

## Endpoint

```text
POST /email-analysis
```

## Description

Analyzes an email and returns a priority classification, summary, suggested action, and draft response for human review.

## Request Body

```json
{
  "email_id": "email-001",
  "sender": "client@example.com",
  "subject": "Project deadline update",
  "body": "Could you confirm the delivery date for the pending report?"
}
```

## Response Body

```json
{
  "email_id": "email-001",
  "priority": "High",
  "intent": "Delivery confirmation request",
  "summary": "The sender is asking for confirmation of the delivery date for a pending report.",
  "suggested_action": "Prepare a follow-up response with the expected delivery date.",
  "draft_response": "Hello, thank you for your message. I will confirm the expected delivery date and follow up with you shortly.",
  "human_review_required": true
}
```

## Validation Rules

- `email_id` is required.
- `subject` is recommended.
- `body` is required.
- Sensitive information should not be logged.
- The system should not send the draft response automatically.

## Error Example

```json
{
  "error": {
    "code": "MISSING_EMAIL_BODY",
    "message": "The email body is required for analysis."
  }
}
```

## Responsible AI Notes

The API response should be treated as a suggestion.

A human user must review the summary, priority, suggested action, and draft response before taking any final action.

## Security and Privacy Notes

- Do not expose API keys.
- Do not store private email data unnecessarily.
- Avoid logging sensitive email content.
- Use fictional or sanitized data in public examples.
- Apply access controls when connected to real email systems.

## Status

Example contract for documentation purposes.
