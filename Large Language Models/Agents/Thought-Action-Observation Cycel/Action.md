## Definition

- Concrete step an AI agent takes to interact with its environment

## Types of agents

- **JSON agent**: The action to take is specified in JSON format
- **Code agent**: The agent writes a code block that is interpreted externally
- **Function-calling agent**: It is a subcategory of the JSON agent which has been fine-tuned to generate a new message for each action

## Types of actions

- **Information gathering**: Performing web searches, querying databases, or retrieving documents
- **Tool usage**: Making API calls, running calculations, and executing code
- **Environment interaction**: Manipulating digital interfaces or controlling physical devices
- **Communication**: Engaging with users via chat or collaborating with other agents

## Stop-and-parse approach

- **Generation in a structured format**: The agent outputs its intended action in a clear, predetermined format (JSON or code)
- **Halting further generation**: Once the text defining the action has been emitted, the LLM stops generating additional tokens
- **Parsing the output**: An external parser reads the formatted action, determines which tool to call, and extracts the required parameters

## Code agnet

- Instead of outputting a simple JSON object, a code agent generates an executable code block
- **Expressiveness:** Code can naturally represent complex logic, including loops, conditionals, and nested functions, providing greater flexibility than JSON
- **Modularity and Reusability:** Generated code can include functions and modules that are reusable across different actions or tasks
- **Enhanced Debuggability:** With a well-defined programming syntax, code errors are often easier to detect and correct
- **Direct Integration:** Code Agents can integrate directly with external libraries and APIs, enabling more complex operations such as data processing or real-time decision making

## Code examples

```python
# Code Agent Example: Retrieve Weather Information
def get_weather(city):
    import requests
    api_url = f"https://api.weather.com/v1/location/{city}?apiKey=YOUR_API_KEY"
    response = requests.get(api_url)
    if response.status_code == 200:
        data = response.json()
        return data.get("weather", "No weather information available")
    else:
        return "Error: Unable to fetch weather data."

# Execute the function and prepare the final answer
result = get_weather("New York")
final_answer = f"The current weather in New York is: {result}"
print(final_answer)
```
