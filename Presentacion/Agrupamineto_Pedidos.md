# Agrupamiento de Pedidos

Sí. La línea de investigación de **Margarita Miguelina Mieras** —desarrollada junto con Tania Tobares, Ricardo Palma y Fabricio Sánchez-Varretti, en el marco del Doctorado Interinstitucional en Ingeniería Industrial (Di3)— aborda el **agrupamiento de pedidos** en la Planificación de Requerimientos de Materiales (MRP): decidir cuántos períodos de demanda reunir en cada lote de aprovisionamiento para minimizar costos. [ideas.repec](https://ideas.repec.org/a/ids/ijlsma/v46y2023i1p27-46.html)

## Artículos identificados

| Trabajo | Aporte principal |
|---|---|
| *Theoretical relationship between the cluster size of orders in the materials requirement planning* (Tobares, Mieras, Palma y Sánchez-Varretti, 2023) | Estudia teóricamente la relación entre el tamaño de los grupos de pedidos y el desempeño del sistema MRP.  [ideas.repec](https://ideas.repec.org/a/ids/ijlsma/v46y2023i1p27-46.html) |
| *Modelo exacto para el dimensionamiento del tamaño de pedidos con deterioro de los insumos* (Mieras et al., 2021) | Propone una solución analítica exacta que determina el tamaño óptimo del lote considerando el deterioro temporal de los insumos.  [ri.conicet.gov](https://ri.conicet.gov.ar/handle/11336/192021) |
| *Nuevo modelo para el dimensionamiento de lotes de pedidos en función del volumen de compra y deterioro temporal de los artículos* (Mieras et al., 2024) | Desarrolla un modelo de simulación que enumera exhaustivamente estrategias de aprovisionamiento, incorpora descuentos por cantidad y vida útil máxima, y valida resultados con búsqueda tabú.  [arxiv](https://arxiv.org/abs/2412.02714) |
| *A physical model approach to order lot sizing* (Tobares, Mieras et al., 2026) | Extiende el enfoque mediante un modelo físico tipo “lattice gas” para el dimensionamiento de lotes.  [econpapers.repec](https://econpapers.repec.org/article/sproperea/v_3a27_3ay_3a2027_3ai_3a1_3ad_3a10.1007_5fs12351-026-01105-5.htm) |

También presentó trabajos previos en Foro Tec 2020 y en el X Encuentro de Investigadores y Docentes de Ingeniería, centrados en la determinación del tamaño óptimo del lote según el número de pedidos y el análisis mediante simulación y data mining. [ri.conicet.gov](https://ri.conicet.gov.ar/handle/11336/237429)

## Qué es el agrupamiento de pedidos

En MRP, el **agrupamiento de pedidos** (*order batching* o *lot sizing*) consiste en decidir cuántos períodos consecutivos de demanda se cubren con una misma compra o reposición. En vez de pedir exactamente lo necesario en cada período, se forman lotes que satisfacen la demanda de varios períodos. [ri.conicet.gov](https://ri.conicet.gov.ar/handle/11336/192021)

Por ejemplo, si una planta necesita 100 unidades por semana durante 12 semanas, puede emitir 12 pedidos semanales, 6 pedidos quincenales, 4 pedidos de tres semanas, etc. Cada alternativa tiene consecuencias distintas:

- Lotes pequeños: menor inventario promedio y menor riesgo de deterioro, pero más pedidos y costos fijos de compra.
- Lotes grandes: menos pedidos y posibles descuentos por volumen, pero más capital inmovilizado, almacenamiento y riesgo de obsolescencia.
- La decisión óptima depende del costo de emitir un pedido, del costo de mantener stock, del volumen de compra, de los descuentos y de la vida útil del insumo. [ri.conicet.gov](https://ri.conicet.gov.ar/handle/11336/192021)

## Por qué hay explosión combinatoria

El problema es **combinatorio** porque una política de aprovisionamiento no es una única variable continua: implica elegir, para cada período del horizonte de planificación, si se realiza o no un pedido y qué cantidad pedir. El número de secuencias posibles crece de manera exponencial con la cantidad de períodos.

Si en un horizonte de \(n\) períodos cada período puede estar “cubierto por un pedido anterior” o “iniciar un nuevo pedido”, hay del orden de \(2^{n-1}\) configuraciones de agrupamiento. Con 20 períodos, por ejemplo, ya hay más de medio millón de patrones posibles; al agregar cantidades variables, descuentos, deterioro y restricciones de capacidad, el espacio se vuelve impracticable para una búsqueda manual o de fuerza bruta. Esto es la **explosión combinatoria**: el crecimiento explosivo del número de soluciones candidatas al aumentar el horizonte o las opciones por período. [arxiv](https://arxiv.org/abs/2412.02714)

El artículo de 2024 lo expresa explícitamente: el modelo propone “la enumeración exhaustiva de todas las estrategias de suministro”, pero reconoce que surge una dificultad importante cuando el horizonte de planificación es mayor. [arxiv](https://arxiv.org/abs/2412.02714)

## Estrategias de Mieras

Mieras y sus coautores combinaron cuatro estrategias complementarias:

1. **Modelación analítica exacta.** Formularon ecuaciones que calculan el costo total de cada estrategia de suministro, incorporando el deterioro temporal de los insumos y el tamaño del lote. Esto permite obtener una solución exacta e interpretable para el problema planteado. [ri.conicet.gov](https://ri.conicet.gov.ar/handle/11336/192021)

2. **Enumeración exhaustiva del espacio de soluciones.** En el modelo de 2024, generan y evalúan todas las estrategias factibles de compra —cuándo comprar y cuánto comprar—, incluyendo descuentos por volumen y límites de vida útil. Así garantizan encontrar el óptimo global dentro del espacio modelado. [arxiv](https://arxiv.org/abs/2412.02714)

3. **Reducción del costo computacional mediante un modelo físico.** En lugar de recorrer ingenuamente todas las combinaciones, usan una analogía con sistemas físicos de tipo *lattice gas* para representar y analizar el dimensionamiento de lotes. Esta aproximación busca capturar la estructura del problema y reducir la carga de exploración. [econpapers.repec](https://econpapers.repec.org/article/sproperea/v_3a27_3ay_3a2027_3ai_3a1_3ad_3a10.1007_5fs12351-026-01105-5.htm)

4. **Validación con heurísticas.** Compararon sus resultados con **búsqueda tabú** (*tabu search*), una metaheurística de optimización. La heurística converge hacia el mínimo global, pero requiere una carga computacional notablemente mayor; el modelo de Mieras identifica el mínimo global con menos cálculos. [arxiv](https://arxiv.org/abs/2412.02714)

## Relación con su tesis Di3

Mieras es ingeniera industrial y doctoranda del Di3; su línea de tesis se titula **“Optimización en el dimensionamiento de lotes de pedidos aplicado a industrias regionales en función del volumen de compra y deterioro temporal de los artículos”**. [ingenieria.uncuyo.edu](https://ingenieria.uncuyo.edu.ar/upload/cronograma-3er-seminario-di3.pdf)

Su aporte central no es simplemente “agrupar pedidos”, sino construir un método que permita decidir el **tamaño y momento óptimos de los lotes** en industrias regionales, cuando los insumos pueden deteriorarse y el proveedor ofrece descuentos según el volumen adquirido.  En términos prácticos, la investigación busca equilibrar costos de compra, inventario, deterioro y descuentos, evitando que la búsqueda de la mejor política de pedidos se vuelva inviable por la cantidad de combinaciones. [ri.conicet.gov](https://ri.conicet.gov.ar/handle/11336/192021)
