---
tags:
  - arquitectura
---
# Self-Attention

**Self-Attention** es un mecanismo que permite que cada elemento de una secuencia se relacione con los demás elementos, ponderando su importancia relativa al momento de codificar la información. Es la base fundamental de los modelos [[Transformer]], ampliamente utilizados en procesamiento de lenguaje natural, visión por computadora y otros dominios.

## Cómo funciona

El mecanismo de self-attention transforma una secuencia de vectores de entrada en una secuencia de vectores de salida, donde cada vector de salida es una combinación ponderada de todos los vectores de entrada.

### 1. **Proyecciones lineales**

Para cada vector de entrada \( x_i \), se generan tres vectores mediante proyecciones lineales entrenables:

$$
q_i = W^Q x_i 
$$

$$
k_i = W^K x_i 
$$

$$
v_i = W^V x_i
$$


Donde \( W^Q, W^K, W^V \) son matrices de pesos aprendibles, y \( q_i, k_i, v_i \in \mathbb{R}^{d_k} \).

### 2. **Cálculo de compatibilidades (scores)**

La similitud entre el query \( q_i \) y cada key \( k_j \) se calcula usando el producto punto escalado:

$$
\text{score}_{ij} = \frac{q_i \cdot k_j^\top}{\sqrt{d_k}}
$$

### 3. **Cálculo de pesos de atención**

Se aplica la función softmax para normalizar los scores y obtener los coeficientes de atención:

$$
\alpha_{ij} = \frac{\exp(\text{score}_{ij})}{\sum_{j=1}^n \exp(\text{score}_{ij})}
$$

### 4. **Agregación ponderada de valores**

El vector de salida \( z_i \) para cada posición se calcula como una combinación lineal de los valores \( v_j \), ponderados por los pesos de atención:

$$
z_i = \sum_{j=1}^n \alpha_{ij} \cdot v_j
$$

## Propiedades

- Captura **dependencias de largo alcance** entre elementos de la secuencia.
- Es completamente **paralelizable**, lo que lo hace eficiente computacionalmente.
- Produce representaciones **contextualizadas** de cada entrada.

## Variantes

- **[[Multi-head Self-Attention]]**: Se aplica el mecanismo de self-attention varias veces en paralelo con diferentes subespacios de proyección, y se concatenan los resultados.
- **Masked self-attention**: Se impide que una posición atienda a posiciones futuras, útil en tareas de generación secuencial (e.g., modelos tipo GPT).

## Ejemplo

En la frase: “El gato que viste estaba en el tejado”, la palabra “que” se relaciona tanto con “gato” como con “viste”, y self-attention permite modelar esta relación directamente mediante ponderaciones internas.

## Enlaces de referencia

- [The Illustrated Transformer (jalammar.github.io)](https://jalammar.github.io/illustrated-transformer/)
- [Attention Is All You Need (arXiv)](https://arxiv.org/abs/1706.03762)

## Conceptos relacionados

- [[Transformer]]
- [[Multi-head Self-Attention]]
- [[Positional Encoding]]
- [[Embedding]]
