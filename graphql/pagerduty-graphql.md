# PagerDuty GraphQL Schema

## Overview

PagerDuty is a digital operations management platform providing incident management, on-call scheduling, and automated alerting for engineering and operations teams. This conceptual GraphQL schema represents PagerDuty's domain model as derived from the PagerDuty REST API v2.

PagerDuty's public API is REST-based. This GraphQL schema is a conceptual representation of the PagerDuty data model and capabilities, intended for teams exploring API design patterns, building GraphQL wrappers, or evaluating the PagerDuty domain.

- **Developer Portal**: https://developer.pagerduty.com/
- **REST API Reference**: https://developer.pagerduty.com/api-reference/
- **REST API Getting Started**: https://developer.pagerduty.com/docs/rest-api-v2/rest-api/
- **Authentication**: https://developer.pagerduty.com/docs/authentication
- **GitHub Organization**: https://github.com/PagerDuty

## Core Domain Areas

### Incident Management

Incidents are the central entity in PagerDuty. They track triggered alerts, acknowledgments, notes, log entries, and resolutions. Incidents are linked to services, escalation policies, and teams.

### On-Call and Scheduling

Schedules define who is on-call at any given time via layers, overrides, and restrictions. Escalation policies route incidents through ordered rules until acknowledged or resolved.

### Services and Integrations

Services represent a logical component being monitored. Each service has integrations (email, webhook, generic events) that ingest alerts. Service dependencies model inter-service relationships.

### Event Orchestration

Event Orchestrations provide advanced routing, enrichment, and suppression of inbound events before they become incidents. Rulesets (legacy) and orchestration pipelines route events to services or suppression.

### Users and Teams

Users have contact methods (email, SMS, phone, push) and notification rules that define how and when they are paged. Teams group users and can own services, escalation policies, and schedules.

### Webhooks and Extensions

Webhooks v3 deliver signed outbound notifications for incident lifecycle events. Extensions connect PagerDuty to external ticketing and communication tools via extension schemas.

### Analytics

The Analytics API exposes aggregated incident metrics, MTTA/MTTR, on-call load, and team performance data.

### Status Pages and Business Services

Business Services represent customer-facing capabilities. Status Pages communicate operational status to external stakeholders.

## Authentication

PagerDuty uses token-based authentication. REST API requests include an `Authorization: Token token=<API_KEY>` header. OAuth 2.0 is available for third-party integrations.

**Rate Limits**:
- REST API: 960 requests/minute per token
- Analytics API: 5 requests/minute per token
- Events API: 480 events/minute per integration key

## Schema File

See `pagerduty-schema.graphql` for the full conceptual type definitions.
