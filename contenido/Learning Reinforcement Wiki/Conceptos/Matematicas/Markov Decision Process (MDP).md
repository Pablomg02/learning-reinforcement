---
tags:
  - matematicas
  - reinforcement_learning
aliases:
  - MDP
---
# Markov Decision Process (MDP)

Un **Markov Decision Process (MDP)** es un modelo matemático para la toma de decisiones en entornos donde el estado del sistema es completamente observable y evoluciona de forma probabilística. Es una herramienta central en inteligencia artificial, teoría de control y optimización dinámica, especialmente en el [[Reinforcement Learning (RL)]].

## Cómo funciona

1. **Componentes**:
   - \( S \): Conjunto de estados posibles.
   - \( A \): Conjunto de acciones disponibles.
   - \( T(s, a, s') \): Función de transición, probabilidad de pasar del estado \( s \) al estado \( s' \) al tomar la acción \( a \).
   - \( R(s, a) \): Recompensa esperada al tomar la acción \( a \) en el estado \( s \).
   - \( \gamma \): Factor de descuento \( (0 < gamma < 1) \), que determina la importancia de las recompensas futuras.

2. **Propiedad de Markov**: La probabilidad de transición al siguiente estado depende solo del estado actual y la acción tomada, no del historial pasado.

3. **Objetivo**: Encontrar una política óptima \( \pi(s) \) que maximice la recompensa acumulada esperada:

   $$
   V^\pi(s) = \mathbb{E} \left[ \sum_{t=0}^{\infty} \gamma^t R(s_t, a_t) \right]
   $$

4. **Solución**: Se puede encontrar la política óptima utilizando algoritmos como:
   - Iteración de valores.
   - Iteración de políticas.
   - Programación dinámica.

## Ejemplo

- Un robot que debe recorrer un almacén evitando obstáculos y optimizando el tiempo de entrega de paquetes puede ser modelado como un MDP.

## Enlaces de referencia

- [Markov Decision Process - Wikipedia](https://en.wikipedia.org/wiki/Markov_decision_process)

## Conceptos relacionados

- [[Partially Observable Markov Decision Process (POMDP)]]
- [[Belief State]]
- [[Inferencia bayesiana]]
