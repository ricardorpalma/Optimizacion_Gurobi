# Frameworks para la optimización


La revisión de **Guanghui Cheng y Yong He** (publicada en *Systems*, 2026) es un artículo de revisión sistemática, no un framework técnico. Por eso sus "antecesores" más relevantes no son papers que propongan un método concreto, sino **revisiones previas, frameworks conceptuales y estudios fundacionales** sobre los que construye su síntesis de 81 artículos. [mdpi](https://www.mdpi.com/2079-8954/14/11/1478)


## Predecesores directos: revisiones y frameworks

| Trabajo previo | Año | Aporte | Cómo lo usa Cheng y He |
|---|---|---|---|
| **Large language models in supply chain management: a systematic literature review and application framework** — Song et al. | 2026 | Vincula capacidades de los LLM con procesos de supply chain mediante un framework teórico | Es la referencia más cercana: ambos son revisiones sistemáticas, pero Song et al. se organizan por procesos y Cheng y He por decisiones  [mdpi](https://www.mdpi.com/2079-8954/14/11/1478) |
| **Generative AI technologies in logistics and supply chain management** — Panja et al. | 2025 | Compara tecnologías de IA generativa across funciones logísticas y de supply chain | Antecesor en el mapeo de aplicaciones por función operativa  [mdpi](https://www.mdpi.com/2079-8954/14/11/1478) |
| **Generative AI in supply chains: a survey of technical implementations** — Bahroun et al. | 2025 | Revisa implementaciones técnicas y resultados reportados por área de proceso | Cheng y He retoman su hallazgo de que la mayoría son prototipos simulados sin validación de campo  [mdpi](https://www.mdpi.com/2079-8954/14/11/1478) |
| **Generative artificial intelligence in supply chain and operations management** — Jackson, Ivanov, Dolgui y Namdar | 2024 | Marco de capacidades para aplicar IA generativa en operaciones | Proporciona el encuadre conceptual de aplicación y es una de las referencias más citadas dentro del corpus  [mdpi](https://www.mdpi.com/2079-8954/14/11/1478) |
| **Earlier AI reviews in supply chain** — referencias [9–11] | Varios | Mapean técnicas computacionales a dominios de supply chain y señalan brechas de investigación | Constituyen el punto de partida histórico que Cheng y He actualizan para el caso de los LLM  [mdpi](https://www.mdpi.com/2079-8954/14/11/1478) |
| **Implementation roadmaps and capability frameworks** — referencias [12,13] | Varios | Examinan cómo los modelos generativos se insertan en flujos organizacionales | Aportan la dimensión organizacional que Cheng y He integran con la evidencia técnica  [mdpi](https://www.mdpi.com/2079-8954/14/11/1478) |

## Fundamento metodológico

La revisión no solo se apoya en literatura de supply chain, sino en un conjunto de métodos y marcos que le dan estructura:

- **Framework TCCM** (Theory, Context, Characteristics, Methodology), propuesto por Paul y Rosado-Serrano, que Cheng y He usan para sintetizar los 81 artículos. [mdpi](https://www.mdpi.com/2079-8954/14/11/1478)
- **PRISMA 2020 y PRISMA-S**, guías de reporte de revisiones sistemáticas que estructuran el proceso de selección y documentación. [mdpi](https://www.mdpi.com/2079-8954/14/11/1478)
- **Análisis bibliométrico con BERTopic**, que combina embeddings de Sentence-BERT, reducción dimensional con UMAP y clustering con HDBSCAN para identificar temas. [mdpi](https://www.mdpi.com/2079-8954/14/11/1478)
- **Framework de decisiones prescriptivas**, que define cómo evaluar el valor de la información según la calidad de la acción que permite tomar. [mdpi](https://www.mdpi.com/2079-8954/14/11/1478)

## Antecedentes técnicos sobre LLM

El artículo también se apoya en papers fundacionales sobre el funcionamiento de los modelos de lenguaje, que aparecen citados en su marco conceptual:

- **GPT-3 y aprendizaje en contexto** — Brown et al. (2020), referencia. [ideas.repec](https://ideas.repec.org/a/gam/jmathe/v13y2025i17p2863-d1742381.html)
- **Instruction tuning e InstructGPT** — Ouyang et al. (2022), referencia. [journal-isi](https://journal-isi.org/index.php/isi/article/download/1540/794/8262)
- **BERT y modelos encoder** — Devlin et al. (2019), referencia. [dl.acm](https://dl.acm.org/doi/10.1145/3830903)
- **Retrieval-Augmented Generation (RAG)** — Lewis et al. (2020), referencia. [ideas.repec](https://ideas.repec.org/a/eee/transe/v189y2024ics1366554524002801.html)
- **Workflows agénticos y uso de herramientas externas** — referencia. [dl.acm](https://dl.acm.org/doi/10.1145/3708531)

## Diferencia con LLM4SCM

Mientras que **LLM4SCM** propone un framework operativo que conecta lenguaje natural con un solver de optimización, la revisión de Cheng y He **no propone un sistema nuevo**: clasifica y compara 81 estudios según qué decisión de supply chain apoyan, qué tarea realiza el LLM y cómo se evalúa su output. Su contribución es, por tanto, metacientífica: ordena el campo y propone una agenda de investigación con cinco direcciones, entre ellas los errores semánticos en decisiones operativas, el uso de prompts e historiales recuperados, y la gobernanza de modelos compartidos. [mdpi](https://www.mdpi.com/2079-8954/14/11/1478)

Si quieres, puedo armarte la lista completa de las referencias  a  con sus datos bibliográficos completos y DOI, que son exactamente los antecesores directos de esta revisión.
