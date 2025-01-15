# BER Agent System Glossary

## Core System Terms

### Agent System

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

## Agent Specializations

From `internal/config/agents/main.go`

### Documentation Agents

> Like technical writers with different specialties

- **DocAuthor**: Implements the [Diátaxis framework](https://diataxis.fr/) for documentation architecture. Transforms natural language requests into structured technical documentation.
- **MermaidAgent**: Specialized in [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language)-style diagram generation using the Mermaid markup language.

### Management Agents

> Like project management tools with natural language interfaces

- **AgentBuilder**: Meta-agent that generates new agent configurations, similar to a factory pattern for AI components.
- **ProductOwner**: Applies agile methodology patterns to analyze and refine product backlog items.

## File Organization and their Meaning

- cmd/ (Command line applications)
- internal/ (Private implementation)
- pkg/ (Shared packages)
- doc/ (Documentation and decisions)

The system implements a chain-of-responsibility pattern where responses flow through:

1. Schema validation (type checking)
1. Template rendering (presentation)
1. Action execution (side effects)

### Error Handling

The system categorizes errors into distinct types:

- Schema violations (type errors)
- Template rendering failures (presentation errors)
- Processing failures (runtime errors)

## Inputs

### GitHub Events

The BER system primarily processes GitHub events as input signals:

- **Issue Comments**: Natural language requests prefixed with "@ber"
- **Issue Creation**: Initial problem statements and documentation requests
- **Installation Events**: System setup and initialization triggers

Terminology is taken from code:

```go
// Event types the system responds to
const (
    Install      Event = "installation"
    Issues       Event = "issues"
    IssueComment Event = "issue_comment"
)
```

### Messages

Messages flow through a validation pipeline:

1. Author verification (skip bot messages)
1. Intent detection ("@ber" mentions)
1. Content extraction (body parsing)

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
