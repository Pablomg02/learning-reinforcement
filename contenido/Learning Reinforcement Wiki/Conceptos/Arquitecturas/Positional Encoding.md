---
tags:
  - arquitectura
---
# Positional Encoding

El mecanismo de atención, incluyendo el [[Self-Attention]] y [[Multi-head Self-Attention]], no tiene conocimiento del orden de los elementos en la secuencia, ya que opera de forma completamente paralela. Para incorporar esta noción de orden, los modelos [[Transformer]] utilizan **Positional Encoding**.

## Idea principal

Se añade un vector que codifica la posición de cada token en la secuencia, y este se **suma** al embedding original del token antes de aplicarle atención.

Si \( x_i \) es el embedding del token en la posición \( i \), y \( p_i \) es su codificación posicional, el vector final es:

$$
z_i = x_i + p_i
$$

Esto permite que la red distinga, por ejemplo, entre “El perro mordió al hombre” y “El hombre mordió al perro”.

## Fórmulas de codificación sinusoidal

En el modelo original del Transformer, se usa una codificación determinista basada en funciones seno y coseno:

$$
PE_{(pos, 2i)} = \sin \left( \frac{pos}{10000^{2i/d_{\text{model}}}} \right) \\
PE_{(pos, 2i+1)} = \cos \left( \frac{pos}{10000^{2i/d_{\text{model}}}} \right)
$$

Donde:
- \( pos \): posición del token.
- \( i \): índice de la dimensión dentro del vector.
- \( d_{\text{model}} \): dimensión del embedding.

Esto genera un patrón único y continuo que permite al modelo inferir relaciones relativas entre posiciones.

## Otras variantes

Además del codificador sinusoidal, existen métodos alternativos:
- **Aprendizaje de posiciones**: usar vectores de posición como parámetros entrenables.
- **Posiciones relativas**: codificar distancias entre tokens en lugar de posiciones absolutas (e.g., en T5 o Transformer-XL).

## Importancia

- Es esencial para preservar la **estructura secuencial**.
- Permite que el modelo aprenda **patrones dependientes del orden**.
- Facilita la generalización a secuencias de longitud no vistas durante el entrenamiento.

## Conceptos relacionados

- [[Self-Attention]]
- [[Multi-head Self-Attention]]
- [[Transformer]]
