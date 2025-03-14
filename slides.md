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

| Característica | LLMs Locales | LLMs en la Nube |
|----------------|--------------|-----------------|
| Privacidad     | ✅ Total     | ❌ Limitada     |
| Potencia       | ⚠️ Limitada por hardware | ✅ Alta |
| Costo          | ✅ Gratis/Único | ❌ Suscripción |
| Personalización| ✅ Completa   | ⚠️ Limitada    |
| Facilidad      | ⚠️ Más técnico | ✅ Sencillo    |
| Disponibilidad | ✅ 24/7 Offline | ❌ Requiere internet |

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

# Ollama: Tu Plataforma de LLMs Locales

- Framework open source para ejecutar LLMs localmente
- Soporte para múltiples modelos (Llama, Mistral, Phi, etc.)
- API simple y potente
- Interfaz de línea de comandos intuitiva

---
layout: two-cols-header
---

# Instalación de Ollama

::left::

## Windows

- Instalar WSL2
- Seguir instrucciones para Linux
- Alternativa: Descargar desde [ollama.com](https://ollama.com)

::right::

## Linux | MacOS
```bash
curl -fsSL https://ollama.com/install.sh | sh
```


---

# Primeros Pasos con Ollama

<v-clicks every="2">

## 1. Descargar un modelo

```bash
ollama pull mistral
```

## 2. Iniciar una conversación
```bash
ollama run mistral
```

## 3. Consultar desde la terminal

```bash
ollama run mistral "Explica qué es un LLM en 3 líneas"
```

</v-clicks >

---

# Modelos Populares en Ollama

- **Mistral** - Balanceado en tamaño y rendimiento
- **Llama** - Varias versiones y tamaños disponibles
- **Phi** - Compacto pero potente
- **Gemma** - El modelo abierto de Google
- **Nous-Hermes** - Optimizado para programación
- **Codellama** - Especializado en código

---

# Personalización de Modelos

## Modelfile
```
FROM mistral
SYSTEM Eres un asistente experto en Python que siempre responde con código
```

## Crear modelo personalizado
```bash
ollama create python-expert -f Modelfile
```

## Ejecutar modelo personalizado
```bash
ollama run python-expert
```

---

# Interfaces de Usuario: Streamlit

![Streamlit Logo](https://streamlit.io/images/brand/streamlit-logo-primary-colormark-darktext.png)

- Framework Python para crear aplicaciones web interactivas
- Perfecto para prototipos rápidos
- Componentes interactivos integrados
- Fácil visualización de datos

---

# Ejemplo Básico con Streamlit

```python
import streamlit as st
from ollama import Client

st.title("Mi Asistente con LLM Local")

# Inicializar cliente de Ollama
client = Client(host="http://localhost:11434")

# Interfaz de usuario
prompt = st.text_input("Tu pregunta:", 
                     placeholder="¿Qué quieres saber?")

if st.button("Generar respuesta"):
    with st.spinner("Pensando..."):
        response = client.chat(model="mistral", 
                            messages=[{"role": "user", "content": prompt}])
        st.write(response["message"]["content"])
```

---

# Componentes Interactivos de Streamlit

- **Entradas**: Text inputs, sliders, selectors
- **Visualización**: Charts, tables, maps
- **Media**: Images, audio, video
- **Layouts**: Columns, tabs, expandable sections
- **Estado**: Session state para persistencia
- **Deployment**: Fácil de implementar en la nube

---

# Demo: Interfaz Avanzada

- Selección de modelos
- Historial de chat persistente
- Configuración de parámetros (temperatura, tokens)
- Exportación de resultados
- Visualización de latencia y tokens

---

# Agentic AI con phidata

![Phidata Logo](https://docs.phidata.com/img/phidata-logo.png)

- Framework para construir agentes AI autónomos
- Integración directa con Ollama
- Workflows inteligentes
- Personalizable y extensible

---

# Creación de un Agente Básico

```python
from phi.assistant import Assistant

# Crear un asistente con modelo local
assistant = Assistant(
    name="Asistente Python",
    llm="ollama/codellama",
    description="Experto en Python y resolución de problemas",
    instructions="""
    - Ayuda con código Python
    - Explica conceptos de programación
    - Sugiere buenas prácticas
    """
)

# Interactuar con el asistente
response = assistant.run("Escribe una función que calcule fibonacci")
print(response)
```

---

# Funcionalidades de los Agentes

- **Memoria**: Recordar conversaciones previas
- **Herramientas**: Acceso a APIs, bases de datos, búsqueda
- **Workflows**: Secuencias automáticas de tareas
- **Retroalimentación**: Aprendizaje por refuerzo
- **Multi-agente**: Colaboración entre agentes

---

# Desarrollo de APIs con FastAPI

![FastAPI Logo](https://fastapi.tiangolo.com/img/logo-margin/logo-teal.png)

- Framework moderno para APIs en Python
- Alto rendimiento con Async/Await
- Documentación automática con Swagger
- Validación de datos integrada
- Fácil integración con Ollama

---

# Ejemplo de API con FastAPI

```python
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel
from ollama import Client

app = FastAPI()
client = Client()

class Query(BaseModel):
    prompt: str
    model: str = "mistral"
    temperature: float = 0.7

@app.post("/generate")
async def generate_response(query: Query):
    try:
        response = client.chat(
            model=query.model,
            messages=[{"role": "user", "content": query.prompt}],
            temperature=query.temperature
        )
        return {"response": response["message"]["content"]}
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))
```

---

# Integración Frontend-Backend

- **React/Vue/Angular**: Frontend moderno
- **WebSockets**: Para streaming de respuestas
- **Gestión de estado**: Control de sesiones y contexto
- **Responsivo**: Adaptable a móviles y desktop
- **Microservicios**: Arquitectura escalable

---

# Mejores Prácticas

- **Optimización de prompts**: Instrucciones claras y específicas
- **Gestión de contexto**: Limitar tamaño para rendimiento
- **Caching**: Almacenar respuestas comunes
- **Monitoreo**: Tracking de uso y rendimiento
- **Fallbacks**: Plan B cuando el modelo falla
- **Feedback loop**: Mejora continua basada en uso real

---

# Casos de Uso Prácticos

- **Asistente de programación personal**
- **Análisis de documentos locales**
- **Generación de contenido sin conexión**
- **Chatbots personalizados para equipos**
- **Automatización de tareas repetitivas**
- **Educación y entrenamiento interactivo**

---

# Recursos Adicionales

- [Documentación de Ollama](https://github.com/ollama/ollama)
- [Streamlit Tutorial](https://docs.streamlit.io/)
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Phidata Agents Guide](https://docs.phidata.com/)
- [Hugging Face - Modelos Open Source](https://huggingface.co/)
- [Comunidad Discord Workshop](https://discord.gg/workshop)

---

# Actividad Práctica

1. Instala Ollama y descarga un modelo
2. Crea una interfaz simple con Streamlit
3. Implementa una funcionalidad específica
4. Presenta tu proyecto al grupo

¡Tienes 45 minutos!

---

# ¡Gracias por Participar!

## Contacto:
- Email: workshop@example.com
- Twitter: @workshop_ai
- GitHub: github.com/workshop-ai

## Próximos Eventos:
- Embeddings y recuperación de información
- Fine-tuning de modelos locales
- Deployment en producción

---
layout: fact
---

# Q&A