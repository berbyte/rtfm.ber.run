---
title: Getting Started
next: docs/agent
sidebar:
  include: true
  open: true
weight: 2
---

## Summary

{{< callout emoji="‼️" >}}
BER is designed based on the principles of the Actor model, enabling independent and distributed processing. By combining this architecture with the power of AI, BER creates agents that are intelligent, flexible, and capable of assisting you in automating and executing tasks within their defined domains.'

or

The BER framework leverages the Actor model to combine independent, distributed processing with the power of AI. This creates dynamic, guided, and modifiable agents—BERAgents—capable of assisting you and executing tasks within their defined domains.

{{< /callout >}}


The BER framework is constructed in the image of the Actor model. The combination of independent and distributed processing with the power of AI creates capable, guided, modifiable agents who can assist you and execute tasks on your behalf within their operating domain.

[![BER's High Level System Diagram](/diagrams/ber-001-framework.svg)](/diagrams/ber-001-framework.svg)


{{< callout emoji="‼️" >}}

The framework has two key components:

- BERAgents: Independent actors that perform tasks and workflows.
- BERAdapters: Communication channels that enable seamless integration with external systems like APIs, databases, and cloud services.

Together, these components enable a highly modular and parallelized system of agents and adapters, ready to tackle complex workflows.

This documentation provides an overview of the system, tutorials to help you get started, and practical examples to compose and customize BER. Start building today to see how BER can streamline your workflows.

{{< /callout >}}

The 2 main components are the actors and the communication channel with these actors. In this context we call the actor: `BERAgent` and the channel: `BERAdapter`. The system is composed of multiple independent agents and adapters running in parallel.

Throughout our documentation you will find an overview of this system, tutorials to get started, and practical examples to compose and customize BER.


## Next
{{< cards >}}
{{< card link="usecases" title="Usecases" icon="user" >}}
{{< /cards >}}
