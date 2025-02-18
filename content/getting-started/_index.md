---
title: Getting Started
next: usecases
sidebar:
  include: true
  open: true
weight: 2
toc: false
---

## Summary
First, look at what you get by the end of our guide. After correct setup, you see `BER` builds server- and client-side units. By launching the TUI or integrating a GitHub application you will be able to start using `BER` -- in natural language -- requesting work-, compute-, or data-resources.

The next page is going to include examples and usecases then we describe how to prepare run-time environment.

{{< cards cols="1" >}}
  {{< card link="/diagrams/ber-001-framework.svg" image="/diagrams/ber-001-framework.svg" title="End-to-End Request Processing  in BER" subtitle="User input flows through BER: requests enter via BERAdapters, get routed to appropriate BERAgents who select relevant skills, generate proposed solutions for user approval, and finally execute approved actions through external APIs" >}}
{{< /cards >}}


`BER` implements the [Actor model](https://en.wikipedia.org/wiki/Actor_model) to combine distributed processing and LLMs.

The system has two key base types:
- `BERAgents`: Independent actors that perform tasks and workflows.
- `BERAdapters`: Communication channels that enable integration with external systems.

This documentation provides the first steps to use `BER`. You can find in other categories articles about:
 - [Concepts](/concepts) - overview of the system,
 - [Tutorials](/tutorials) - help material for learning,
 - [Guides](/guides) - practical examples to compose and customize BER.

## Next
{{< cards >}}
{{< card link="usecases" title="Usecases" icon="library" >}}
{{< card link="quickstart" title="Quickstart Guide" icon="library" >}}
{{< /cards >}}


## Contact, feedback, questions
{{< callout emoji="❓" >}}
  Have a question or feedback? Feel free to [open an issue](https://github.com/berbyte/ber-os/issues/new)!
{{< /callout >}}
