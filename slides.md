---
theme: slidev-theme-nearform
background: https://images.unsplash.com/photo-1636690581110-a512fed05fd3?q=80&w=1920&auto=format&fit=crop
title: Introducción Práctica a LLMs con Ollama
info: Workshop por EmaSuriano
transition: slide-left
---

# Introducción Práctica a LLMs con Ollama

## Workshop por [EmaSuriano](https://emasuriano.com)

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/EmaSuriano/workshop-ollama" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

---

# ¿Qué haremos hoy?

- Entender qué son los LLMs locales y por qué son importantes
- Instalar y configurar Ollama en tu computadora
- Experimentar con diferentes modelos de lenguaje
- Crear interfaces gráficas para interactuar con tus modelos
- Desarrollar aplicaciones prácticas con IA local

---

# ¿Por qué LLMs Locales?

- **Privacidad**: Tus datos nunca salen de tu computadora
- **Sin conexión**: Funcionan sin necesidad de internet
- **Personalización**: Control total sobre los modelos y parámetros
- **Economía**: Sin costos recurrentes por llamadas a APIs
- **Latencia**: Respuestas más rápidas sin depender de servidores externos

---

# Comparativa: Local vs Cloud

<v-clicks>

| Característica | LLMs Locales | LLMs en la Nube |
|----------------|--------------|-----------------|
| Privacidad     | ✅ Total     | ❌ Limitada     |
| Potencia       | ⚠️ Limitada por hardware | ✅ Alta |
| Costo          | ✅ Gratis/Único | ❌ Suscripción |
| Personalización| ✅ Completa   | ⚠️ Limitada    |
| Facilidad      | ⚠️ Más técnico | ✅ Sencillo    |
| Disponibilidad | ✅ 24/7 Offline | ❌ Requiere internet |

</v-clicks>

---
layout: two-cols-header
---

# Requisitos Técnicos

::left::

## Mínimos:

- CPU moderno (4+ cores)
- 8GB RAM
- 10GB espacio libre
- Sistema operativo compatible

::right::

## Recomendados:

- GPU NVIDIA (CUDA)
- 16GB+ RAM
- 50GB+ espacio libre

---
layout: image-right
image: ./assets/ollama.png
---

# **Ollama**: Tu Plataforma de LLMs Locales

- Framework open source para ejecutar LLMs localmente
- Soporte para múltiples modelos (Llama, Mistral, Phi, etc.)
- API simple y potente
- Interfaz de línea de comandos intuitiva

---
layout: image-right
image: ./assets/ollama-install.png
---

# Instalación de Ollama


Ollama tiene soporte para todos los Sistemas Operativos: 

* [Mac](https://ollama.com/download/mac)
* [Linux](https://ollama.com/download/linux)
* [Windows](https://ollama.com/download/windows)


---

# Primeros Pasos con Ollama

Ollama en si no tiene una interfaz, por lo que la forma de comunicarnos es usando la consola: 

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

# Workflow normal de trabajo con modelos 

<v-clicks every="2">

## 1. Descargar un modelo

```bash
> ollama pull llama3.2
```

## 2. Iniciar una conversación
```bash
> ollama run llama3.2
>>> Hi
How can I help you today?
```

## 3. Consultar desde la terminal

```bash
> ollama run llama3.2 "Contame un chiste bueno"
¡Claro! Aquí tienes uno:
¿Por qué la computadora fue al doctor?
¡Porque tenía un virus!
Espero que te haya hecho sonreír. ¿Quieres escuchar otro?
```

</v-clicks >

---
layout: image-right
image: ./assets/ollama-models.png
---

# Modelos Populares en Ollama

- **Mistral** - Balanceado en tamaño y rendimiento
- **Llama** - Varias versiones y tamaños disponibles
- **Phi** - Compacto pero potente
- **Gemma** - El modelo abierto de Google
- **Deepseek-r1** - Modelo chino con razonamiento

---
layout: image
image: https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExbWRwbzU0b2MweDBqdWFjZmU0NzVuMHlveTdiM3BtYWpvOHc0eGJqcSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/fxqt51CAMGITJlxcRI/giphy.gif
---

<!-- Demo Ollama -->

---
layout: quote
---

# "Todo muy lindo, pero esto no se parece a Chat GPT"

-. Dicho por todo el mundo ...

---
layout: iframe-right
url: https://msty.app/
---

# MSTY 

Es la forma más sencilla de usar modelos de IA locales y en línea con integración perfecta de Ollama y sin necesidad de configuración técnica.

## Features

- Sin configuración técnica (sin Docker, sin terminal)
- Compara múltiples respuestas de IA lado a lado
- Importa archivos y conecta fuentes de conocimiento
- Mejor UX para Ollama

---
layout: iframe
url: https://docs.msty.app/getting-started/download
---

# MSTY: Instalación

---
layout: image
image: https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExcm5tdnp0dGt1anU2Z2ZwcXBvejhreW42cDZsNm8wODNxOTdpYXJwYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/WcpaItX5JHYkw/giphy.gif
---

<!-- Demo MSTY -->

---
layout: quote
---

# "Todo muy lindo, pero como hago una aplicación?"

-. Dicho por los devs ...

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

# Stack de una aplicación (real)

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
* Ollama: ya lo vimos 

</v-click>

---

# Stack de una aplicación (workshop)

## Frontend + Backend

* Frontend: Chainlit / Streamlit ✨
* Application Layer + Database
* AI Layer: 🎁
* Ollama: ya lo vimos 


---

# Streamlit

Streamlit es un framework de Python para construir rápidamente aplicaciones web interactivas para ciencia de datos e inteligencia artificial.

- **Simplicidad**: Crea aplicaciones web con Python puro (sin necesidad de HTML/CSS/JS)
- **Prototipado rápido**: Convierte scripts de datos en aplicaciones web compartibles en minutos
- **Elementos interactivos**: Widgets incorporados para entradas de usuario (deslizadores, botones, entradas de texto)
- **Reactividad**: Actualizaciones automáticas cuando cambian las entradas
- **Visualización de datos**: Integración perfecta con bibliotecas populares de gráficos
- **Gestión de estado**: Estado de sesión para mantener el estado de la aplicación entre ejecuciones
- **Opciones de despliegue**: Fácil implementación a través de Streamlit Cloud u otros servicios

---
layout: full
---

<video controls autoplay loop src="https://s3-us-west-2.amazonaws.com/assets.streamlit.io/videos/hero-video.mp4" />

---

# Chainlit

Chainlit es un framework de Python diseñado específicamente para construir aplicaciones de IA conversacional.

- **Enfocado en aplicaciones LLM**: Optimizado para construir chatbots e interfaces conversacionales
- **Gestión de conversaciones**: Características incorporadas para manejar contextos e historiales de chat
- **Componentes de UI**: Elementos prefabricados para interfaces de chat
- **Transmisión de mensajes**: Soporte para transmitir respuestas desde modelos de lenguaje
- **Multi-modal**: Maneja texto, imágenes y archivos adjuntos en conversaciones
- **Integración con bibliotecas LLM**: Funciona bien con LangChain, LlamaIndex y otros frameworks de LLM
- **Herramientas de depuración**: Herramientas para ayudar a rastrear y depurar la ejecución de aplicaciones LLM
- **Despliegue en la nube**: Opciones de implementación similares a Streamlit

---
layout: full
---

<video controls autoplay loop src="https://mintlify.s3.us-west-1.amazonaws.com/chainlit-43/images/overview.mp4" />

---

# Tabla de Decisión

<v-clicks>


| **Necesidad** | **Mejor Opción** |
|---------------|------------------|
| Aplicación de chat o conversacional | Chainlit |
| Visualización de datos | Streamlit |
| Tableros interactivos | Streamlit |
| Interfaces para modelos ML | Streamlit |
| Integración avanzada con LLMs | Chainlit |
| Mayor comunidad y recursos | Streamlit |
| Interfaces optimizadas para chat | Chainlit |


</v-clicks>

---

# Guía Rápida

##  **Streamlit** para: aplicaciones de datos, visualizaciones y dashboards
##  **Chainlit** para: chatbots e interfaces conversacionales

---
layout: image
image: https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExeDBkYXV6aHNldmk0ajU0M2J2cDc4Y3pmOWtuZG85NDkzeTJpYWYyeiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/da75JuW2HHuBNqOHHE/giphy.gif
---

<!-- Demo Chainlit -->

---

# Chainlit y Ollama

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

# Porque usar un Framework

- **Simplicidad**: Menos código repetitivo con estructura y patrones claros
- **Memoria Integrada**: Gestión automática del historial de conversaciones y contexto
- **Experiencia del Desarrollador**: Seguridad de tipos y soporte IDE para desarrollo más rápido
- **Manejo de Errores**: Lógica robusta de reintentos y gestión elegante de fallos
- **Flexibilidad**: Cambio sencillo entre modelos y abstracción de proveedores
- **Funciones Avanzadas**: Acceso simplificado a llamadas de funciones, RAG y otras técnicas
- **Soporte Comunitario**: Documentación, ejemplos y mantenimiento continuo

---
layout: two-cols
---
# Popular Frameworks

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

Y la lista sigue y sigue ...

</v-click>

---
layout: iframe
url: https://aiagentsdirectory.com/category/ai-agents-frameworks
---

---
layout: statement
---

## Pero... Cual es el **mejor**?

<v-clicks>

# El que mas te guste

## En realidad ... El que mejor comunidad tenga

## Lo importante es eligir uno y **empezar**

</v-clicks>

---

# **OpenAI** Agents SDK


El SDK de Agentes de **OpenAI** es un framework ligero pero potente para construir flujos de trabajo multi-agente con LLMs que ofrece un enfoque estructurado para crear, gestionar e implementar agentes de IA.

<v-clicks>

- **Agents**: LLMs configurados con instructions, tools, guardrails, y handoffs
- **Guardrails**: Verificaciones de seguridad configurables para validación de input/output
- **Handoffs**: Llamadas especializadas de tools para transferir el control entre agents
- **Compatibilidad**: Funciona con cualquier proveedor de modelos que soporte la API de Chat Completions de OpenAI
- **Implementación Sencilla**: Fácil de configurar y comenzar con código mínimo
- **Patrones de Agents Flexibles**: Soporta flujos deterministas, bucles iterativos y más
- **Depuración Integrada**: Sistema de tracing completo con integraciones externas

</v-clicks>

---

# Agents

Los Agents son el bloque de construcción fundamental en tus aplicaciones. Un agent es un modelo de lenguaje grande (LLM), configurado con instructions y tools.

## Configuración básica

Las propiedades más comunes de un agent que configurarás son:

* `instructions`: también conocido como developer message o system prompt.
* `model`: qué LLM usar, y `model_settings` opcionales para configurar parámetros de ajuste del modelo como temperature, top_p, etc.
* `tools`: Tools que el agent puede usar para lograr sus tareas.

---

# Ejemplo: Hola Mundo

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

# Integración con **Ollama**

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

# Integración con **Chainlit**

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

# Actividad Práctica

1. Instala [Ollama](https://ollama.com/) y [MSTY](https://msty.app/)
1. Descarga un [modelo](https://ollama.com/models) que se adapte a tu sistema
1. Chatea con tu modelo usando MSTY
1. Clona el [repositorio de práctica](https://github.com/EmaSuriano/chainlit-ollama-demo/tree/main)
1. Implementa una funcionalidad específica usando [OpenAI Agents SDK](https://openai.github.io/openai-agents-python)
1. Presenta tu proyecto al grupo

¡Tienes 45 minutos!

---
layout: cover
background: https://images.unsplash.com/photo-1636690581110-a512fed05fd3?q=80&w=1920&auto=format&fit=crop
---

# ¡Gracias por Participar!

## Workshop por [EmaSuriano](https://emasuriano.com)

---