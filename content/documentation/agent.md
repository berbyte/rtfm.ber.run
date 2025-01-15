---
title: BERAgent
type: explanation
prev: ./manual
next: ./adapter
---

The system implements a chain-of-responsibility pattern where responses flow through:

1. Schema validation (type checking)
2. Template rendering (presentation)
3. Action execution (side effects)



BER framework defines domain executors - `Agents` - who can accomplish tasks with their command card. The command card has slots for domain specific templates and prompts which is identified as `Skills`.

 Each autonomous unit is built from multiple layers and each layer can be customised separately.

## Agent Specializations
### Documentation Agents

> Like technical writers with different specialties

- **DocAuthor**: Implements the [Diátaxis framework](https://diataxis.fr/) for documentation architecture. Transforms natural language requests into structured technical documentation.
- **MermaidAgent**: Specialized in [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language)-style diagram generation using the Mermaid markup language.

### Management Agents

> Like project management tools with natural language interfaces

- **AgentBuilder**: Meta-agent that generates new agent configurations, similar to a factory pattern for AI components.
- **ProductOwner**: Applies agile methodology patterns to analyze and refine product backlog items.
