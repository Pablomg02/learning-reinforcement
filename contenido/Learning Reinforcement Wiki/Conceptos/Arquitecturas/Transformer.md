---
tags:
  - arquitectura
---
# Transformer

El **Transformer** es una arquitectura de red neuronal introducida en el artículo *"Attention Is All You Need"* (Vaswani et al., 2017), diseñada para procesar secuencias sin recurrencia ni convolución. Su núcleo es el mecanismo de [[Self-Attention]], complementado por [[Multi-head Self-Attention]] y [[Positional Encoding]], lo que le permite modelar dependencias a largo plazo de forma eficiente y paralelizable.

## Arquitectura general

La arquitectura Transformer consta de dos bloques principales:

### 1. **Codificador (Encoder)**
Recibe una secuencia de entrada \( X \) y genera una representación contextual de cada token.

Cada una de sus capas incluye:
- [[Multi-head Self-Attention]]
- Capa feed-forward totalmente conectada
- Normalización + conexiones residuales

Se aplica \( N \) veces en secuencia (típicamente \( N = 6 \)).

### 2. **Decodificador (Decoder)**
Genera la secuencia de salida, paso a paso, condicionado tanto en los tokens generados como en la salida del codificador.

Cada capa del decodificador incluye:
- Masked Self-Attention (para evitar mirar tokens futuros)
- Atención sobre la salida del codificador
- Capa feed-forward
- Normalización + conexiones residuales

## Flujo general

1. Se suman los embeddings de entrada con [[Positional Encoding]].
2. Se pasan por el codificador (todas las capas en paralelo).
3. El decodificador genera un token a la vez, usando atención en sus propias salidas previas y en la representación del codificador.

## Fórmulas clave

Sea \( X \in \mathbb{R}^{n \times d_{\text{model}}} \) la secuencia de entrada embebida.

- Self-attention dentro de cada capa del encoder:
  
  $$
  \text{Attention}(Q, K, V) = \text{softmax}\left( \frac{QK^\top}{\sqrt{d_k}} \right) V
  $$

- Salida de multi-head:

  $$
  \text{MultiHead}(Q, K, V) = \text{Concat}(\text{head}_1, \dots, \text{head}_h) W^O
  $$

## Ventajas

- **Altamente paralelizable**: permite entrenar más rápido que RNNs.
- **Captura de dependencias globales** en pocas capas.
- Base de modelos como BERT, GPT, T5, etc.

## Aplicaciones

- Traducción automática
- Modelos de lenguaje (GPT, BERT)
- Resumen de texto
- Visión por computadora (ViT)

## Enlaces de referencia

- [Paper original: Attention Is All You Need (arXiv)](https://arxiv.org/abs/1706.03762)
- [Visualización interactiva - The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/)

## Conceptos relacionados

- [[Self-Attention]]
- [[Multi-head Self-Attention]]
- [[Positional Encoding]]
- [[Decoder]]
