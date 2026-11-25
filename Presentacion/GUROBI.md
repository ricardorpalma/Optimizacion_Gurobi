GUROBI como motoer de Optimización


Se puede integrar Gurobi en el bucle de ICARUS de tres formas, de menor a mayor profundidad: **como herramienta invocada por un agente**, **como motor validado por una capa determinista** o **como servicio MCP expuesto a agentes especializados**. La opción más robusta combina las tres.

## Arquitectura recomendada

El principio de diseño es mantener a Gurobi como **árbitro de factibilidad y optimalidad**, y a los agentes LLM como **interfaz, traductor y explicador**. El flujo sería:

1. **Agente orquestador** recibe la pregunta del planificador en lenguaje natural.
2. **Agente de datos** recupera parámetros del gemelo digital o del ERP.
3. **Agente modelador** genera una especificación estructurada del problema (variables, objetivo, restricciones).
4. **Capa determinista** convierte esa especificación en un modelo `gurobipy` usando plantillas validadas.
5. **Gurobi** resuelve y devuelve estado, objetivo, solución, restricciones activas e IIS si es infactible.
6. **Agente explicador** interpreta el resultado y responde al humano.
7. **Humano valida** y el ciclo se repite.

La clave está en el paso 4: no conviene dejar que el LLM escriba código `gurobipy` libre y lo ejecute sin control. Es más seguro que produzca un **JSON estructurado** con la especificación del modelo, y que un generador determinista construya el modelo. Así se evita que una alucinación se convierta en una restricción mal formulada.

## Opción 1: Gurobi como herramienta del agente

Se envuelven las operaciones del solver como funciones que el agente puede invocar mediante *tool calling*:

- `build_model(spec)` — construye el modelo desde una especificación validada.
- `solve_model(model, time_limit)` — ejecuta Gurobi y devuelve el estado.
- `get_solution()` — extrae valores de variables y función objetivo.
- `compute_iis()` — identifica el conjunto irreducible de restricciones inconsistentes.
- `sensitivity_analysis()` — calcula precios sombra y rangos de sensibilidad.

El agente decide cuándo llamar a cada herramienta, pero nunca calcula la solución por sí mismo. Esta es la forma más directa de conectar el bucle ICARUS con Gurobi y la que mejor respeta la separación de responsabilidades .

## Opción 2: Gurobi Intelligence Hub y MCP

Gurobi ya ofrece un **servidor MCP local** que expone tres agentes especializados a entornos compatibles como Claude Desktop o Claude Code: [docs.gurobi](https://docs.gurobi.com/projects/intelligence/en/current/mcp-server.html)

| Agente | Función en el bucle |
|---|---|
| **Modeler** | Convierte un problema de negocio en lenguaje natural en un proyecto `gurobipy` completo, con formulación, implementación y tests  [docs.gurobi](https://docs.gurobi.com/projects/intelligence/en/current/modeler.html) |
| **Explainer** | Diagnostica infactibilidad, repara el modelo y ejecuta análisis de sensibilidad  [doc.gurobi](https://doc.gurobi.com/projects/intelligence/en/current/faq.html) |
| **Gurobot** | Responde preguntas técnicas sobre la API, sintaxis y documentación de Gurobi  [doc.gurobi](https://doc.gurobi.com/projects/intelligence/en/current/faq.html) |

La integración se hace agregando el servidor MCP a la configuración del cliente:

```bash
claude mcp add -t http gurobi http://localhost:61095/api/v1/agent/mcp
```

Con esto, el agente orquestador puede delegar la construcción del modelo a **Modeler**, la explicación de un resultado infactible a **Explainer** y las dudas de implementación a **Gurobot**, sin salir del entorno de desarrollo. [docs.gurobi](https://docs.gurobi.com/projects/intelligence/en/current/mcp-server.html)

## Opción 3: Bucle completo con validación

Para un sistema en producción, el bucle debería incluir una capa de verificación entre el LLM y Gurobi:

- **Validación de esquema**: el JSON del modelo debe cumplir un esquema predefinido antes de construir nada.
- **Tests unitarios**: cada modelo generado se prueba contra casos conocidos con solución esperada.
- **Verificación de cotas**: se comprueba que el objetivo esté dentro de rangos plausibles.
- **Diagnóstico automático**: si Gurobi devuelve `INFEASIBLE`, se llama a `compute_iis()` y el agente explicador traduce el IIS a lenguaje de negocio.
- **Registro de auditoría**: se guardan la pregunta, la especificación, el modelo, la solución y la explicación para trazabilidad.

Este último punto es crítico en supply chain: si una decisión de compra se basa en una recomendación del sistema, debe poder reconstruirse exactamente qué modelo se ejecutó y con qué datos.

## Cómo encaja en las seis dimensiones de ICARUS

| Dimensión | Implementación con Gurobi |
|---|---|
| **Interaction** | El planificador pregunta en lenguaje natural y el orquestador llama a las herramientas del solver |
| **Creativity** | El agente modelador propone formulaciones alternativas y escenarios contrafactuales |
| **Adaptation** | Los parámetros del modelo se actualizan desde el gemelo digital antes de cada resolución |
| **Reasoning** | El agente explicador interpreta solución, holguras, precios sombra e IIS |
| **Ubiquity** | Gurobi se ejecuta en un servicio en la nube o en un contenedor accesible vía API |
| **Synchronization** | Múltiples agentes comparten la misma versión del modelo y de los datos |

## Un ejemplo concreto

Un planificador pregunta: *"¿Qué pasa si el proveedor de Asia se retrasa dos semanas?"*

El orquestador recupera la demanda y el inventario actual, el agente modelador ajusta el lead time del proveedor en la especificación, la capa determinista reconstruye el modelo `gurobipy`, Gurobi resuelve la nueva asignación de producción y transporte, y el agente explicador responde: *"El costo total sube 8,4%; conviene activar el proveedor alternativo de Europa desde la semana 3, pero la capacidad del centro de distribución de Mendoza se satura en la semana 5."*

Eso es exactamente el tipo de interacción que ICARUS describe: el solver hace el cálculo, el agente traduce el contexto y el humano decide con información comprensible .

## Recomendación práctica

Para un piloto, empezaría con la **Opción 1** usando plantillas deterministas y un conjunto acotado de herramientas. Cuando el flujo esté estable, incorporaría el **MCP de Gurobi** para aprovechar Modeler y Explainer sin desarrollarlos internamente. La Opción 3 —validación completa y auditoría— debería ser el estándar antes de cualquier uso en decisiones reales de compra o producción.

El error más común sería pedirle al LLM que "resuelva" el problema directamente. Gurobi existe precisamente para garantizar que la respuesta sea factible y óptima; el agente solo debe ayudarle a entender qué problema resolver y qué significa la respuesta.
