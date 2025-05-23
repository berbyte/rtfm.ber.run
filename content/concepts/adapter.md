---
title: BERAdapter
diataxis: explanation
prev: BERAgent
next: tutorials
weight: 3
---

## Summary
The `BERAdapter` is a core module of `BER`. The module connects the `BER` server with popular project management platforms e.g. GitHub or Jira; company messaging platforms, like Slack. This makes `BER` platform agnostic and easy to extend.

It is a tool that by implementing 3rd-party APIs, adds control of `BERAgents` to a platform users are already familiar with. `BERAdapters` make `@ber` instantly available across your workspaces.

{{< cards cols="1" >}}
  {{< card link="/diagrams/ber-003-adapter.svg" title="BERAdapter: Universal Integration Through Webhooks and REST APIs" image="/diagrams/ber-003-adapter.svg" subtitle="BERAdapter uses webhooks to receive requests and REST APIs to send responses, enabling seamless integration with any platform supporting these standard protocols" >}}
{{< /cards >}}

## Features
The role of the module is to enable frictionless communication between the user and `BER`. This component is used for task discussion and remote task execution. Configuration about how to select `BERAgents` can also be communicated here.

All commands and instructions are in natural language. All of the input fields such as attachments can be used to enrich the text.

When remote tasks are executed, and external systems are affected the `BERAdapter` can display and accept special forms. Every special form takes precedence over natural language input. This separate format gives control and oversight to the user, similar to having draft, preview or `--dry-run` abilities.

Find practical, detailed examples in our tutorial about BERAdapter for GitHub
{{< cards >}}
  {{< card link="/tutorials/github" title="BERAdapter" icon="sparkles" >}}
{{< /cards >}}

### Inputs
To receive user inputs `BERAdapters` have API endpoints that can be used as webhooks. In the general form, the input can be natural language and structured data. In the special form, the input is a formal command, such as approving or rejecting an external change or configuring settings.

### Outputs
The output is always received on the same `BERAdapter` where the input was sent.

Depending on where the response comes from, an external system or a `BERAgent` the structure of the output is different.

The output event is skipped by the same `BERAdapter` to prevent infinite reaction-cycles.

### Comparative chart

| User Intent | Input                                  | Output                                                 |
|:-----------:|:--------------------------------------:|:------------------------------------------------------:|
| *Action*      | `{ approval, rejection } <TASK_HASH>` | external system response                               |
| *Discussion*  | free-form natural language             | templated, structured, Agent-generated natural language |
| *Selection*   | `{ label, similarity }`               | templated, structured, Agent-generated natural language |
