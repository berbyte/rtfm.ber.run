---
title: BER Adapter
diataxis: explanation
prev: documentation/agent
next: documentation/glossary
weight: 4
---

## Summary

The `BER Adapter` is client-facing interface that is implemented for any system that has a method to communicate real-world input with a `BER Agent`. An adapter is defined for a specific interface which may be a platform e.g. Github; or Jira.

For input, the `BER Adapter` relies on webhooks and for output it integrates with the service's REST API endpoint.

[![BER's Pluggable Adapter System](/diagrams/ber-003-adapter.svg)](/diagrams/ber-003-adapter.svg)


## Integrations
### GitHub

The BER GitHub Adapter takes the form of a GitHub application that you can install from the marketplace or through our launch site. This adapter allows any GitHub account, organisation, repository to talk with different BERAgents. It can look for issue `labels` that follow a specific schema, it reacts to any mention in an issue or discussion or comment. When installed it runs in the background on each new issue to update its context.

#### Inputs
The BER system primarily processes GitHub events as input signals:

- **Issue Comments**: Natural language requests prefixed with "@ber"
- **Issue Creation**: Initial problem statements and documentation requests
- **Issue Events**: Added or removed `labels` call the attached `BERAgent`
- **Installation Events**: System setup and initialization triggers


#### Adapter rules for understanding intent
Messages flow through a validation pipeline:
1. Author verification (skip bot messages)
2. Intent detection ("@ber" mentions)
3. Content extraction (body parsing)

#### Outputs
 - Natural language
 - Templated, structured response
 - Visualisation

## Examples
 - Go to an issue and add a label following the schema `Agent:ProductOwner:Estimate`
 - Open an issue and mention BER as `@ber` and describe what agent you want to employ and which skill is needed for your task
