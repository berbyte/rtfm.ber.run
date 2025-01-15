---
title: BER
---

###### Welcome to the BER framework docs

BER is a versatile, structured, systematic framework to employ AI models and allow corresponding with them specifically and reliably.

On this page you can find detailed information of the two main components of the BER system which are
 - the `BERAgent` (llm-end) and
 - the `BERAdapter` (user-facing client).

The most important concepts, and guides on how to get started are highlighted in the Explore section further down; just after our short summary for newcomers. (Folded content, click to unwhirl.)

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


## Explore
{{< cards >}}
{{< card link="documentation" title="Documentation" icon="book-open" >}}
{{< card link="manual" title="User Manual" icon="user" >}}
{{< card link="documentation/agent" title="BERAgent Overview" icon="user" >}}
{{< card link="documentation/adapter" title="BERAdapter Overview" icon="user" >}}
{{< card link="documentation/glossary" title="Glossary" icon="user" >}}
{{< /cards >}}
