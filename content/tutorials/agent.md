---
title: Your First BERAgent
weight: 2
prev: /tutorials/setup
next: /tutorials/github
sidebar:
  open: true
---


Let's create a Weather Agent to visualize weather data using diagrams. The agent will generate Mermaid-based visualizations. This demonstrates how to create a custom BER agent with specific skills and schema definitions.

### Prerequisites

Before starting this tutorial, make sure you have set up your BER development environment following the [setup guide](/tutorials/setup)

```
cd ber-os
mkdir agents/my_frist_agent
cd agents/my_first_agent
```

### BERAgent configuration
First, let's create the agent configuration. This file registers our Weather Agent with BER, defining its name, tag, and available skills. The `init()` function ensures the agent is registered when the package is imported.

```golang{linenos=table,hl_lines=[2,4],linenostart=1,filename=agent.go}
package weather

import "github.com/berbyte/ber/internal/agent"

func init() {
	agent.RegisterAgent(agent.BERAgent{
		Name:        "Weather Agent",
		Tag:         "weather",
		Description: "Weather Agent: provides current weather information for any location",
		Skills: []agent.BaseSkill{
			WeatherInfo,
		},
	})
}
```

### Schema configuration
Next, we'll define the schema for our Weather Agent. This schema specifies the data structure that will be used to store and process weather information. The schema includes fields for location details (filled by the LLM) and weather metrics (populated by the API hook).

The schema uses struct tags to provide JSON mapping and validation rules. The `jsonschema` tags define validation rules and field descriptions that will be processed by the LLM to populate values according to the schema requirements. See [JSON Schema documentation](https://json-schema.org/understanding-json-schema/) for more details on validation rules.

```golang{linenos=table,hl_lines=[2,4],linenostart=1,filename=types.go}
package weather

type WeatherResponseSchema struct {
	// These fields will be filled by the LLM
	Location    string  `json:"location" jsonschema:"required,description=The location name"`
	Latitude    float64 `json:"latitude" jsonschema:"required,description=The latitude of the location"`
	Longitude   float64 `json:"longitude" jsonschema:"required,description=The longitude of the location"`
	// These will be filled in the PostLLMHook
	Temperature float64 `json:"temperature"`
	WindSpeed   float64 `json:"wind_speed"`
	Humidity    int     `json:"humidity"`
	IsDay       bool    `json:"is_day"`
}
```

### Skill configuration
Now, let's define the skill configuration for our Weather Agent. This configuration specifies how the skill processes user input, interacts with the LLM, and formats the output. The skill includes:

- A name and description for identification
- A prompt that guides the LLM in extracting location information
- A template for formatting the weather data output
- The schema we defined earlier for data structure
- A hook that fetches real weather data after LLM processing

```golang{linenos=table,hl_lines=[2,4],linenostart=1,filename=skill_trend.go}
package weather

import "github.com/berbyte/ber/internal/agent"

type WeatherSkill struct {
	agent.Skill[WeatherResponseSchema]
}

var WeatherInfo = WeatherSkill{
	Skill: agent.Skill[WeatherResponseSchema]{
		Name:        "Weather Information",
		Tag:         "weather",
		Description: "Displays current weather information for a location",
		Prompt: `As a location information extractor, analyze the following text and extract:
1. The location or city name
2. Its exact latitude and longitude coordinates

Return the information in JSON format with the following fields:
- location: the name of the location
- latitude: the latitude coordinate
- longitude: the longitude coordinate`,
		Template: `### Weather in {{.location}} ({{.latitude}}, {{.longitude}}) {{if .is_day}}☀️{{else}}🌙{{end}}

🌡️ Temperature: {{.temperature}}°C
💨 Wind Speed: {{.wind_speed}} km/h
💧 Humidity: {{.humidity}}%`,
		LLMSchema: WeatherResponseSchema{},
		Hooks: agent.Hooks[WeatherResponseSchema]{
			PostLLMRequest: fetchWeatherData,
		},
	},
}
```

### Hooks
The `fetchWeatherData` hook is responsible for retrieving real-time weather data from the Open-Meteo API using the location coordinates extracted by the LLM. It updates the response schema with current temperature, wind speed, humidity and daylight status.


```golang{linenos=table,hl_lines=[2,4],linenostart=1,filename=hooks.go}
package weather

import (
	"context"
	"encoding/json"
	"fmt"
	"net/http"
)

type weatherResponse struct {
	Current struct {
		Temperature float64 `json:"temperature_2m"`
		WindSpeed   float64 `json:"wind_speed_10m"`
		RelHumidity int     `json:"relative_humidity_2m"`
		IsDay       int     `json:"is_day"`
	} `json:"current"`
}

func fetchWeatherData(ctx context.Context, response *WeatherResponseSchema) error {
	if ctx.Err() != nil {
		return ctx.Err()
	}

	// Get weather data using the coordinates
	weatherURL := fmt.Sprintf("https://api.open-meteo.com/v1/forecast?latitude=%.6f&longitude=%.6f&current=temperature_2m,relative_humidity_2m,wind_speed_10m,is_day",
		response.Latitude, response.Longitude)

	req, err := http.NewRequestWithContext(ctx, "GET", weatherURL, nil)
	if err != nil {
		return fmt.Errorf("creating weather request: %w", err)
	}

	resp, err := http.DefaultClient.Do(req)
	if err != nil {
		return fmt.Errorf("fetching weather data: %w", err)
	}
	defer resp.Body.Close()

	var weatherResp weatherResponse
	if err := json.NewDecoder(resp.Body).Decode(&weatherResp); err != nil {
		return fmt.Errorf("decoding weather response: %w", err)
	}

	// Update the response with real weather data
	response.Temperature = weatherResp.Current.Temperature
	response.WindSpeed = weatherResp.Current.WindSpeed
	response.Humidity = weatherResp.Current.RelHumidity
	response.IsDay = weatherResp.Current.IsDay == 1

	return nil
}
```

### Registering the new agent

Register your agent by adding it to `agents/registry.go`:

```golang{linenos=table,hl_lines=[2,4],linenostart=1,filename=registry.go}
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

{{< cards cols="1" >}}
  {{< card link="/screenshots/tui-weather.png" image="/screenshots/tui-weather.png" title="Weather Agent in TUI" >}}
{{< /cards >}}
