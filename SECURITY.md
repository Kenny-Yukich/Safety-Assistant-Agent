# Security Policy

## Reporting A Concern

Please do not open a public issue for a suspected credential, personal-data, or tenant-information exposure. Use GitHub's private vulnerability reporting feature for this repository instead.

## Deployment Guidance

- Store credentials in the target platform's managed connection system, never in repository files.
- Enforce employee-data authorization in SharePoint, the connector, or an API layer. Do not rely on model instructions as the only control.
- Apply least-privilege permissions and test with accounts from different roles and teams.
- Treat agent transcripts and telemetry as potentially sensitive records.
- Keep internal policies, employee records, emergency contacts, and tenant identifiers outside public source control.
- Have qualified personnel approve safety-critical content before production use.

This repository contains illustrative configuration only and is not connected to a live environment.

