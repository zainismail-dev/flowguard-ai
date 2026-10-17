# FlowGuard AI: Automation Failure Detective

FlowGuard AI is a rule-based automation failure diagnosis prototype built with n8n. It receives error reports through a webhook, validates incoming data, classifies common HTTP errors, and recommends troubleshooting actions.

## Features

- Webhook-based incident intake
- Input validation and conditional routing
- Rule-based error classification
- Recommended troubleshooting actions
- Structured JSON diagnostic responses
- HTTP response handling for valid and invalid inputs

## How It Works

1. **Receive Error Report:** Accepts incoming HTTP POST requests.
2. **Validate Input:** Checks required incident fields.
3. **Conditional Routing:** Sends valid reports to diagnosis and invalid reports to an error response.
4. **Diagnose Incident:** Applies predefined rules to identify likely causes and recommend actions.
5. **Return Diagnosis:** Responds with structured JSON containing the diagnosis and recommendations.

## Supported Error Types

| HTTP Status | Classification |
|---|---|
| 401 | Authentication |
| 403 | Permission |
| 404 | Resource Not Found |
| 429 | Rate Limit |
| 5xx | Server Error |

Additional rules handle timeout messages and missing required fields.

## Example Use Case

A Shopify order synchronization workflow fails because of an invalid API access token. FlowGuard receives the incident report, classifies it as an authentication error, and recommends checking or reconnecting the credential.

## Testing

The prototype has successfully completed the following tests:

- **HTTP 429:** Tested rate limit diagnosis using mock data.
- **HTTP 401:** Tested authentication diagnosis using mock data.
- **Real HTTP POST:** Sent a request through Hoppscotch to the n8n test webhook and received a structured diagnostic response.

## Technology Stack

- **n8n:** Workflow automation
- **Webhooks and HTTP:** Request and response handling
- **JSON:** Structured data exchange
- **JavaScript:** Validation and diagnostic rules
- **Hoppscotch:** API testing

## Current Limitations

- Diagnoses use predefined rules rather than an AI model.
- Suggested root causes are not independently verified.
- Persistent incident storage is not implemented.
- A dashboard and user authentication are not implemented.
- Automatic monitoring of Shopify or CRM systems is not implemented.

## Future Improvements

- Persistent incident history
- Additional validation and error handling tests
- Incident dashboard and recurring error analysis
- Optional
