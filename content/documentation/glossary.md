---
title: Glossary
cascade:
  type: docs
sidebar:
  include: true
weight: 10
---


# BER System Glossary

## Core System Terms

 - Agent
 - Skill
 - Action
 - Validation
 - Hook
 - Adapter

### BERAgent

> Like a microservices architecture where each service has natural language capabilities

The BER agent system implements the [Actor model](https://en.wikipedia.org/wiki/Actor_model) for distributed AI processing. Each agent is an autonomous unit that processes messages (prompts) and produces structured responses.

### GitHub Request

Found in `internal/integrations/github/webhook/`, handles:

- Installation events
- Issue events
- Issue comment events
- Event signature verification

Defined in `internal/models/github.go`:

```go
type GitHubRequest struct {
    Event     string    // Type of GitHub event
    Payload   string    // Raw event data
    Processed bool      // Processing status
}
```

### BER Agent

> Like a specialized service worker

Core system type in `internal/config/types.go`:

```go
type BERAgent struct {
    Name      string            // Agent identifier
    Prompt    string            // System instructions
    Template  string            // Response format
    LLMSchema interface{}       // Response structure
    Action    func(interface{}) // Processing function
}
```

### Template System

> Like a view layer in MVC architecture

Templates provide a presentation layer that transforms structured data into human-readable formats. The system uses Go's text/template package with custom functions for documentation-specific formatting.



## File Organization and their Meaning

- cmd/ (Command line applications)
- internal/ (Private implementation)
- pkg/ (Shared packages)
- doc/ (Documentation and decisions)


### Error Handling

The system categorizes errors into distinct types:

- Schema violations (type errors)
- Template rendering failures (presentation errors)
- Processing failures (runtime errors)





## TODO: Future Glossary Terms

### TBD

- **Response Templates**: Standard response patterns for common requests
- **Agent Coordination**: How multiple agents collaborate on complex tasks

### Similar Concepts to Clarify

- User (GitHub user vs bot distinction)
- Client (GitHub API client vs OpenAI client)
- Event (GitHub event types and processing)
- Message (Comment content and processing)

### Domain-Specific Terms

- **GitHub App Permissions**: Required scopes and their implications
- **LLM Integration Points**: Where and how AI models are invoked
