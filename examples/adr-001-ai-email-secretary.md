# ADR-001: Use a Human-in-the-Loop Approach for AI-Generated Email Responses

## Status

Accepted

## Context

The AI Email Secretary project generates email summaries, priority classifications, and draft responses.

Because email communication can involve sensitive information, business context, tone, and personal judgment, fully automated sending could introduce risk.

The project needs to improve productivity while keeping the user in control of final communication.

## Decision

The system will use a human-in-the-loop approach.

AI can suggest classifications, summaries, actions, and draft responses, but the user must review and approve any final action.

The system will not send emails automatically.

## Rationale

This approach balances productivity with control.

It reduces manual workload while keeping final decisions under human supervision.

It also supports responsible AI usage by treating AI output as a recommendation instead of a final decision.

## Alternatives Considered

### Fully automated email sending

Rejected because it increases the risk of sending incorrect, incomplete, or inappropriate responses.

It also creates privacy, tone, and accountability concerns.

### Manual-only email review

Rejected because it does not address the productivity problem.

It keeps full human control, but does not reduce manual review time.

### Human-in-the-loop workflow

Accepted because it improves efficiency while keeping the user responsible for final decisions.

## Consequences

### Positive Consequences

- Reduces manual review time
- Keeps user control over final responses
- Supports responsible AI usage
- Reduces risk of incorrect communication
- Improves visibility of priority emails
- Helps standardize draft responses

### Negative Consequences

- Requires human review
- Does not fully automate the workflow
- May require additional validation steps
- AI suggestions may still need correction

## Risks

- AI-generated summaries may miss important context.
- Suggested responses may require tone or content adjustment.
- Sensitive information must be protected.
- Users may over-trust AI-generated output.
- Prompt design may influence output quality.

## Follow-up Actions

- Add clear review steps.
- Use fictional or sanitized sample data.
- Document privacy considerations.
- Avoid automatic email sending.
- Add examples of expected outputs.
- Document limitations and improvement opportunities.

## Related Documentation

- Project AI Email Secretary repository
- Notebook summary
- Privacy notice
- Responsible AI approach
