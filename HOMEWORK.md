# Laboratory 13 homework

For homework, you will create a trip planning assistant, incorporating vLLM, tool usage with
MCP, and security with guardrails. This is basically a simple AI agent, which could be extended
in practical deployment with, e.g., providing affiliate links to travel sites or integrated with
ticket sales.

Write a simple Python chat application, terminal-based (just `input()` + `print()`). User should
be able to converse with the model, refining their trip plan.

Assumptions:

- single-user system
- always pass all tools
- send all messages back and forth every time (stateless app)

Deployment:

1. Docker Compose to deploy the whole system.
2. Dotenv files to store secrets, e.g. API keys. Use environment variables in Docker to
   store and access them in runtime.

First MCP server:

- custom server for [OpenWeatherMap API](https://openweathermap.org/)
- generate a free API key, note that students have a higher limit
- tool for [daily forecast](https://openweathermap.org/forecast16) up to 16 days, returning, e.g.,
  weather description, temperature statistics, precipitation
- tool for [monthly average weather](https://openweathermap.org/api/statistics-api#month) for requests
  over 16 days, returning average monthly weather statistics
- you may need to use a geocoding library to translate city name to coordinates, such
  as [GeoPy](https://geopy.readthedocs.io/en/stable/), or
  use [OpenWeatherMaP geocoding endpoint](https://openweathermap.org/api/geocoding-api#direct_name)

Second MCP server:

- remote [Tavily MCP server](https://docs.tavily.com/documentation/mcp), for web search and page
  scraping
- generate a free API key, you can use either local or a cloud-hosted MCP server
- use it to provide travel information about places

Include security:

- guide the model with system prompt to exclude questions not relevant to trip planning
- select reasonable guardrails

Along code files, include screenshots of conversations with the model.
