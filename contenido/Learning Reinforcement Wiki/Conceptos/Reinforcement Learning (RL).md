---
aliases:
  - RL
tags:
  - reinforcement_learning
---
# Reinforcement Learning (RL)

El **Reinforcement Learning (RL)** o aprendizaje por refuerzo es un paradigma de aprendizaje automático donde un agente aprende a tomar decisiones mediante la interacción con un entorno, con el objetivo de maximizar una señal de recompensa acumulada a largo plazo.

## Cómo funciona

1. **Elementos principales**:
   - **Agente**: El que toma decisiones.
   - **Entorno**: El sistema con el que interactúa el agente.
   - **Estado (\(s\))**: Representación del entorno en un momento dado.
   - **Acción (\(a\))**: Elección del agente.
   - **Recompensa (\(r\))**: Retroalimentación del entorno tras una acción.
   - **Política (\(\pi\))**: Estrategia del agente para decidir acciones.
   - **Valor (\(V(s)\))** y **Q-valor (\(Q(s, a)\))**: Medidas del beneficio esperado.

2. **Ciclo de aprendizaje**:
   - El agente observa un estado \(s\), toma una acción \(a\), recibe una recompensa \(r\) y observa el nuevo estado \(s'\).
   - Con esta experiencia, ajusta su política para obtener mejores recompensas futuras.

3. **Funciones objetivo**:
   - Maximizar la **recompensa acumulada descontada**:
     $$
     G_t = \sum_{k=0}^{\infty} \gamma^k r_{t+k}
     $$
     Donde \( \gamma \) es el factor de descuento.

4. **Métodos comunes**:
   - **Basados en valores**: Q-learning, SARSA.
   - **Basados en políticas**: Policy Gradient.
   - **Métodos actor-crítico**: Combinan política y función de valor.

## Ejemplo

- Un videojuego donde un agente aprende a jugar solo, mejorando su desempeño al recibir puntos por victorias o penalizaciones por errores.

## Enlaces de referencia

- [Deep Reinforcement Learning - Spinning Up](https://spinningup.openai.com/en/latest/)

## Conceptos relacionados

- [[Markov Decision Process (MDP)]]
- [[Partially Observable Markov Decision Process (POMDP)]]
- [[Inferencia bayesiana]]
- [[Multi-Agent Reinforcement Learning (MARL)]]
