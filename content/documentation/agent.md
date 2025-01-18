---
title: BER Agent
diataxis: explanation
prev: documentation/manual
next: documentation/
weight: 3
---

## Overview

**A `BER Agent` is a container of skills covering a specific knowledge domain.**

BER Agents will process messages in natural language and produce task specific structured responses. It does this through a sequence of interaction by the **SHAV architecture** (`Skills`, `Hooks`, `Actions`, `Validators`).

Each agent is a collection of one or more `Skills`, zero or more `Hooks`, zero or more `Actions`, and zero or more `Validators`.

In this sense there is no difference between pre-built agents and custom agents you can create in your domain.
{{< callout emoji="‼️" >}}
  ^^ I would rephrase focusing on the main message which is that you can create your own agents.
{{< /callout >}}

----


{{< callout emoji="‼️" >}}
  we need to explain how the agents are executing calls to 3rd party APIs
{{< /callout >}}


[![BER's SHAV Architecture](/diagrams/ber-004-shav.svg)](/diagrams/ber-004-shav.svg)


## Concept of a BER Agent
BER framework defines domain executors - `Agents` - who can accomplish tasks with their command card. The command card has slots for domain specific templates and prompts which are identified as `Skills`. With the application of their skills they try to fulfill the request and return a structured, directed response.

During request parsing they can run skill-specific `validators`. `BER Agents` can follow up on the response, by running specified `actions`. The real-world user can determine the action to take by selecting the correct action based on the response. During the workflow execution the framework provides `hooks` to listen to / interact with the environment. All of this can be used as-is or extended as-wanted.

### SHAV architecture
BER Agents can be employed as actors in domains because of the introduction of constraints and add-ons to the basic, simple prompt request you would send to any LLM-based AI model. This multi-layered approach gives to 2 very positive advantages.
 1. Enhances the results across metrics such as precision of the answer, the direction of the skill employed, reliability and repeatability of requests.
 2. Allows extensibility, configuration in how an agent uses their skills and how the procedure processes the input, the skill, the output.


Collectively we can call these `modifiers` but to give it a distinction they are named after their initials and referred to as `SHAV`.

#### Skills

##### Prompts
Agents can contain multiple skills which are a collection of behaviors, responsibilities, and guidance. Each skill is named, and is given a specific prompting and response templates and thenwhatever direction real-world users may add. For example, a document author may have a prompt asking for technical writing in neutral language.

##### Templates
The template is used to render the response in a guided, structured, predictable way.

##### Schema
The response will include one or more fields from a JSON Schema that is defined as part of the skill. An example configuration might look like this in golang

```go
type Schema struct {
	Items []struct {
		Name        string `json:"name" jsonschema:"required,description=Name of the item"`
		Description string `json:"description" jsonschema:"required,description=Description of the item"`
	} `json:"items" jsonschema:"required,description=List of items to manage"`
}
```

Find more detailed references in our API documentation.

##### Hooks
A skill is used by any creature in the hope of some benefit, reaction. With hooks the concept of skill is expanded and connected with other systems, and can be triggered or trigger events in the outside world (outside-context).

BER Agent's have 6 breakpoints during execution where we can interact with the agent and react to their work:
 - `Pre-LLM`
 - `Post-LLM`
 - `Pre-Action`
 - `Post-Action`
 - `Pre-Validation`
 - `Post-Validation`

Basically we can oversee the state of any skilled work whenever another behavioral context is used. The state of the outside world, the state of the skill execution are both very complex and their possible interactions are limitless, which is why hooks are needed before and after each `SHAV` modifier for greater control.

##### Actions
Correspondence with the agent can be continued on a custom basis depending on user settings and agent configuration.

Actions are always executed as the last step, and the computed state, the rendered template becomes final. The real-world user can then define what actions would they request from their agent.

For example an `ITAgent` might present you with your new Cloudflare DNS setup. In this case it is natural to have an approve / reject boolean pair of actions for this skill.

By adding this modifier we can guarantee supervision for each agent and their skills. The agent helps us and we help the agent in return.

##### Validators
Validators run at the beginning of the agent's skill execution. They address the prompt given and filter the prompt in-between a human communicating with an agent. It is a modifier that is concerned about what can be and what must not be present for the agent to behave correctly in the skill-space selected.

The two validators that are present for an agent currently are simply black and white:
 - An `AllowList` and
 - a `DenyList`

## Execution Workflow

[![BER Agent Execution Workflow](/diagrams/ber-002-agent.svg)](/diagrams/ber-002-agent.svg)




## Tutorials

### Add a validation rule to filter fake URL refs

## Settings
 Each autonomous unit is built from multiple layers and each layer can be customised separately. These configurations are defined as `golang` code. The table below details the fields and values that determine the final configuration of an agent.

## Examples

### SHAV pattern processing
The system implements a chain-of-responsibility pattern where responses flow through the SHAV architecture:

1. Skill selection, template rendering, NLP (skills)
2. Pre- and post-processing, pre- and post-rendering, side effects (hook triggers)
3. Data operations, CRUD, logging, communication (action execution)
4. Type checking, enumeration, field presence, schema marshalling (validation of rules

{{< callout  >}}
  It is mandatory for an agent to have at least 1 skill defined.

  All other capabilities are optional however their usage is highly recommended.
{{< /callout >}}

### Agent Specializations

#### Documentation Agents

> Like technical writers with different specialties

- **DocAuthor**: Implements the [Diátaxis framework](https://diataxis.fr/) for documentation architecture. Transforms natural language requests into structured technical documentation.
- **MermaidAgent**: Specialized in [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language)-style diagram generation using the Mermaid markup language.

#### Management Agents

> Like project management tools with natural language interfaces

- **AgentBuilder**: Meta-agent that generates new agent configurations, similar to a factory pattern for AI components.
- **ProductOwner**: Applies agile methodology patterns to analyze and refine product backlog items.
