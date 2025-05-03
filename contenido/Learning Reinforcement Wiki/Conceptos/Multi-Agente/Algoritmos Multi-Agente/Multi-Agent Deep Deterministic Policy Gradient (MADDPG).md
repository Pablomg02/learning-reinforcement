---
tags:
  - multi_agent
  - reinforcement_learning
  - algoritmos
aliases:
  - MADDPG
---
# Multi-Agent Deep Deterministic Policy Gradient (MADDPG)

**MADDPG (Multi-Agent Deep Deterministic Policy Gradient)** es un algoritmo de [[Multi-Agent Reinforcement Learning (MARL)]] que extiende el [[Deep Deterministic Policy Gradient (DDPG)]] a entornos multiagente, permitiendo políticas diferenciables y continuas para cada agente, con entrenamiento centralizado pero ejecución descentralizada ([[Centralized Training with Decentralized Execution (CTDE)]]).

## Cómo funciona

1. **Entrenamiento centralizado**:
   - Cada agente tiene su propia política (actor), pero durante el entrenamiento se accede a la información de todos los agentes.
   - El crítico de cada agente recibe como entrada las observaciones y acciones de todos los agentes:
     $$
     Q_i(x, a_1, \dots, a_N)
     $$
     donde \( x \) es el estado global y \( a_j \) es la acción del agente \( j \).

2. **Ejecución descentralizada**:
   - Cada agente actúa solo con su observación local durante la ejecución, lo que lo hace aplicable a entornos distribuidos.

3. **Actualización de políticas**:
   - Basada en DDPG, usa una política determinista y redes neuronales para representar tanto el actor como el crítico.
   - El objetivo del actor es maximizar el valor estimado por su crítico correspondiente.

4. **Ventajas**:
   - Escalable a múltiples agentes.
   - Mejora la estabilidad del entrenamiento en entornos multiagente.
   - Se adapta bien a tareas cooperativas o con competencia limitada.

## Ejemplo

- Un equipo de drones que necesita aprender a patrullar una zona, evitando solaparse y cubriendo eficientemente todo el terreno, entrenados usando MADDPG para aprender políticas coordinadas.

## Enlaces de referencia

- [MADDPG original paper (arXiv)](https://arxiv.org/abs/1706.02275)

## Conceptos relacionados

- [[Multi-Agent Reinforcement Learning (MARL)]]
- [[Reinforcement Learning (RL)]]
- [[Deep Deterministic Policy Gradient (DDPG)]]
