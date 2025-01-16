---
title: BER
type: docs
sidebar:
  open: true
---

##### Welcome to the BER framework docs
###### What is BER?
BER is a versatile, structured, systematic framework to employ AI models, to deploy autonomous agents in a domain of your interest, and to correspond with them specifically and reliably. The marriage of free-form data input and structured access that makes for example, spreadsheets so ubiquitous is a useful analogy to understand how BER works. BER consists of domain expert Agents composed of skills, actions, validations just like a real-world colleague. For example, a product owner agent can assist you in giving estimates, breaking down a task into requirements.

###### Features
 - **Natural language input** Whatever the medium and the task at hand you can say so without needing to think about `syntax`
 - **Control over AI models** Use the combination of agents, skills, validation, action, and hook execution to guide and channel the limitless raw power of LLM-type AI models
 - **Assistance across domains** Customise any of the components to extend BER and encapsulate new fields of expertise and fine-tune various skills to generate, replicate, compare, extract, transform your input
 - **Define the world of BER** Add existing or create new adapters to make BER available on any channel in every medium

##### Read further and explore

 - Start using BER immediately, visit the quick-start section for instructions,
 - Learn more by heading straight to the technical documentation,
 - Understand how to communicate with BER.

{{< cards >}}
{{< card link="documentation" title="Documentation" icon="book-open" >}}
{{< card link="manual" title="User Manual" icon="user" >}}
{{< card link="documentation/agent" title="BERAgent Overview" icon="user" >}}
{{< card link="documentation/adapter" title="BERAdapter Overview" icon="user" >}}
{{< card link="documentation/glossary" title="Glossary" icon="user" >}}
{{< /cards >}}


#### For starters
##### Reasons
<details>
<summary>The collective intelligence represented by the current models is a marvel in its own terms. The partial coherence and understanding can still make it frustrating to use them to complete everyday tasks. This hit-and-miss in their usefulness is a huge waste. We believe this is a topological issue that boils down to data structures.</summary>
</details>

##### Goal
<details>
<summary>BER aims to be the framework that brings natural language capabilities as useful and purposeful services through human interfaces.</summary>
</details>

##### Audience
<details>
<summary>With our extensible, configurable ASHAV architecture (Agents, Skills, Hooks, Actions, Validators) and a set of pre-defined agents that are ready to be used, the BER framework hopes to accomodate hackers, developers, management people, support teams - anyone with chores, with overheads, robotic tasks.</summary>
</details>

##### Our product
###### BERAgent
<details>
<summary>The BER framework is constructed in the image of the Actor model. The combination of independent and distributed processing with the power of AI creates capable, guided, modifiable agents who can assist you and execute tasks on your behalf within their operating domain.

These units are called `Agents` - domain experts and executors. An `agent` can send and receive messages with their `skills`, they can follow up by running specified `actions` or `validations`. During the workflow execution the framework provides `hooks` to listen to the environment.

A BERAgent will process messages in natural language and produce task specific structured responses. Correspondence can be continued on a custom basis depending on user settings and agent configuration.</summary>
</details>

###### BERAdapter
<details>
<summary>The BERAdapter is client-facing interface that is implemented for any system that has a method to communicate real-world input with a BERAgent. An adapter is defined for a specific interface which may be a platform e.g. Github; or a terminal.</summary>
</details>
