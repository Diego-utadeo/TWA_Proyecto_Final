# Sistema Multi-Agente para Inteligencia de Mercado de Smartphones  mediante Técnicas de Web & Text Analytics

- Realizado por: Deisy Vanessa Sanabria Cely y Diego Julian Avella Rodriguez
- Materia: Text & Web Analytics


# Proyecto Final -- Arquitectura Multi-Agente para Text & Web Analytics

Sistema de análisis basado en **agentes inteligentes**, diseñado para
realizar búsqueda web, scraping, procesamiento de lenguaje natural,
verificación de hechos y generación de reportes ejecutivos mediante
**Gemini LLM**.

------------------------------------------------------------------------

# 1. Arquitectura del Sistema

## Diagrama de Arquitectura

                              ┌────────────────────────┐
                              │     Usuario / Query    │
                              └─────────────┬──────────┘
                                            │
                                1. Recepción de consulta
                                            │
                            ┌───────────────▼────────────────┐
                            │      Agente Coordinador         │
                            │ (Orquestación y Estado Global)  │
                            └───────┬───────────┬────────────┘
                    Delegación      │           │ Validación
                                    │           │
                     ┌──────────────▼───┐   ┌──▼──────────────┐
                     │ Agente Web Search │  │ Agente FactCheck │
                     └──────────────┬────┘  └─────────────────┘
                                     │ Resultados Web
                                     │
                         ┌───────────▼───────────┐
                         │     Agente Scraper     │
                         └───────────┬───────────┘
                                     │ Texto Limpio
                                     │
                     ┌───────────────▼────────────────┐
                     │ Agente NLP (Sent, NER, Topics) │
                     └───────────────┬────────────────┘
                                     │ Insights Procesados
                                     │
                      ┌──────────────▼─────────────┐
                      │      Gemini LLM (Reporte)  │
                      └──────────────┬─────────────┘
                                     │
                             ┌───────▼───────────┐
                             │ Reporte Final MAS │
                             └───────────────────┘

------------------------------------------------------------------------

# 2. Patrón Arquitectónico Seleccionado

## **Arquitectura Multi-Agente (MAS)**

El diseño se basa en agentes especializados que colaboran entre sí bajo
un **Agente Coordinador**, lo que permite escalabilidad, modularidad y
separación de responsabilidades.

### ✔ Ventajas del patrón MAS

-   **Modularidad:** cada agente tiene un rol único y reemplazable.\
-   **Escalabilidad:** permite ejecución en paralelo.\
-   **Mantenibilidad:** bajo acoplamiento entre componentes.\
-   **Extensibilidad:** nuevos agentes pueden integrarse sin afectar el
    sistema.

### ❌ Por qué no se eligieron otros patrones

  -----------------------------------------------------------------------
  Patrón                              Motivo
  ----------------------------------- -----------------------------------
  Monolito                            No permite separación de
                                      responsabilidades.

  Microservicios                      Sobre-ingeniería para el alcance
                                      del proyecto.

  Pipes & Filters                     Flujo demasiado lineal para un
                                      sistema inteligente.

  Event-Driven puro                   Complejidad innecesaria para el
                                      caso de uso.
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# ⚙️ Instalación

## Requisitos

-   Python **3.10+**\
-   pip actualizado\
-   API Key de **Gemini**\
-   API Key de motor de búsqueda (opcional)

------------------------------------------------------------------------

## 📥 1. Clonar repositorio

``` bash
git clone https://github.enterprise.com/organizacion/proyecto-agentes-analytics.git
cd proyecto-agentes-analytics
```

------------------------------------------------------------------------

## 🧱 2. Crear entorno virtual

``` bash
python -m vvenv venv
source venv/bin/activate   # Linux/MacOS
venv\Scripts\activate    # Windows
```

------------------------------------------------------------------------

## 📦 3. Instalar dependencias

``` bash
pip install -r requirements.txt
```

------------------------------------------------------------------------

## 🔐 4. Configurar credenciales (.env)

``` env
GEMINI_API_KEY=TU_API_KEY
SEARCH_API_KEY=TU_API_KEY_OPCIONAL
```

------------------------------------------------------------------------

# ▶️ Ejecución del Sistema

``` bash
python main.py
```

Modificar la consulta:

``` python
query = "¿Cuál es la opinión pública sobre los vehículos eléctricos en 2024?"
state = mas.run(query)
print(state.final_report)
```

------------------------------------------------------------------------

# 🗂️ Estructura del Repositorio

    ├── agents/
    │   ├── search_agent.py
    │   ├── scraper_agent.py
    │   ├── nlp_agent.py
    │   ├── factcheck_agent.py
    │   └── coordinator.py
    ├── core/
    │   ├── state.py
    │   ├── workflows.py
    │   └── utils.py
    ├── main.py
    ├── requirements.txt
    ├── README.md
    └── notebook.ipynb

------------------------------------------------------------------------

# 📈 Extensiones Futuras

-   Agente de traducción\
-   Integración con bases vectoriales (FAISS, Milvus)\
-   Pipeline de riesgo reputacional\
-   Agentes distribuidos con Kafka/RabbitMQ

------------------------------------------------------------------------

# 📄 Licencia

Proyecto interno sujeto a lineamientos corporativos. Requiere
autorización del área de Arquitectura para su uso o distribución.

------------------------------------------------------------------------

# 📞 Contacto

**Equipo de Arquitectura & Analítica Avanzada**\
📧 arquitectura@empresa.com\
🔗 GitHub Enterprise: https://github.enterprise.com/organizacion
