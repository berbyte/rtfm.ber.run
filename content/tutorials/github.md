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
You will learn how to enable `BER` for the GitHub platform. This adapter allows any GitHub account, organisation, repository to talk with different `BERAgents`. A bot will be running in your selected repository to help you run tasks.

Refer to the concept of `BERAdapters` and how it is connecting you and `BER`:
{{< cards >}}
  {{< card link="/concepts/adapter" title="BERAdapter" icon="sparkles" >}}
{{< /cards >}}

 In this tutorial we demonstrate how to create a GitHub app, so `BER` can be reached from your repository. Then we show simple options and commands to control `BER` from GitHub.

## Installation

Navigate to [GitHub's New App Registration page](https://github.com/settings/apps/new) and enter your configurations and settings as follows.

### Register new GitHub App
 | Field name          | Field value       |
 |:-------------------:|:-----------------:|
 | **GitHub App name** | `BER-test`        |
 | **Write**           | `BER rulez`       |
 | **Homepage URL**    | `https://ber.run` |

### Webhook
  | Field name      | Field value                  |
  |:---------------:|:----------------------------:|
  | **Active**      | [x]                          |
  | **Webhook URL** | `https://<YOUR_WEBHOOK_URL>` |
  | **Secret**      | `sUpEr-Str0nG-S3cr3t-!!@`    |

### Permissions
  | Field name   | Field value              |
  |:------------:|:------------------------:|
  | **Issues**   | `Access: Read and write` |
  | **Metadata** | `Access: Read-only`      |

### Subscribe to events
  | Field name        | Field value |
  |:-----------------:|:-----------:|
  | **Issues**        | [x]         |
  | **Sub issues**    | [x]         |
  | **Meta**          | [x]         |
  | **Issue comment** | [X]         |
  | **Label**         | [x]         |
  | **Milestone**     | [x]            |


Follow our visual cheatsheet for highlighted instructions in image format

{{< cards >}}
  {{< card link="/references/images" title="Images"  >}}
{{< /cards >}}

## Commands
Learn more about how you can use the `BERAdapter` for GitHub.

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

## Examples
Look at usecases and how `BER` stays out of the way

{{< cards >}}
  {{< card link="/getting-started/usecases" title="Explore BER in Action" icon="sparkles" >}}
{{< /cards >}}
