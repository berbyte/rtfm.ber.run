---
title: GitHub Adapter Setup
weight: 3
type: docs
diataxis: tutorial
prev: /tutorials/agent
next: /tutorials/tui
sidebar:
  open: true
---

## Overview
You will learn how to enable `BER` for the GitHub platform. This adapter allows any GitHub account, organisation, repository to talk with different `BERAgents`. A bot will be running in your selected repository parsing select events.

Refer to the concept of `BERAdapters` connecting you and `BER`:
{{< cards >}}
  {{< card link="/concepts/adapter" title="BERAdapter" icon="sparkles" >}}
{{< /cards >}

 In this tutorial we demonstrate how to create a GitHub app, so BER can be reached from your repository.
 
## Installing and Authorization

1. Navigate to [GitHub's New App Registration page](https://github.com/settings/apps/new)
2. Copy the settings from the screenshot:

{{< cards cols="1" >}}
  {{< card link="/images/ber-github-app.png" title="GitHub App Settings" image="/images/ber-github-app.png" subtitle="Screenshot showing the required settings for creating a BER GitHub app" >}}
{{< /cards >}}


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
