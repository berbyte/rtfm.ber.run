---
title: Implementation
diataxis: reference
prev: Glossary
weight: 3
---

## Agent Specializations
### Documentation Agents

> Like technical writers with different specialties

- **DocAuthor**: Implements the [Diátaxis framework](https://diataxis.fr/) for documentation architecture. Transforms natural language requests into structured technical documentation.
- **MermaidAgent**: Specialized in [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language)-style diagram generation using the Mermaid markup language.

### Management Agents

> Like project management tools with natural language interfaces

- **AgentBuilder**: Meta-agent that generates new agent configurations, similar to a factory pattern for AI components.
- **ProductOwner**: Applies agile methodology patterns to analyze and refine product backlog items.

## Agent domains
We can think of a domain in a couple of different terms. (However there are no absolute rules, use your own judgment!)
 - Function: Like a job description, a functional domain covers a role, a collection of inter-dependent tasks and skills. F.e. `product owner`.
 - Result: We may associate domains with a type of result or presentation it has to produce. F.e. `charts`
 - Knowledge: Certain topics or certain knowledge we would like to interact with. Eg. `BER agent builder`

An agent is an expert and executor of a given domain. The actions it can take and the validation an agent does should be modelled with the specific domain in mind.
