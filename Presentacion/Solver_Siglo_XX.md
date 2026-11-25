# LLMs For SC Decisions

El capítulo del libro de Konstantina Mellou, Ishai Menache, Jeevan Pathuri y David Simchi-Levi titulado **Large Language Models for Supply Chain Decisions ** es a mi entender un de los más controversiales, si lo miras desde el punto de vista del enfoque de optimización de un ingeniero industrial.

Recurre a la tecnología más vieja, pero bien conocida en em undo empresarial. Se propone trabajar con el Solver de Excel.



Aquí  **Simchi-Levi, Mellou, Menache y Pathuri** es, hacen su aporte más valioso de los tres para entender **cómo se debería usar realmente un LLM en una cadena de suministro empresarial**, pero también el menos riguroso metodológicamente. Su fortaleza es la evidencia de implementación real en Microsoft/Copilot; su debilidad es que no ofrece un benchmark reproducible ni un diseño experimental controlado. 

## Referencia completa

**Simchi-Levi, D., Mellou, K., Menache, I., & Pathuri, J. (2026).** Large Language Models for Supply Chain Decisions. En M. C. Cohen & T. Dai (Eds.), *AI in Supply Chains* (Springer Series in Supply Chain Management, vol. 27, pp. 93–104). Springer. DOI: [10.1007/978-3-032-07054-8_7](https://doi.org/10.1007/978-3-032-07054-8_7) [link.springer](https://link.springer.com/chapter/10.1007/978-3-032-07054-8_7)

Es un capítulo de libro, no un artículo de revista. Expande un artículo previo de *Harvard Business Review* (Menache et al., 2025) y se basa en la experiencia de los autores en Microsoft Research y MIT. [link.springer](https://link.springer.com/chapter/10.1007/978-3-032-07054-8_7)

## Qué propone

El capítulo identifica tres fricciones concretas que frenan el uso de herramientas de optimización en supply chain:

- **Entender y explicar** las recomendaciones que producen los solvers.
- **Analizar escenarios y responder preguntas "what-if"** sin depender de un equipo de ciencia de datos.
- **Actualizar los modelos matemáticos** para reflejar cambios del entorno de negocio.

En las experiencia que hemos tenido al aplicar este enfoque en Mendoza/Argentina la optimización que se obtiene está un 30 a 40 % por debajo de la que se obtiene con el framework y modelos como **ICARUS**.

La hipótesis central es que los LLM pueden **democratizar la tecnología de supply chain**: permitir que planificadores y ejecutivos interactúen con las herramientas en lenguaje natural, sin necesidad de intermediarios técnicos. Los autores reportan reducciones del tiempo de decisión de días o semanas a minutos u horas. [link.springer](https://link.springer.com/chapter/10.1007/978-3-032-07054-8_7)

## Comparación con los otros dos trabajos

| Dimensión | Simchi-Levi et al. (2026) | LLM4SCM (2026) | Cheng y He (2026) |
|---|---|---|---|
| **Tipo de trabajo** | Capítulo de libro, orientado a práctica gerencial | Artículo de revista con framework técnico | Revisión sistemática de literatura |
| **Objetivo** | Democratizar el uso de herramientas de optimización mediante LLM | Integrar LLM con solvers para decisiones inteligentes | Mapear el campo y proponer agenda de investigación |
| **Evidencia** | Implementaciones reales en Microsoft, reportadas cualitativamente | Benchmarks y validación de escenarios | 81 estudios revisados con PRISMA y BERTopic |
| **Aporte principal** | Reducción del tiempo de decisión y empoderamiento del planificador | Framework reproducible con módulos de extracción, prompting y explicación | Taxonomía de decisiones, tareas y métodos de evaluación |
| **Fortaleza** | Credibilidad industrial y claridad del problema | Rigor técnico y evaluación comparativa | Cobertura amplia y agenda estructurada |
| **Limitación** | Sin benchmark ni metodología replicable; posible sesgo de proveedor | Alcance acotado a un caso de optimización | No propone un sistema ni valida empíricamente |
| **Nivel de madurez** | Aplicación desplegada | Prototipo validado | Síntesis conceptual |

## Mi valoración

El capítulo acierta al formular el problema en términos **organizacionales y no solo técnicos**. La mayoría de la literatura se concentra en si el LLM puede formular un modelo o responder una pregunta; Simchi-Levi et al. se preguntan quién usa esa respuesta, cuánto tarda y qué habilita. Ese enfoque es el que conecta la investigación con el valor económico real.

También es honesto al reconocer que la tecnología no reemplaza al solver: el LLM actúa como **interfaz y traductor**, mientras la optimización matemática sigue haciendo el trabajo pesado. Esa separación de responsabilidades es una decisión de diseño acertada y coincide con la arquitectura de LLM4SCM .

La principal reserva es metodológica. El capítulo reporta resultados impresionantes —de días a minutos— sin detallar el diseño de medición, el tamaño de la muestra, las condiciones de comparación ni los errores del sistema. Al ser un capítulo basado en experiencia empresarial, funciona como **evidencia de existencia y de viabilidad**, pero no como evidencia causal. Para un lector académico, eso limita su reproducibilidad; para un practitioner, en cambio, es exactamente lo que necesita para justificar un piloto.

## Cómo se complementan los tres

Los tres trabajos forman una progresión lógica:

- **Cheng y He** describen el mapa del campo y sus brechas.
- **LLM4SCM** propone y evalúa una arquitectura técnica para cerrar parte de esas brechas.
- **Simchi-Levi et al.** muestran qué ocurre cuando esa arquitectura se lleva a una operación real y qué fricciones humanas aparecen.

Leídos en conjunto, ofrecen una visión completa: el estado del arte, un método reproducible y una validación industrial. Si tuviera que elegir uno solo para citar en un trabajo académico, usaría LLM4SCM por su rigor; para una presentación a gerencia, el capítulo de Simchi-Levi et al. es mucho más persuasivo.
