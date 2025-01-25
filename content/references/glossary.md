---
title: Glossary
diataxis: reference
next: Implementation
prev: References
weight: 2
---


# BER System Glossary
## Core System Terms
- [Action](#Action)
- [BER](#BER)
- [BERAdapter](#BERAdapter)
- [BERAgent](#BERAgent)
- [Domain](#Domain)
- [Hook](#Hook)
- [Prompt](#Prompt)
- [Schema](#Schema)
- [SHAV Architecture](#SHAV)
- [Skill](#Skill)
- [Template](#Template)
- [Validator](#Validator)

---

### Action
A procedure [`BER`](#BER) can optionally do with the data received from the LLM response. It is bound to a [`Skill`](#Skill). Actions return a function operating on your data.
> Like a callback in a front-end framework.

### BER
Péter "BER" Berényi was our mentor and senior to whom we dedicate this project.

`BER` means in the context of this documentation the system. 

## BERAdapter
Core system type. An adapter allows connections between [`Agents`](#BERAgent) and APIs or other external platforms. An adapter defines a client API interface that can be used for integration.
> Like an electrical adapter used for charging devices

### BERAgent
Core system type. An agent is an expert and executor of a given domain. The actions it can take and the validation an agent does should be modelled with the specific domain in mind.
> Like a microservices architecture where each service has natural language capabilities

in `internal/config/types.go`:

```go
type BERAgent struct {
    Name      string            // Agent identifier
    Prompt    string            // System instructions
    Template  string            // Response format
    LLMSchema interface{}       // Response structure
    Action    func(interface{}) // Processing function
}
```

### Domain
We can think of a domain in a couple of different terms. (However there are no absolute rules, use your own judgment!)
 - Function: Like a job description, a functional domain covers a role, a collection of inter-dependent tasks and skills. F.e. `product owner`.
 - Result: We may associate domains with a type of result or presentation it has to produce. F.e. `charts`
 - Knowledge: Certain topics or certain knowledge we would like to interact with. Eg. `BER agent builder`

## Error types
The system categorizes errors into distinct types:
- Schema violations (type errors)
- Template rendering failures (presentation errors)
- Processing failures (runtime errors)


## Template System
Templates provide a presentation layer that transforms structured data into human-readable formats. The system uses Go's text/template package with custom functions for documentation-specific formatting. Templates are bound to [`Skills`](#Skills). 
> Like a view layer in MVC architecture

## User
The documentation assumes there is a human entity giving commands and input.
