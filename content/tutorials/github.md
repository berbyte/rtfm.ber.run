---
title: GitHub Adapter Setup
weight: 3
prev: /tutorials/agent
next: /tutorials/tui
sidebar:
  open: true
---


## Overview
You will learn how to enable `BER` for the GitHub platform. A bot will be running in your selected repository following all events.

### Integration
The `BER` GitHub Adapter takes the form of a GitHub application. Follow our [GitHub App setup guide](/guides/howto-adapter-github-install) to create and configure a new GitHub Application. This adapter allows any GitHub account, organisation, repository to talk with different `BERAgents`.


## Inputs
### Label-Based Direct Selection
It can look for issue labels added on issues that follow a specific schema.

### Direct Mention in Comment Field
With any direct mention `@ber` in an issue (or discussion [or comment]).

### Event Types
The BER system primarily processes GitHub events as input signals:
- **Issue Comments**: Natural language requests prefixed with "@ber"
- **Issue Creation**: Initial problem statements and documentation requests
- **Issue Events**: Added or removed `Labels` call the attached `BERAgent`
- **Installation Events**: System setup and initialization triggers

### Input Rules and Workflow
Messages flow through a validation pipeline:
1. Author verification (skip bot messages)
2. Intent detection ("@ber" mentions)
3. Content extraction (body parsing)

## Outputs
 - Natural language
 - Templated, structured response
 - Visualisation

## Examples
 - Go to an issue and add a label following the schema `Agent:ProductOwner`.
 - Open an issue and mention BER as `@ber` and describe what agent you want to employ and which skill is needed for your task.
