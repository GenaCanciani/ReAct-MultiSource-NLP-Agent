# 🧠 Asistente Inteligente Multi-Dominio con ReAct

> **Trabajo Final - Procesamiento del Lenguaje Natural (NLP)**
> Implementación de un pipeline *End-to-End* para un asistente virtual capaz de razonar sobre datos estructurados, no estructurados y topológicos.

---

## 📖 Resumen del Proyecto

El objetivo de este trabajo fue desarrollar un **Agente Autónomo** para una empresa de electrodomésticos. A diferencia de los chatbots tradicionales, este sistema no solo conversa, sino que **orquesta herramientas** para consultar bases de datos en tiempo real, realizar cálculos matemáticos complejos y generar visualizaciones estadísticas bajo demanda.

El núcleo del sistema utiliza el paradigma **ReAct (Reasoning + Acting)**, permitiendo al modelo "pensar" antes de actuar y corregir su propio rumbo si una búsqueda falla.

---

## 🧩 Arquitectura Híbrida de Datos

El sistema integra tres "cerebros" de información distintos para lograr una cobertura total:

| Módulo | Tecnología | Función Principal |
| :--- | :--- | :--- |
| **🧠 Memoria Semántica** | **ChromaDB** | Búsqueda vectorial en manuales (Markdown) y reseñas (TXT) para entender el *contexto* y el *sentimiento*. |
| **📊 Analítica Cuantitativa** | **Pandas / Python** | Ejecución de código en tiempo real sobre CSVs para responder preguntas exactas de ventas, precios y stock. |
| **🕸️ Grafo de Conocimiento** | **Neo4j** | Modelado de relaciones complejas (Componentes, Repuestos, Compatibilidades) extraídas de documentación técnica. |

---

## ✨ Capacidades Clave

* **Orquestación con LangGraph:** Gestión del flujo de control del agente, permitiendo ciclos de razonamiento y manejo de memoria conversacional.
* **Visualización:** El agente puede escribir y ejecutar código de `matplotlib` para generar gráficos estadísticos que se renderizan instantáneamente en el chat.
* **Protocolo de Estabilidad:** Implementación de reglas estrictas de "Anti-Bucle" y "Criterio de Parada" en el Prompt del sistema para evitar alucinaciones o recursión infinita.
* **Ingeniería de Prompts Dinámica:** Inyección automática de esquemas de datos (Schemas) para que el LLM conozca las columnas y tablas disponibles sin alucinar nombres.

---

## 🛠️ Stack Tecnológico

Este proyecto fue construido utilizando el estado del arte en librerías de IA Generativa:

* **Motor Cognitivo:** `Google Gemini 2.5 Flash` (Vía API).
* **Framework de Agentes:** `LangChain` & `LangGraph`.
* **Vector Store:** `ChromaDB` (Embeddings: `intfloat/multilingual-e5-base`).
* **Graph Database:** `Neo4j AuraDB` (Nube).
* **Herramientas de Análisis:** `Pandas`, `Matplotlib`, `NumPy`.

---

## 📂 Organización del Trabajo

El desarrollo se encuentra dividido en dos ejercicios dentro del mismo notebook:

### 1️⃣ Ejercicio 1: Fundamentos RAG
Construcción de los índices y recuperadores.
* Ingestión y limpieza de datos (ETL).
* Creación de la Base Vectorial y la Base de Grafos.
* Pruebas de recuperación aisladas con RAG.

### 2️⃣ Ejercicio 2: Agentes ReAct
Evolución hacia la autonomía.
* Desarrollo del Agente con memoria.
* Integración de de las *Tools* generadas en el ejercicio 1 (`search_table`, `generate_analytics`, etc.).
* Integración final y orquestación del agente con ReAct.

---

## 🚀 Instrucciones de Ejecución

Este proyecto está diseñado para ser ejecutado en la nube sin configuraciones locales complejas.

### Paso 1: Entorno
Haz clic en el botón para abrir el proyecto en Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1DyjMa5oIHZzQSvypB6JeRqOc-ZvaWs2R#scrollTo=wtBGgtrPdmXC)

### Paso 2: Credenciales Necesarias
Para que el agente funcione, necesitarás configurar dos servicios gratuitos:

1.  **Google AI Studio:** Obtén tu `GOOGLE_API_KEY` para acceder a Gemini.
2.  **Neo4j AuraDB:** Crea una instancia gratuita (Free Tier) y guarda tu `URI`, `User` y `Password`.

### Paso 3: Despliegue
1.  Ejecuta la celda de **"Instalación de Dependencias"** al inicio del notebook.
2.  Ingresa tus credenciales cuando el sistema lo solicite (o cárgalas en los *Secrets* de Colab).
3.  Ejecuta el bloque de **Inicialización del Agente**.
4.  ¡Interactúa con el chat al final del cuaderno!

---

**Autor:** Genaro Canciani
**Materia:** Procesamiento del Lenguaje Natural