---
title: Your First BERAgent
weight: 2
prev: /tutorials/setup
next: /tutorials/github
sidebar:
  open: true
---


Let's create a Weather Agent that helps visualize weather data using charts and diagrams. The agent will generate Mermaid-based visualizations to analyze weather trends and patterns. This demonstrates how to create a custom BER agent with specific skills and schema definitions.

### Prerequisites

Before starting this tutorial, make sure you have set up your BER development environment following the [setup guide](/tutorials/setup)

```
cd ber-os
mkdir agents/my_frist_agent
cd agents/my_first_agent
```

### BERAgent configuration

```golang{filename=agent.go}
package weather

import "github.com/berbyte/ber/internal/agents"

func init() {
	agents.RegisterAgent(agents.BERAgent{
		Name:        "Weather Visualization",
		Tag:         "weather",
		Description: "Weather Agent: helps visualize and analyze weather data using charts and diagrams",
		Skills: []agents.BaseSkill{
			WeatherTrendChart,
		},
	})
}
```

### Schema configuration

```golang{filename=types.go}
package weather

type WeatherTrendSchema struct {
	DiagramCode string `json:"diagram_code" jsonschema:"required,description=The valid Mermaid code Flow or sequence or pie chart"`
	Explanation string `json:"explanation" jsonschema:"required,description=Detailed explanation of the diagram"`
}
```

### Skill configuration

```golang{filename=skill_trend.go}
package weather

import (
	"github.com/berbyte/ber/internal/agents"
)

type WeatherTrendSkill struct {
	agents.Skill[WeatherTrendSchema]
}

var WeatherTrendChart = WeatherTrendSkill{
	Skill: agents.Skill[WeatherTrendSchema]{
		Name:        "Weather Trend Chart",
		Tag:         "trend",
		Description: "Creates weather trend visualizations using Mermaid charts",
		Prompt: `As a weather visualization expert, create a Mermaid chart based on the provided weather data.
Follow these guidelines:
- Create a line or bar chart showing temperature/precipitation trends
- Include clear labels for time periods (days/hours)
- Add appropriate units (°C/°F for temperature, mm/inches for precipitation)
- Use color coding for different weather parameters
- Ensure the chart is easy to read and interpret
- Use valid Mermaid syntax that can be rendered in markdown
- Don't include markdown code blocks in the response`,
		Template: `### Weather Trend Visualization

{{.diagram_code}}

### Analysis

{{.explanation}}`,
		LLMSchema: WeatherTrendSchema{},
		Hooks: agents.Hooks[WeatherTrendSchema]{
			PostLLMRequest: postLLMRequest,
		},
	},
}

```

### Hooks
```golang{filename=hooks.go}
package weather

import (
	"context"
	"strings"
)

func postLLMRequest(ctx context.Context, response *WeatherTrendSchema) error {
	if ctx.Err() != nil {
		return ctx.Err()
	}

	if !strings.HasPrefix(response.DiagramCode, "```mermaid") {
		response.DiagramCode = "```mermaid\n" + response.DiagramCode + "\n```"
	}
	return nil
}
```

### Registering the new agent

You need to load your agent in `agents/registry.go`:

```golang{filename=registry.go}
package agents

import (
	...
	_ "github.com/berbyte/ber-os/agents/my_first_agent"
)
```

### Test in the TUI:
```
go run . tui --debug
```
