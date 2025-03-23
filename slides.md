---
theme: slidev-theme-nearform
background: https://images.unsplash.com/photo-1636690581110-a512fed05fd3?q=80&w=1920&auto=format&fit=crop
title: Practical Introduction to LLMs with Ollama
info: Workshop by EmaSuriano
transition: slide-left
---

# Practical Introduction to LLMs with Ollama

## Workshop by [EmaSuriano](https://emasuriano.com)

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/EmaSuriano/workshop-ollama" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

---

# What will we do today?

- Understand what local LLMs are and why they're important
- Install and configure Ollama on your computer
- Experiment with different language models
- Create graphical interfaces to interact with your models
- Develop practical applications with local AI

---

# Why Local LLMs?

<v-clicks>

- **Privacy**: Your data never leaves your computer
- **Offline**: They work without internet
- **Customization**: Total control over models and parameters
- **Economy**: No recurring costs for API calls
- **Latency**: Faster responses without depending on external servers

</v-clicks>

---

# Comparison: Local vs Cloud

<v-clicks>

| Feature       | Local LLMs     | Cloud LLMs      |
|---------------|----------------|-----------------|
| Privacy       | ✅ Total       | ❌ Limited      |
| Power         | ⚠️ Limited by hardware | ✅ High  |
| Cost          | ✅ Free/One-time| ❌ Subscription |
| Customization | ✅ Complete    | ⚠️ Limited     |
| Ease of use   | ⚠️ More technical | ✅ Simple    |
| Availability  | ✅ 24/7 Offline | ❌ Requires internet |

</v-clicks>

---
layout: two-cols-header
---

# Technical Requirements

::left::

## Minimum:

- Modern CPU (4+ cores)
- 8GB RAM
- 10GB free space
- Compatible operating system

::right::

## Recommended:

- NVIDIA GPU (CUDA)
- 16GB+ RAM
- 50GB+ free space

---
layout: image-right
image: ./assets/ollama.png
---

# **Ollama**: Your Local LLMs Platform

- Open source framework to run LLMs locally
- Support for multiple models (Llama, Mistral, Phi, etc.)
- Simple and powerful API
- Intuitive command line interface

---
layout: image-right
image: ./assets/ollama-install.png
---

# Installing Ollama

Ollama supports all Operating Systems:

* [Mac](https://ollama.com/download/mac)
* [Linux](https://ollama.com/download/linux)
* [Windows](https://ollama.com/download/windows)

---

# First Steps with Ollama

Ollama itself doesn't have an interface, so the way to communicate is using the console:

```bash
> ollama

Usage:
  ollama [flags]
  ollama [command]

Available Commands:
  serve       Start ollama
  create      Create a model from a Modelfile
  show        Show information for a model
  run         Run a model
  stop        Stop a running model
  pull        Pull a model from a registry
  push        Push a model to a registry
  list        List models
  ps          List running models
  cp          Copy a model
  rm          Remove a model
  help        Help about any command

Flags:
  -h, --help      help for ollama
  -v, --version   Show version information

Use "ollama [command] --help" for more information about a command.
```

---

# Normal workflow with models

<v-clicks every="2">

## 1. Download a model

```bash
> ollama pull llama3.2
```

## 2. Start a conversation
```bash
> ollama run llama3.2
>>> Hi
How can I help you today?
```

## 3. Query from the terminal

```bash
> ollama run llama3.2 "Tell me a good joke"
Sure! Here's one:
Why did the computer go to the doctor?
Because it had a virus!
Hope that made you smile. Would you like to hear another one?
```

</v-clicks >

---
layout: image-right
image: ./assets/ollama-models.png
---

# Popular Models in Ollama

- **Mistral** - Balanced in size and performance
- **Llama** - Various versions and sizes available
- **Phi** - Compact but powerful
- **Gemma** - Google's open model
- **Deepseek-r1** - Chinese model with reasoning

---
layout: image
image: https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExbWRwbzU0b2MweDBqdWFjZmU0NzVuMHlveTdiM3BtYWpvOHc0eGJqcSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/fxqt51CAMGITJlxcRI/giphy.gif
---

<!-- Demo Ollama -->

---
layout: quote
---

# "That's nice and all, but this doesn't look like Chat GPT"

-. Said by everyone ...

---
layout: iframe-right
url: https://msty.app/
---

# MSTY

It's the easiest way to use local and online AI models with seamless integration of Ollama and without the need for technical configuration.

## Features

- No technical setup (no Docker, no terminal)
- Compare multiple AI responses side by side
- Import files and connect knowledge sources 
- Better UX for Ollama

---
layout: iframe
url: https://docs.msty.app/getting-started/download
---

# MSTY: Installation

---
layout: image
image: https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExcm5tdnp0dGt1anU2Z2ZwcXBvejhreW42cDZsNm8wODNxOTdpYXJwYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/WcpaItX5JHYkw/giphy.gif
---

<!-- Demo MSTY -->

---
layout: quote
---

# "That's nice and all, but how do I make an application?"

-. Said by devs ...

---

```mermaid {scale:0.7}
flowchart TD
    %% Clients
    WebApp([Web Application])
    MobileApp([Mobile Application])
    DesktopApp([Desktop Application])
    CLI([Command Line Tool])
    
    %% Backend components
    subgraph Backend["Backend Services"]
        direction TB
        Gateway[API Gateway]
        
        subgraph AppLayer["Application Layer"]
            direction LR
            Logic[Business Logic]
            DB[(Database)]
        end
        
        subgraph AILayer["AI Layer"]
            direction LR
            Framework["LLM Framework"]
            OllamaService["Ollama"]
        end
    end
    
    %% Client connections
    WebApp -->|HTTP/REST| Gateway
    MobileApp -->|HTTP/REST| Gateway
    DesktopApp -->|HTTP/REST| Gateway
    CLI -->|HTTP/REST| Gateway
    
    %% Backend connections
    Gateway <--> Logic
    Logic <--> DB
    Logic <-->|Requests models| Framework
    Framework <-->|API calls| OllamaService
    
    %% Visual styling
    classDef clients stroke:#1890ff
    classDef gateway stroke:#52c41a
    classDef appLayer stroke:#d48806
    classDef aiLayer stroke:#fa541c
    classDef database stroke:#722ed1
    
    class WebApp,MobileApp,DesktopApp,CLI clients
    class Gateway gateway
    class Logic appLayer
    class Framework,OllamaService aiLayer
    class DB database
    
    %% Add titles
    subgraph Clients["Client Applications"]
        WebApp
        MobileApp
        DesktopApp
        CLI
    end
```

---
layout: two-cols-header
---

# Stack of a (real) application

::left::

<v-click>

## Frontend

* Web Application: ReactJS
* Mobile Application: Kotlin / Swift
* Desktop Application: Electron
* Command Line Tool: Commander

</v-click>

::right::

<v-click>

## Backend

* API Gateway: FastAPI, Flask, etc.
* Application Layer + Database
* AI Layer: 🎁
* Ollama: we've already seen it

</v-click>

---

# Stack of a _workshop_ application

## Frontend + Backend

* Frontend: Chainlit / Streamlit ✨
* Application Layer + Database
* AI Layer: 🎁
* Ollama: we've already seen it

---

# Streamlit

Streamlit is a Python framework for quickly building interactive web applications for data science and artificial intelligence.

<v-clicks>

- **Simplicity**: Create web applications with pure Python (no need for HTML/CSS/JS)
- **Rapid prototyping**: Turn data scripts into shareable web applications in minutes
- **Interactive elements**: Built-in widgets for user inputs (sliders, buttons, text inputs)
- **Reactivity**: Automatic updates when inputs change
- **Data visualization**: Seamless integration with popular graphing libraries
- **State management**: Session state to maintain application state between runs
- **Deployment options**: Easy implementation through Streamlit Cloud or other services

</v-clicks>

---
layout: full
---

<video controls autoplay loop src="https://s3-us-west-2.amazonaws.com/assets.streamlit.io/videos/hero-video.mp4" />

---

# Chainlit

Chainlit is a Python framework specifically designed for building conversational AI applications.

<v-clicks>

- **Focused on LLM applications**: Optimized for building chatbots and conversational interfaces
- **Conversation management**: Built-in features for handling contexts and chat histories
- **UI components**: Prefabricated elements for chat interfaces
- **Message streaming**: Support for streaming responses from language models
- **Multi-modal**: Handles text, images, and file attachments in conversations
- **Integration with LLM libraries**: Works well with LangChain, LlamaIndex, and other LLM frameworks
- **Debugging tools**: Tools to help track and debug LLM application execution
- **Cloud deployment**: Deployment options similar to Streamlit

</v-clicks>

---
layout: full
---

<video controls autoplay loop src="https://mintlify.s3.us-west-1.amazonaws.com/chainlit-43/images/overview.mp4" />

---

# Decision Table

<v-clicks>

| **Need** | **Best Option** |
|---------------|------------------|
| Chat or conversational application | Chainlit |
| Data visualization | Streamlit |
| Interactive dashboards | Streamlit |
| Interfaces for ML models | Streamlit |
| Advanced integration with LLMs | Chainlit |
| Larger community and resources | Streamlit |
| Chat-optimized interfaces | Chainlit |

</v-clicks>

---

# Quick Guide

## **Streamlit** for: data applications, visualizations, and dashboards
## **Chainlit** for: chatbots and conversational interfaces

---
layout: image
image: https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExeDBkYXV6aHNldmk0ajU0M2J2cDc4Y3pmOWtuZG85NDkzeTJpYWYyeiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/da75JuW2HHuBNqOHHE/giphy.gif
---

<!-- Demo Chainlit -->

---

# Chainlit and Ollama

```python {*}{maxHeight:'45vh'}
import chainlit as cl
import requests
import json


@cl.on_chat_start
def start_chat():
    # Initialize the message history with a system prompt
    cl.user_session.set(
        "message_history",
        [{"role": "system", "content": "You are a helpful assistant."}],
    )


@cl.on_message
async def main(message: cl.Message):
    # Get the current message history
    message_history = cl.user_session.get("message_history")

    # Add the user's new message to history
    message_history.append({"role": "user", "content": message.content})

    # Create a message object for streaming
    msg = cl.Message(content="")

    try:
        # Set up the request to Ollama's API
        response = requests.post(
            "http://localhost:11434/api/chat",  # Using the chat endpoint instead of generate
            json={
                "model": "llama3.2",  # Change to your preferred model
                "messages": message_history,  # Pass the entire message history
                "stream": True,  # Enable streaming
            },
            stream=True,  # Important for requests to stream the response
        )

        # Prepare to collect the full response
        full_response = ""

        # Process the streaming response
        for line in response.iter_lines():
            if line:
                # Parse the JSON line
                json_line = json.loads(line)

                # Check if this is a content token
                if "message" in json_line and "content" in json_line["message"]:
                    token = json_line["message"]["content"]
                    full_response += token
                    # Stream the token to the UI
                    await msg.stream_token(token)

                # Check if this is the end of the stream
                if json_line.get("done", False):
                    break

        # Add the assistant's response to the message history
        message_history.append({"role": "assistant", "content": full_response})

        # Update the session with the new message history
        cl.user_session.set("message_history", message_history)

        # Update the message (this is required even with streaming)
        await msg.update()

    except Exception as e:
        # Handle any errors
        await cl.Message(content=f"Error: {str(e)}", author="System").send()
```

---
layout: cover
background: https://images.unsplash.com/photo-1636690513351-0af1763f6237?q=80&w=1920&fit=crop
---

# AI Frameworks

---

# Why use a Framework

<v-clicks>

- **Simplicity**: Less repetitive code with clear structure and patterns
- **Integrated Memory**: Automatic management of conversation history and context
- **Developer Experience**: Type safety and IDE support for faster development
- **Error Handling**: Robust retry logic and elegant failure management
- **Flexibility**: Easy switching between models and provider abstraction
- **Advanced Features**: Simplified access to function calls, RAG, and other techniques
- **Community Support**: Documentation, examples, and continuous maintenance

</v-clicks>

---
layout: two-cols-header
---

# Popular Frameworks

::left::

<v-clicks>

* LangChain
* LangGraph
* LlamaIndex
* CrewAI
* Microsoft AutoGen
* Phidata
* PydanticAI
* OpenAI Agents

</v-clicks>

::right::

<v-click>

![Jackie Chan](https://i.imgflip.com/qiev6.jpg?a483912)

And the list goes on and on...

</v-click>

---
layout: iframe
url: https://aiagentsdirectory.com/category/ai-agents-frameworks
---

---
layout: statement
---

## But... Which one is the **best**?

<v-clicks>

# The one you like the most

## Actually... The one with the best community

## The important thing is to choose one and **start**

</v-clicks>

---

# **OpenAI** Agents SDK

The **OpenAI** Agents SDK is a lightweight but powerful framework for building multi-agent workflows with LLMs that offers a structured approach to creating, managing, and implementing AI agents.

<v-clicks>

- **Agents**: LLMs configured with instructions, tools, guardrails, and handoffs
- **Guardrails**: Configurable safety checks for input/output validation
- **Handoffs**: Specialized tool calls to transfer control between agents
- **Compatibility**: Works with any model provider that supports OpenAI's Chat Completions API
- **Simple Implementation**: Easy to set up and get started with minimal code
- **Flexible Agent Patterns**: Supports deterministic flows, iterative loops, and more
- **Integrated Debugging**: Complete tracing system with external integrations

</v-clicks>

---

# Agents

Agents are the fundamental building block in your applications. An agent is a large language model (LLM), configured with instructions and tools.

## Basic configuration

The most common agent properties you'll configure are:

* `instructions`: also known as developer message or system prompt.
* `model`: which LLM to use, and optional `model_settings` to configure model tuning parameters like temperature, top_p, etc.
* `tools`: Tools that the agent can use to accomplish its tasks.

---

# Example: Hello World

```python
from agents import Agent, ModelSettings, function_tool

@function_tool
def get_weather(city: str) -> str:
    return f"The weather in {city} is sunny"

agent = Agent(
    name="Haiku agent",
    instructions="Always respond in haiku form",
    model="o3-mini",
    tools=[get_weather],
)
```

---

# Integration with **Ollama**

```python
from agents import Agent, OpenAIChatCompletionsModel, Runner, AsyncOpenAI

model = OpenAIChatCompletionsModel(
    model="llama3.2",
    openai_client=AsyncOpenAI(
        base_url="http://localhost:11434/v1",
        api_key="NOT_AN_API_KEY",
    ),
)

agent = Agent(
    name="Assistant",
    instructions="You are a helpful assistant",
    model=model
)
```

---

# Integration with **Chainlit**

```python {*}{maxHeight:'45vh'}
from agents import Agent, OpenAIChatCompletionsModel, AsyncOpenAI, Runner
import chainlit as cl
from openai.types.responses import ResponseTextDeltaEvent

model = OpenAIChatCompletionsModel(
    model="llama3.2",
    openai_client=AsyncOpenAI(base_url="http://localhost:11434/v1", api_key="mock"),
)

agent = Agent(
    name="News Assistant",
    instructions="You are a helpful assistant.",
    model=model,
)


@cl.on_chat_start
def start_chat():
    cl.user_session.set("message_history", [])


@cl.on_message
async def main(message: cl.Message):
    # Get the current message history
    message_history = cl.user_session.get("message_history")

    # Add the user's new message to history
    message_history.append({"role": "user", "content": message.content})

    # Create a message object for streaming
    msg = cl.Message(content="")

    # Prepare to collect the full response
    full_response = ""

    response = Runner.run_streamed(agent, input=message_history)

    try:
        async for event in response.stream_events():
            if event.type == "raw_response_event" and isinstance(
                event.data, ResponseTextDeltaEvent
            ):
                full_response += event.data.delta
                await msg.stream_token(event.data.delta)

        message_history.append({"role": "assistant", "content": full_response})

        # Update the session with the new message history
        cl.user_session.set("message_history", message_history)

        # Update the message (this is required even with streaming)
        await msg.update()

    except Exception as e:
        # Handle any errors
        await cl.Message(content=f"Error: {str(e)}", author="System").send()
```

---

# Practical Activity

<v-clicks>

1. Install [Ollama](https://ollama.com/) and [MSTY](https://msty.app/)
1. Download a [model](https://ollama.com/models) that suits your system
1. Chat with your model using MSTY
1. Clone the [practice repository](https://github.com/EmaSuriano/chainlit-ollama-demo/tree/main)
1. Implement a specific functionality using [OpenAI Agents SDK](https://openai.github.io/openai-agents-python)
1. Present your project to the group

</v-clicks>

---
layout: cover
background: https://images.unsplash.com/photo-1636690581110-a512fed05fd3?q=80&w=1920&auto=format&fit=crop
---

# Thank You for Participating!

## Workshop by [EmaSuriano](https://emasuriano.com)

---