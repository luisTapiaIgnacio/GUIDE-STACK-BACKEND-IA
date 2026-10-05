# 🚀 Ruta de preparación: Backend con Python + IA + RAG

> **Objetivo:** prepararme desde una base inicial hasta un nivel junior–medio para una entrevista y, si soy seleccionado, poder entender el flujo de trabajo real de un proyecto de IA aplicado a documentos.

---

# 1. 🎯 ¿Qué tipo de proyecto es?

Por las tecnologías de la oferta, el proyecto parece ser una aplicación de **IA aplicada a documentos**, probablemente con una arquitectura similar a:

```text
                         👤 USUARIO
                             │
                             ▼
                     ┌───────────────┐
                     │    React      │
                     │ Chat + Docs   │
                     └───────┬───────┘
                             │
                             ▼
                     ┌───────────────┐
                     │    FastAPI    │
                     │    Backend    │
                     └───────┬───────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
          Documentos        RAG        Autenticación
              │              │
              ▼              ▼
           PDF/OCR       Embeddings
              │              │
              ▼              ▼
          Chunking      Vector DB
                             │
                             ▼
                     Búsqueda semántica
                             │
                             ▼
                          Contexto
                             │
                             ▼
                       OpenAI / Claude
                             │
                             ▼
                         Respuesta
```

La idea central sería:

> **El usuario sube documentos, el sistema los procesa y posteriormente puede hacer preguntas sobre ellos.**

---

# 2. 👨‍💻 ¿Qué perfil profesional parece buscar la empresa?

No parece que busquen necesariamente a un investigador de Machine Learning que entrene modelos desde cero.

El perfil parece más cercano a:

- **AI Application Developer**
- **Backend Developer con IA**
- **AI Engineer orientado a aplicaciones**
- **Python / LLM / RAG Developer**

## Diferencia entre perfiles

| Perfil | Principal responsabilidad |
|---|---|
| Backend Developer | APIs, lógica, BD, servicios |
| AI Application Developer | Integrar IA dentro de aplicaciones |
| AI/ML Engineer | Modelos, entrenamiento, evaluación y optimización |
| Data Engineer | Preparación y procesamiento de datos |
| RAG Engineer | Recuperación de información + generación |

La oferta parece combinar principalmente:

**Backend + IA aplicada + RAG + integración con LLM.**

---

# 3. 🧠 ¿Qué nivel de IA necesito?

### Junior

- Consumir APIs de modelos.
- Entender prompts.
- Procesar documentos.
- Usar embeddings.
- Construir un RAG básico.

### Junior–Mid

- Diseñar chunking.
- Elegir estrategia de recuperación.
- Trabajar con vector DB.
- Integrar LLM.
- Manejar streaming.
- Diseñar APIs para el sistema.

### Avanzado

- Evaluación de RAG.
- Optimización de recuperación.
- Costos.
- Latencia.
- Seguridad.
- Observabilidad.
- Escalabilidad.
- Evaluación automática.

**Para una entrevista junior no necesitas dominar el nivel avanzado.**

Lo importante es poder explicar el flujo completo y construir una versión funcional.

---

# 4. 📚 Tecnologías mencionadas en la oferta

La oferta pide:

```text
Python avanzado
      │
      ├── FastAPI / Django
      │
      ├── PDF / documentos
      │      └── OCR
      │
      ├── RAG
      │      ├── embeddings
      │      ├── chunking
      │      ├── vector DB
      │      └── búsqueda semántica
      │
      ├── OpenAI / Anthropic / otros LLM
      │
      ├── Chat
      │      ├── historial
      │      └── streaming
      │
      └── Integración con sistemas existentes
```

No debemos aprender todo al mismo tiempo.

---

# 5. 🗺️ Ruta general de aprendizaje

La ruta que recomiendo:

```text
FASE 1
Fundamentos de IA
        ↓
FASE 2
Python + Backend
        ↓
FASE 3
FastAPI
        ↓
FASE 4
PDF + OCR
        ↓
FASE 5
Chunking
        ↓
FASE 6
Embeddings
        ↓
FASE 7
Vector DB
        ↓
FASE 8
RAG
        ↓
FASE 9
OpenAI / Anthropic
        ↓
FASE 10
Chat + Streaming
        ↓
FASE 11
React + integración
        ↓
FASE 12
Pruebas + deploy
```

---

# 6. 🏗️ El proyecto práctico que usaremos

En lugar de estudiar cada tecnología de forma aislada, construiremos un proyecto:

# 🤖 AI Document Assistant

Una aplicación donde:

1. El usuario inicia sesión.
2. Sube un PDF.
3. El sistema procesa el documento.
4. Extrae texto.
5. Si es necesario utiliza OCR.
6. Divide el texto.
7. Genera embeddings.
8. Guarda los vectores.
9. El usuario hace una pregunta.
10. El sistema busca información relevante.
11. Construye el contexto.
12. Envía el contexto al LLM.
13. El LLM genera la respuesta.
14. La respuesta aparece progresivamente en el chat.
15. Se conserva el historial.

---

# 7. 🧩 El flujo completo explicado de forma sencilla

## PARTE A — Preparación del documento

```text
                 PDF
                  │
                  ▼
          ¿Tiene texto?
             /       \
           Sí         No
           │           │
           ▼           ▼
      Extraer texto   OCR
           │           │
           └─────┬─────┘
                 ▼
             Texto limpio
                 │
                 ▼
              Chunking
                 │
                 ▼
             Embeddings
                 │
                 ▼
             Vector DB
```

Esta parte se ejecuta principalmente cuando se carga o actualiza un documento.

---

# 8. 📄 PDF y procesamiento de documentos

Un PDF puede ser de dos tipos:

### PDF con texto

El texto puede seleccionarse y extraerse directamente.

```text
PDF
 ↓
Extractor
 ↓
Texto
```

### PDF escaneado

La página puede ser simplemente una imagen.

```text
PDF
 ↓
Imagen
 ↓
OCR
 ↓
Texto
```

Por eso la oferta menciona **OCR**.

---

# 9. ✂️ ¿Qué es chunking?

No conviene convertir un documento enorme en un solo bloque.

Ejemplo:

```text
Documento de 100 páginas
          ↓
       Chunking
          ↓
 ┌────────┬────────┬────────┐
 │Chunk 1 │Chunk 2 │Chunk 3 │ ...
 └────────┴────────┴────────┘
```

Cada chunk debería contener una cantidad razonable de información y conservar suficiente contexto.

También podemos almacenar:

```text
chunk
+
document_id
+
page
+
metadata
```

---

# 10. 🔢 ¿Qué son los embeddings?

Un embedding transforma un texto en un vector numérico.

Ejemplo conceptual:

```text
"El trabajador tiene 30 días de vacaciones"
                    │
                    ▼
              Embedding Model
                    │
                    ▼
       [0.12, -0.72, 0.45, ...]
```

La idea es que textos con significados similares tengan vectores cercanos.

Ejemplo:

```text
"¿Cuántos días de vacaciones tengo?"

        ≈

"El trabajador tiene derecho a 30 días
 de descanso anual."
```

Aunque no utilicen exactamente las mismas palabras, existe una relación semántica.

---

# 11. 🔎 ¿Qué es búsqueda semántica?

Una búsqueda tradicional puede buscar coincidencias de palabras.

Una búsqueda semántica busca por **significado**.

Ejemplo:

```text
Pregunta:
"¿Cuántos días de vacaciones tiene el empleado?"
```

El documento dice:

```text
"El trabajador tiene derecho a treinta días
de descanso remunerado..."
```

La búsqueda semántica puede identificar que ambos textos están relacionados.

---

# 12. 🗄️ Vector Database

Necesitamos almacenar los embeddings y poder buscar vectores similares.

Opciones:

- PostgreSQL + pgvector
- Qdrant
- Pinecone
- Weaviate
- Milvus
- Chroma

Para este aprendizaje recomiendo comenzar con:

> **PostgreSQL + pgvector**

porque permite aprovechar conocimientos previos de PostgreSQL.

Una estructura conceptual:

```text
document_chunks
--------------------------------
id
document_id
page
content
embedding
metadata
created_at
```

---

# 13. 🧠 ¿Qué es RAG?

RAG significa:

> **Retrieval-Augmented Generation**

En español:

> **Generación aumentada mediante recuperación de información.**

La idea es:

```text
Pregunta
   │
   ▼
Embedding de la pregunta
   │
   ▼
Búsqueda vectorial
   │
   ▼
Chunks relevantes
   │
   ▼
Contexto
   │
   ▼
LLM
   │
   ▼
Respuesta
```

RAG permite que el LLM responda utilizando información recuperada de documentos externos.

---

# 14. ❓ ¿Por qué no enviar todo el PDF al GPT?

Porque:

- Puede ser demasiado grande.
- Consume más tokens.
- Aumenta costos.
- Puede dificultar encontrar la información relevante.
- Puede superar la ventana de contexto.
- No es eficiente.

Con RAG:

```text
Documento 500 páginas
        ↓
Pregunta
        ↓
Buscar solamente información relevante
        ↓
5–10 chunks
        ↓
LLM
```

Es mucho más eficiente.

---

# 15. 🤖 Integración con OpenAI / Anthropic

El backend puede comunicarse con un proveedor de modelos mediante API.

Flujo:

```text
React
  │
  ▼
FastAPI
  │
  ├── autentica usuario
  │
  ├── ejecuta RAG
  │
  └── prepara contexto
          │
          ▼
    OpenAI / Anthropic
          │
          ▼
       Respuesta
          │
          ▼
        React
```

La API key debe permanecer en el backend.

Nunca debemos colocar una API key privada directamente en React.

---

# 16. 🧾 Prompt + contexto

Un prompt de RAG puede conceptualmente verse así:

```text
SYSTEM:

Responde utilizando únicamente la información
proporcionada en el contexto.

Si el contexto no contiene suficiente información,
indícalo.

CONTEXTO:

[Documento: reglamento.pdf]
[Página 12]

La empresa otorga a sus trabajadores treinta
días calendario de vacaciones...

PREGUNTA:

¿Cuántos días de vacaciones corresponden?
```

El LLM utilizará el contexto para generar la respuesta.

---

# 17. ⚡ Streaming

Sin streaming:

```text
Usuario
   ↓
espera
   ↓
respuesta completa
```

Con streaming:

```text
Usuario
   ↓
"Según..."
"el documento..."
"el trabajador..."
"tiene derecho..."
```

La respuesta aparece progresivamente.

Tecnologías posibles:

- SSE
- WebSockets

Para un chat de LLM, SSE es una opción común.

---

# 18. 💬 Chat

Una vez funcionando el RAG:

```text
┌──────────────────────────────────────────┐
│ AI DOCUMENT ASSISTANT                    │
├────────────────┬─────────────────────────┤
│ DOCUMENTOS     │ CHAT                    │
│                │                         │
│ contrato.pdf   │ Tú: ¿Cuánto dura...?    │
│ manual.pdf     │                         │
│ reglamento.pdf │ IA: Según el documento…│
│                │                         │
│ [+ Subir]      │                         │
└────────────────┴─────────────────────────┘
```

---

# 19. 🏢 Flujo profesional de trabajo

Ahora viene una de las partes más importantes.

Si mañana entras a una empresa, **no empiezas programando inmediatamente**.

El flujo sería:

```text
1. Requerimientos
       ↓
2. Definir alcance
       ↓
3. MVP
       ↓
4. Arquitectura
       ↓
5. División de tareas
       ↓
6. Preparar entorno
       ↓
7. Desarrollo
       ↓
8. Pruebas
       ↓
9. Code Review
       ↓
10. Integración
       ↓
11. Deploy
       ↓
12. Documentación
```

---

# 20. 👥 Etapa 1 — Reunión de requerimientos

Preguntas importantes:

1. ¿Quién utilizará el sistema?
2. ¿Qué documentos se procesarán?
3. ¿Cuántos documentos habrá?
4. ¿Qué tamaño tendrán?
5. ¿Los PDF contienen texto o son escaneados?
6. ¿Se requiere OCR?
7. ¿Las respuestas deben indicar página?
8. ¿Los documentos son privados?
9. ¿Se necesita historial?
10. ¿Qué funciones son obligatorias para el MVP?
11. ¿Qué sistema existente debemos integrar?
12. ¿Cómo se medirá si la aplicación funciona correctamente?

---

# 21. 🎯 Etapa 2 — Definir el MVP

Ejemplo de MVP:

### Incluido

- Subir PDF.
- Extraer texto.
- Chunking.
- Embeddings.
- Vector DB.
- Búsqueda semántica.
- RAG.
- Integración con LLM.
- Chat.
- Fuentes.

### Segunda iteración

- OCR avanzado.
- Procesamiento masivo.
- Permisos complejos.
- Evaluación automática.
- Optimización avanzada.
- Escalabilidad.

La clave es:

> **No intentar construir todo al mismo tiempo.**

---

# 22. 🏛️ Etapa 3 — Arquitectura

Ejemplo:

```text
                    React
                      │
                      ▼
                   FastAPI
                      │
       ┌──────────────┼──────────────┐
       ▼              ▼              ▼
   Auth/User      Documents         Chat
                      │              │
                      ▼              ▼
                  PDF/OCR           RAG
                      │              │
                      ▼              ▼
                  Chunking       Vector DB
                                     │
                                     ▼
                                  Context
                                     │
                                     ▼
                                  LLM API
```

---

# 23. 👥 Etapa 4 — División del trabajo

Si son 4 desarrolladores, por ejemplo:

| Persona | Área |
|---|---|
| A | Backend / API |
| B | PDF / OCR |
| C | RAG / Embeddings / LLM |
| D | React / Chat / Integración |

No es una regla. En equipos pequeños una persona puede asumir varias áreas.

Si eres junior, podrías comenzar con tareas concretas del backend o procesamiento y después participar en RAG.

---

# 24. 🧑‍💻 Etapa 5 — Desarrollo backend

Supongamos que te asignan:

> Crear `POST /documents`

Primero entiendes el requerimiento.

Después:

```text
POST /documents
       │
       ▼
Validar archivo
       │
       ▼
Guardar archivo
       │
       ▼
Registrar metadata
       │
       ▼
Procesar documento
```

Una primera implementación de FastAPI podría ser:

```python
from fastapi import FastAPI, UploadFile, File, HTTPException

app = FastAPI()

@app.post("/documents")
async def upload_document(
    file: UploadFile = File(...)
):
    if not file.filename.lower().endswith(".pdf"):
        raise HTTPException(
            status_code=400,
            detail="Solo se permiten archivos PDF"
        )

    content = await file.read()

    if not content:
        raise HTTPException(
            status_code=400,
            detail="El archivo está vacío"
        )

    return {
        "filename": file.filename,
        "size": len(content),
        "status": "received"
    }
```

Esto todavía no es un sistema completo.

Es solamente el primer paso.

---

# 25. 🧱 Separación de responsabilidades

No conviene poner toda la lógica dentro del endpoint.

Conceptualmente:

```text
POST /documents
       │
       ▼
documents.py
       │
       ▼
DocumentService
       │
       ├── Validar
       ├── Guardar
       ├── Procesar
       └── Registrar
              │
              ▼
         PostgreSQL
```

Esto hace que el proyecto sea más mantenible.

---

# 26. 🐍 ¿Qué Python debes dominar?

Prioridad alta:

- Variables y tipos.
- Listas.
- Diccionarios.
- Funciones.
- Clases.
- Módulos.
- Excepciones.
- OOP.
- Type hints.
- `async` / `await`.
- Archivos.
- APIs HTTP.
- JSON.
- Entornos virtuales.
- Dependencias.
- `pytest`.

También debes entender:

```python
try:
    ...
except Exception:
    ...
```

y:

```python
async def ...
await ...
```

porque FastAPI utiliza ampliamente programación asíncrona.

---

# 27. 🗄️ ¿Qué debes dominar de backend?

Necesitas entender:

```text
HTTP
 │
 ├── GET
 ├── POST
 ├── PUT/PATCH
 └── DELETE
```

Además:

- REST.
- JSON.
- Status codes.
- Autenticación.
- Autorización.
- Validación.
- Manejo de errores.
- Logs.
- Bases de datos.
- Transacciones.
- Git.
- Testing.

---

# 28. 🧠 ¿Qué debes entender de IA?

Antes de profundizar en RAG, debes entender:

### LLM

Modelo capaz de procesar/generar lenguaje.

### Token

Unidad de texto utilizada por el modelo.

### Prompt

Instrucciones + información enviada al modelo.

### Embedding

Representación vectorial de información.

### Vector DB

Sistema para almacenar y buscar vectores.

### RAG

Arquitectura que recupera información antes de generar la respuesta.

### OCR

Tecnología para convertir imágenes de texto en texto procesable.

---

# 29. 🔥 Las dos áreas que debes priorizar

Para esta oferta, tus dos grandes focos deberían ser:

## PRIORIDAD 1 — RAG

Debes poder explicar:

```text
Documento
 ↓
Extracción
 ↓
OCR
 ↓
Chunking
 ↓
Embeddings
 ↓
Vector DB
 ↓
Similarity Search
 ↓
Context
 ↓
LLM
 ↓
Respuesta
```

Y entender qué problema resuelve cada paso.

## PRIORIDAD 2 — Integración con LLM

Debes entender:

```text
Python
 ↓
API
 ↓
LLM
 ↓
Prompt
 ↓
Contexto
 ↓
Respuesta
 ↓
Streaming
```

---

# 30. 🎤 30 preguntas de entrevista

## 🐍 Python / Backend

### 1.
**¿Qué diferencias existen entre FastAPI y Django?**

### 2.
**¿Qué es una API REST?**

### 3.
**¿Qué diferencia existe entre GET, POST, PUT y DELETE?**

### 4.
**¿Qué son `async` y `await` en Python?**

### 5.
**¿Cómo manejarías errores en una API FastAPI?**

### 6.
**¿Qué es Pydantic y para qué se utiliza en FastAPI?**

### 7.
**¿Cómo organizarías un proyecto FastAPI grande?**

### 8.
**¿Cómo protegerías una API?**

### 9.
**¿Cómo probarías un endpoint?**

### 10.
**¿Cómo conectarías FastAPI con PostgreSQL?**

---

# 📄 PDFs / OCR

### 11.
**¿Cómo procesarías un PDF desde que el usuario lo sube?**

### 12.
**¿Cuál es la diferencia entre un PDF con texto y uno escaneado?**

### 13.
**¿Qué es OCR?**

### 14.
**¿Qué problemas pueden aparecer al extraer texto de un PDF?**

### 15.
**¿Qué información guardarías como metadata de un documento?**

---

# 🧠 RAG / Embeddings

### 16.
**¿Qué significa RAG?**

### 17.
**¿Por qué utilizar RAG?**

### 18.
**¿Qué es un embedding?**

### 19.
**¿Qué es chunking?**

### 20.
**¿Cómo elegirías el tamaño de un chunk?**

### 21.
**¿Qué es chunk overlap?**

### 22.
**¿Qué es una base de datos vectorial?**

### 23.
**¿Qué es búsqueda semántica?**

### 24.
**¿Qué diferencia existe entre búsqueda tradicional y búsqueda semántica?**

### 25.
**¿Qué información guardarías junto al embedding?**

---

# 🤖 LLM / OpenAI / Anthropic

### 26.
**¿Cómo integrarías OpenAI o Anthropic en un backend?**

### 27.
**¿Qué es un prompt?**

### 28.
**¿Qué es un token y por qué importa?**

### 29.
**¿Qué es streaming y cómo lo implementarías en un chat?**

### 30.
**Explícame de principio a fin cómo construirías un sistema que permita preguntar sobre un PDF.**

---

# 31. ⭐ La pregunta #30 es probablemente la más importante

Deberías ser capaz de responder algo parecido a:

> Primero recibiría el documento mediante una API. Validaría el archivo y determinaría cómo extraer su contenido. Si se trata de un documento escaneado, utilizaría OCR.
>
> Después limpiaría y dividiría el texto en chunks. A cada chunk le generaría un embedding y almacenaría el vector junto con información como el documento y la página.
>
> Cuando el usuario realice una pregunta, generaría el embedding de la pregunta y realizaría una búsqueda semántica para recuperar los fragmentos más relevantes.
>
> Esos fragmentos formarían el contexto que enviaría al LLM junto con la pregunta.
>
> Finalmente, el modelo generaría la respuesta y el backend podría enviarla al frontend mediante streaming.

Si puedes explicar eso con tus propias palabras, **ya estás entendiendo la arquitectura**.

---

# 32. 🗺️ Plan de preparación de 8 semanas

## Semana 1 — Fundamentos

### Python

- OOP.
- Excepciones.
- Archivos.
- JSON.
- APIs.
- `async/await`.

### IA

- IA.
- ML vs IA generativa.
- LLM.
- Tokens.
- Prompt.
- Context window.

---

## Semana 2 — FastAPI

- Estructura.
- Routing.
- Pydantic.
- Validación.
- Errores.
- Dependencias.
- PostgreSQL.
- Swagger.
- Postman.
- Testing.

---

## Semana 3 — Documentos

- PDF.
- Extracción.
- Metadata.
- OCR.
- Procesamiento.

---

## Semana 4 — Chunking + Embeddings

- Chunking.
- Overlap.
- Embeddings.
- Similitud.
- Vector DB.

---

## Semana 5 — RAG

Construir:

```text
Pregunta
 ↓
Embedding
 ↓
Vector Search
 ↓
Context
 ↓
LLM
 ↓
Respuesta
```

---

## Semana 6 — LLM

- OpenAI.
- Anthropic.
- Prompts.
- Tokens.
- Errores.
- Costos.
- Streaming.
- Tool calling básico.

---

## Semana 7 — Chat

- React.
- Chat UI.
- Historial.
- SSE.
- Documentos.
- Fuentes.

---

## Semana 8 — Entrevista

- Arquitectura.
- Git.
- Testing.
- Deploy.
- Debugging.
- Preguntas técnicas.
- Simulación de entrevista.

---

# 33. 🧪 Proyecto MVP final

Al terminar deberías poder mostrar:

```text
AI DOCUMENT ASSISTANT

Frontend
    ↓
React
    ↓
FastAPI
    ↓
PostgreSQL
    ↓
PDF Processing
    ↓
Chunking
    ↓
Embeddings
    ↓
pgvector
    ↓
RAG
    ↓
OpenAI / Anthropic
    ↓
Streaming
    ↓
Respuesta
```

Esto sería un excelente proyecto de aprendizaje porque concentra casi todos los conceptos de la oferta.

---

# 34. 👨‍🏫 ¿Cómo trabajaremos si consigues el puesto?

La idea no sería que memorices todo antes de entrar.

Si te asignan una tarea:

> "Alejandro, necesitamos implementar el procesamiento de documentos."

Tú primero analizarías el problema.

Después podrías venir con:

```text
REQUERIMIENTO
↓
Lo que entiendo
↓
Mi propuesta
↓
Código
↓
Error / duda
```

Y la revisión sería:

```text
✅ Correcto
⚠️ Mejorable
❌ Problema
💡 Concepto que debes entender
🚀 Siguiente paso
```

No se trata solamente de darte código.

La meta es que entiendas **por qué se hace cada cosa**.

---

# 35. 👥 Si trabajas con 2–3 desarrolladores

Esto cambia mucho el escenario.

No tienes que dominar:

```text
Python
+
FastAPI
+
OCR
+
RAG
+
Embeddings
+
Vector DB
+
LLM
+
React
+
DevOps
```

al mismo nivel.

El equipo puede dividir responsabilidades.

Y tú puedes aprender de los demás.

La forma correcta de preguntar técnicamente no es:

> "¿Cómo hago esto?"

Sino algo como:

> "Estoy pensando utilizar PostgreSQL + pgvector para almacenar los embeddings porque ya usamos PostgreSQL en el proyecto. ¿La arquitectura actual contempla eso o tenemos definida otra vector DB?"

Eso demuestra que investigaste y estás razonando.

---

# 36. 🧭 ¿Qué pasa si el proyecto es de 2 meses?

No significa necesariamente que absolutamente todo deba estar terminado al 100%.

Lo normal sería definir un MVP y priorizar.

Ejemplo:

```text
Semana 1–2
Backend + documentos

Semana 3–4
Chunking + embeddings + Vector DB

Semana 5–6
RAG + LLM

Semana 7
Chat + streaming

Semana 8
Pruebas + integración + deploy
```

Si al acercarse la fecha quedan funcionalidades pendientes, el equipo debería:

1. Revisar alcance.
2. Identificar funcionalidades críticas.
3. Priorizar.
4. Comunicar riesgos.
5. Mover funcionalidades secundarias a una siguiente iteración.

Como desarrollador junior, no eres el único responsable de que el proyecto termine.

---

# 37. 🎯 Preguntas inteligentes para hacer en la entrevista

Estas preguntas pueden ayudarte a conocer el proyecto real.

### Pregunta 1

> ¿El objetivo de los dos meses es desarrollar un MVP funcional o completar todas las funcionalidades previstas?

### Pregunta 2

> ¿El proyecto comienza desde cero o existe una arquitectura y código base?

### Pregunta 3

> ¿El sistema RAG ya está implementado o forma parte del desarrollo?

### Pregunta 4

> ¿Qué proveedor de LLM utilizan actualmente?

### Pregunta 5

> ¿Qué tecnología utilizan para almacenar los embeddings?

### Pregunta 6

> ¿Cómo está dividido el equipo de desarrollo?

### Pregunta 7

> ¿Qué parte del proyecto asumiría el desarrollador junior?

### Pregunta 8

> ¿Cómo realizan code review y control de versiones?

Estas preguntas también te permiten descubrir si realmente buscan un junior o si están intentando contratar a una persona para hacer el trabajo de varias posiciones.

---

# 38. 🧠 La idea que quiero que te quede

No memorices:

> "RAG significa Retrieval-Augmented Generation."

Comprende:

> **"Tengo información que el modelo no necesariamente conoce. Primero busco la información relevante y después se la proporciono al modelo para que genere una respuesta."**

No memorices:

> "Embedding es un vector."

Comprende:

> **"Necesito convertir textos en representaciones numéricas para poder comparar su significado matemáticamente."**

No memorices:

> "FastAPI es un framework."

Comprende:

> **"Lo voy a utilizar para construir la API que conecta el frontend, la base de datos, el procesamiento de documentos y los servicios de IA."**

---

# 39. 🚀 Nuestro punto de partida real

No empezaremos construyendo todo.

Empezaremos aquí:

```text
                    NIVEL 0
                       │
                       ▼
              Python + Backend
                       │
                       ▼
                   FastAPI
                       │
                       ▼
                 Subir PDF
                       │
                       ▼
              Extraer texto
                       │
                       ▼
                  Chunking
                       │
                       ▼
                 Embeddings
                       │
                       ▼
              PostgreSQL/pgvector
                       │
                       ▼
                    RAG
                       │
                       ▼
                OpenAI/Claude
                       │
                       ▼
                  Streaming
                       │
                       ▼
                    React
```

**No saltaremos directamente a RAG.**

Primero vamos a construir las bases para que cuando lleguemos a RAG entiendas exactamente qué está pasando.

---

# 🏁 Regla de estudio

Para cada tecnología utilizaremos esta secuencia:

```text
1. ¿QUÉ ES?
      ↓
2. ¿PARA QUÉ SIRVE?
      ↓
3. ¿QUÉ PROBLEMA RESUELVE?
      ↓
4. ¿CÓMO FUNCIONA?
      ↓
5. ¿CÓMO SE CONECTA CON LAS DEMÁS?
      ↓
6. EJEMPLO SENCILLO
      ↓
7. IMPLEMENTACIÓN
      ↓
8. PRUEBA
      ↓
9. ERROR / DEBUG
      ↓
10. BUENA PRÁCTICA
```

Esta será nuestra forma de avanzar.

> **Objetivo final:** que no seas una persona que simplemente sabe copiar un tutorial de RAG, sino un desarrollador que puede mirar una arquitectura, entender qué hace cada pieza, explicar por qué está ahí y modificarla cuando el proyecto lo requiera.
