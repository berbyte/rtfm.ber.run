---
title: Building your BERAgent
weight: 2
prev: /tutorials/setup
next: /tutorials/github
sidebar:
  open: true
---


## Let's build a Weather Agent

### BERAgent configuration

```golang
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

```golang
package weather

type WeatherTrendSchema struct {
	DiagramCode string `json:"diagram_code" jsonschema:"required,description=The valid Mermaid code Flow or sequence or pie chart"`
	Explanation string `json:"explanation" jsonschema:"required,description=Detailed explanation of the diagram"`
}
```

### Skill configuration

```golang
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
```golang
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
