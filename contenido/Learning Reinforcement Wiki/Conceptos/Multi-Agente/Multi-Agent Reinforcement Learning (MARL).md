---
tags:
  - reinforcement_learning
  - multi_agent
aliases:
  - MARL
---
# Multi-Agent Reinforcement Learning (MARL)

El **Multi-Agent Reinforcement Learning (MARL)** es una extensión del [[Reinforcement Learning (RL)]] en la que múltiples agentes interactúan dentro de un entorno compartido, aprendiendo simultáneamente a través de la experiencia y la retroalimentación. Cada agente puede tener objetivos individuales o cooperativos, lo que introduce desafíos adicionales como la no estacionariedad y la coordinación.

## Cómo funciona

1. **Componentes**:
   - Varios agentes \( \{A_1, A_2, \dots, A_n\} \) que aprenden en paralelo.
   - Un entorno compartido, donde las acciones de un agente afectan potencialmente a los demás.
   - Recompensas individuales \( r_i \) o globales, dependiendo del tipo de interacción (competitiva, cooperativa o mixta).

2. **Tipos de entornos**:
   - **Cooperativos**: Todos los agentes comparten la misma función de recompensa.
   - **Competitivos**: Las recompensas están en conflicto (e.g., juegos de suma cero).
   - **Mixtos**: Combinan elementos de cooperación y competencia.

3. **Desafíos clave**:
   - **No estacionariedad**: El entorno cambia a medida que otros agentes aprenden.
   - **Coordinación**: Los agentes deben aprender a trabajar juntos.
   - **Exploración más compleja**: La dinámica de múltiples agentes aumenta la complejidad del espacio de políticas.

4. **Algoritmos representativos**:
   - **Independent Q-learning**
   - **[[Centralized Training with Decentralized Execution (CTDE)]]**
   - **[[Multi-Agent Deep Deterministic Policy Gradient (MADDPG)]]**
   - **QMIX**, **COMA**, **MAPPO**

## Ejemplo

- En un entorno de simulación de tráfico, múltiples vehículos autónomos (agentes) deben aprender a coordinarse para evitar colisiones y optimizar el flujo de tránsito.

## Enlaces de referencia

- [Survey on Multi-Agent Reinforcement Learning](https://arxiv.org/abs/1810.05587)

## Conceptos relacionados

- [[Reinforcement Learning (RL)]]
- [[Markov Decision Process (MDP)]]
- [[Partially Observable Markov Decision Process (POMDP)]]
- [[Belief State]]
