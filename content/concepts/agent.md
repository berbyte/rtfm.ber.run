---
title: BERAgent
diataxis: explanation
prev: concepts
next: BERAdapter
weight: 2
---

## Overview
A BERAgent is a customizable container of skills designed for specific knowledge domains. Agents process natural language inputs, execute tasks via API calls, and return structured responses using the SHAV architecture (Skills, Hooks, Actions, Validators). You can build your own agents or use pre-built ones to automate workflows.

{{< cards cols="1" >}}
  {{< card link="/diagrams/ber-002-agent.svg" title="BERAgent Execution Workflow" image="/diagrams/ber-002-agent.svg" subtitle="Detailed diagram showing the workflow steps of a BERAgent" >}}
{{< /cards >}}

BERAgents will process messages in natural language and produce task specific structured responses. It does this through a sequence of interaction by the **SHAV architecture** (`Skills`, `Hooks`, `Actions`, `Validators`).

## How BERAgents Work
BER enables agents to act as domain executors that perform tasks based on defined instructions. Agents rely on a command card that includes templates and prompts (Skills) specific to their domain. Here’s the execution flow:

1. **Natural Language Processing:** The agent interprets a user request.
2. **Skill Application:** Based on the intent, the agent selects an appropriate skill and generates a response using structured templates.
3. **Validators:** Input is verified to ensure it meets the defined schema and constraints.
4. **Actions:** The agent executes tasks, such as making API calls, interacting with external systems, or triggering events.
5. **Hooks:** Hooks allow the agent to interact with external environments at key stages in the workflow for added flexibility.

This modular approach lets you use pre-built agents or create entirely new ones that cater to your specific needs.

### SHAV architecture
The SHAV architecture underpins the `BER`, enhancing precision, reliability, and extensibility. It introduces additional control and structure to workflows, ensuring better outputs compared to standard LLM-based models.

{{< cards cols="1">}}
  {{< card link="/diagrams/ber-004-SHAV.svg" title="BERAgent SHAV Architecture" image="/diagrams/ber-004-SHAV.svg" subtitle="Diagram showing the SHAV (Skills, Hooks, Actions, Validators) architecture of BERAgents" >}}
{{< /cards >}}

The system implements a chain-of-responsibility pattern where responses flow through the SHAV architecture:
1. Skill selection, template rendering, NLP (skills)
2. Pre- and post-processing, pre- and post-rendering, side effects (hook triggers)
3. Data operations, CRUD, logging, communication (action execution)
4. Type checking, enumeration, field presence, schema marshalling (validation of rules)

Key Benefits:
1. **Improved Output Quality:** Increases precision, direction, and repeatability of results.
2. **Customizability:** Provides control over how agents process inputs, execute tasks, and structure responses.

Collectively we can call these modifiers but to give it a distinction they are named after their initials and referred to as `SHAV`.

#### SHAV components
##### 1. Skills
Skills define the core functionality of an agent. Each skill includes:
- **Prompts:** Custom instructions for generating task-specific responses.
- **Templates:** Predefined structures that guide the format and layout of responses.
- **Schemas:** JSON-based schemas ensure structured outputs with clearly defined fields.

{{< callout >}}
**Example:**
An agent tasked with document generation might use a skill with a prompt for technical writing, a template for layout, and a schema for organizing content into sections.
{{< /callout >}}

###### Prompts
Agents can contain multiple skills which are a collection of behaviors, responsibilities, and guidance. Each skill is named, and is given a specific prompting and response templates and thenwhatever direction real-world users may add. For example, a document author may have a prompt asking for technical writing in neutral language.

###### Templates
The template is used to render the response in a guided, structured, predictable way.

###### Schema
The response will include one or more fields from a JSON Schema that is defined as part of the skill. This allows control over your output and actions.

##### 2. Hooks
Hooks allow agents to interact with external systems or respond to environmental changes. BERAgents include six breakpoints where hooks can trigger custom logic:

- **Pre-LLM:** Before generating a response.
- **Post-LLM:** After generating a response.
- **Pre-Action:** Before executing an action.
- **Post-Action:** After completing an action.
- **Pre-Validation:** Before applying validation rules.
- **Post-Validation:** After applying validation rules.

Hooks expand agent functionality by enabling interactions like logging, analytics, or side effects during workflows.

##### 3. Actions
Actions are the final step in an agent’s workflow. They execute tasks such as making API calls, updating databases, or sending notifications. Users can configure actions to allow manual decision-making, such as approving or rejecting a proposed change.

{{< callout >}}
**Example:**
An `ITAgent` might generate a new DNS configuration and wait for the user to approve or reject it before applying changes.

By adding this modifier we can guarantee supervision for each agent and their skills. The agent helps us and we help the agent in return.
{{< /callout >}}

##### 4. Validators
Validators ensure inputs and outputs conform to predefined rules, increasing reliability and preventing errors.

Validators operate at the start of a skill execution to ensure the agent functions correctly within its domain.


{{< cards >}}
  {{< card link="/tutorials/agent" title="Build Your First Agent" icon="code" >}}
{{< /cards >}}
