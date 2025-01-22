---
title: Manual
type: docs
diataxis: explanation
prev: documentation
next: documentation/agent
---

# BER framework -- User manual

| Revisions                       | Version  | Update date   | Author |
|:-------------------------------:|:--------:|:-------------:|:------:|
| adding manual, product overview | `v0.2.0` | 2025. 01. 15. | @pvj   |
| init                            | `v0.1.0` | 2025. 01. 11. | @dominis       |

# Quickstart

# Components
Responsibilities of the BER framework are separated into 2 components. The system has a linear, sequential execution path. Inputs are handled one at a time, and produce zero or one output from each input. The input and output is communicated with the real-world user through an adapter. An agent is called by an adapter, the agent is given the content from the adapter with relevant context. Agents both receive context and produce their own context. There are modifiers that create or collect contexts during execution. The agent produces the output that is represented by the adapter. Agents and adapters are inter-changeable and customisable. BER always execute the same workflow. The user manual is going to describe what is meant when referring to content, context, modifier, agent, and adapter.

## Agents
An agent component is the highest-level collection of features and data, and it covers some specific domain. It can be tricky to understand where a context begins or a content ends or a domain applies. The agents are task-based and follow a simple request-response pattern.

### Considering domains
We can think of a domain in a couple of different terms. (However there are no absolute rules, use your own judgment!)
 - Function: Like a job description, a functional domain covers a role, a collection of inter-dependent tasks and skills. F.e. `product owner`.
 - Result: We may associate domains with a type of result or presentation it has to produce. F.e. `charts`
 - Knowledge: Certain topics or certain knowledge we would like to interact with. Eg. `BER agent builder`

An agent is an expert and executor of a given domain. The actions it can take and the validation an agent does should be modelled with the specific domain in mind.

### Understanding context
We use the term `context` for any data that is independent of the request's content and affects how the content is going to be understood by the agent.
The agent will process a given request in steps. In the first steps context is parsed. This determines scope and boundary the agent is going to work with. Some context is agent-wide, some context is skill-specific, and users can provide context for a single request processing.


For agent examples head to BERAgent Overview.

## Adapters
For adapter reference head to BERAdapter Overview document.

# Tutorials

# Guides
 - [How to use BER as a GitHub application?](howto-adapter-github-install)
 - [How to use GitHub labels to invoke BER?](howto-adapter-github-label)
 -

# Terminology
To understand specific syntax related to BER please visit the glossary.
