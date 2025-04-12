# Google ADK Examples

This repository contains example implementations using the Google Agent Development Kit (ADK).
Watch a YouTube Video [here](https://youtu.be/TONBnWCsoTU).

## Project Structure

```
/
├── google-search-agent/   # Google Search based agent
└── multi-task-agent/      # Multi-capability agent (weather and time)
```

## Agents

### Google Search Agent

A simple agent that leverages Google Search to answer questions. It uses the Gemini 2.0 Flash model for generating responses.

**Features:**
- Uses Google Search for grounding responses
- Follows instructions to act as an expert researcher
- Sticks to facts in its responses

**Implementation:**
```python
# Located in google-search-agent/agent.py
from google.adk.agents import Agent
from google.adk.tools import google_search

root_agent = Agent(
    name="basic_search_agent",
    model="gemini-2.0-flash-exp",
    description="Agent to answer questions using Google Search.",
    instruction="You are an expert researcher. You always stick to the facts.",
    tools=[google_search],
)
```

### Multi-Task Agent

An agent that can provide weather information for cities and tell the current time.

**Features:**
- Weather reporting for cities (mock implementation for New York)
- Current time reporting
- Uses custom tool functions

**Implementation:**
```python
# Located in multi-task-agent/agent.py
import datetime
from google.adk.agents import Agent

# Custom tool functions for weather and time
def get_weather(city: str) -> dict:
    # Implementation details...

def get_current_time(city: str) -> dict:
    # Implementation details...

root_agent = Agent(
    name="weather_time_agent",
    model="gemini-2.0-flash-exp",
    description="Agent to answer questions about weather in a city.",
    instruction="I can answer your questions about weather in a city.",
    tools=[get_weather, get_current_time],
)
```

## Requirements

- Google ADK (`google.adk`)
- Gemini 2.0 Flash model access
- Python 3.x

## Usage

The repository is organized to showcase different agent implementations using Google's Agent Development Kit.

1. Google Search Agent: Demonstrates how to create an agent that uses Google Search to answer questions
2. Multi-Task Agent: Shows how to implement custom tools that an agent can use to perform specific tasks

To run these examples, you'll need appropriate Google ADK credentials and access to the Gemini models.

## License

This project uses Google ADK, please refer to Google's licensing and usage terms for the ADK.