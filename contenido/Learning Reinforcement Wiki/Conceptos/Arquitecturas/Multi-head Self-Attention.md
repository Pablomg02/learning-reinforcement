---
tags:
  - arquitectura
  - attention
---
# Multi-Head Self-Attention

El mecanismo de **Multi-Head Self-Attention** es una extensión directa del [[Self-Attention]], diseñada para mejorar la capacidad del modelo de capturar múltiples tipos de relaciones simultáneamente entre los elementos de una secuencia. En lugar de usar una única función de atención, el modelo ejecuta varias atenciones en paralelo, denominadas *cabezas* (*heads*), y luego combina sus resultados.

## Idea principal

Cada cabeza aprende una representación distinta del contexto, ya que tiene sus propios parámetros de proyección. Esto permite que el modelo se enfoque en distintos aspectos de la secuencia al mismo tiempo (por ejemplo, relaciones sintácticas vs. semánticas).

## Proceso matemático

Si tenemos \( h \) cabezas de atención, el procedimiento es el siguiente:

1. **Proyecciones independientes**:
   Para cada cabeza \( i \in \{1, \dots, h\} \), se proyectan las entradas en subespacios distintos:

   $$
   Q_i = X W_i^Q, \quad K_i = X W_i^K, \quad V_i = X W_i^V
   $$

2. **Atención por cabeza**:
   Cada cabeza realiza su propia operación de atención escalada:

   $$
   \text{head}_i = \text{softmax} \left( \frac{Q_i K_i^\top}{\sqrt{d_k}} \right) V_i
   $$

3. **Concatenación y proyección final**:
   Se concatenan todas las cabezas y se aplica una proyección lineal final:

   $$
   \text{MultiHead}(X) = \text{Concat}(\text{head}_1, \dots, \text{head}_h) W^O
   $$

   Con \( W^O \), una matriz entrenable que transforma la concatenación en la dimensión original.

## Ejemplo intuitivo

En una oración ambigua, como “El banco está al lado del río”, una cabeza puede aprender a enfocarse en el sentido geográfico de “banco” y otra en su posible sentido financiero. Esto es posible porque cada cabeza tiene libertad para aprender patrones distintos.

## Beneficios

- Incrementa la **expresividad** del modelo sin incrementar drásticamente el coste computacional.
- Facilita el aprendizaje de **representaciones contextualizadas diversas**.
- Es fundamental para el éxito del [[Transformer]] y sus variantes.

## Conceptos relacionados

- [[Self-Attention]]
- [[Transformer]]
- [[Positional Encoding]]
