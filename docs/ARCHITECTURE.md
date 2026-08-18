# Architecture

## Components

| Component | Responsibility | Trust consideration |
| --- | --- | --- |
| Teams or Microsoft 365 Copilot | Authenticated conversation channel | Confirm the signed-in identity is available to downstream controls |
| Copilot Studio agent | Intent routing, response policy, and answer composition | Prompt rules guide behavior but are not an authorization boundary |
| Approved knowledge sources | Organization-specific safety procedures | Preserve document permissions and review freshness |
| Public regulatory sources | Supplemental regulatory context | Cite clearly and do not let them silently override local policy |
| SharePoint certification list | Certification status and expiration dates | Restrict rows and fields through platform permissions or a controlled API |
| Escalation path | Routes emergencies and uncertainty to local help | Use reviewed, location-specific contacts in the private deployment |

## Request Flow

1. The channel authenticates the user.
2. The agent classifies the request as safety guidance, certification status, equipment inventory, general conversation, or escalation.
3. Safety questions retrieve from approved documents first and public sources second.
4. Certification questions call the controlled data source, apply authorization, and then filter for the requested person or equipment.
5. The response cites its source, labels uncertainty, and surfaces expired status when relevant.
6. Urgent or insufficiently grounded requests are routed to the organization's reviewed emergency or safety process.

## Authorization Boundary

The model must receive only data the signed-in user is authorized to see. Team filtering written in a prompt is useful defense in depth, but it cannot replace SharePoint permissions, row-level filtering in a connector, or a policy-enforcing API.

## Failure Modes To Test

- Connector unavailable or returns a partial page
- Missing, stale, duplicated, or conflicting certification records
- Similar employee names and identity ambiguity
- User asks for another team's records
- Knowledge source does not contain the requested procedure
- Public guidance conflicts with approved local policy
- Emergency language is vague or the local contact is unavailable
- Prompt injection appears inside a document or data field

