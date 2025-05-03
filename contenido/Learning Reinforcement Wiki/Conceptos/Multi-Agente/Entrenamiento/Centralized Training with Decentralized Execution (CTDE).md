---
tags:
  - multi_agent
  - reinforcement_learning
---
# Centralized Training with Decentralized Execution (CTDE)

**CTDE (Centralized Training with Decentralized Execution)** es un marco de entrenamiento para [[Multi-Agent Reinforcement Learning (MARL)]] que separa el proceso de aprendizaje (centralizado) del proceso de actuación (descentralizado). Esta separación se logra comúnmente utilizando arquitecturas basadas en **actor-crítico**.

## Cómo funciona

1. **Arquitectura actor-crítico**:
   - Cada **agente \( i \)** tiene:
     - Un **actor**: \( \pi_i(a_i | o_i) \), que mapea observaciones locales \( o_i \) a acciones \( a_i \).
     - Un **crítico centralizado**: \( Q_i(o_1, \dots, o_n, a_1, \dots, a_n) \), que evalúa la calidad de la acción del agente considerando observaciones y acciones de *todos* los agentes.

2. **Entrenamiento centralizado**:
   - El **crítico** usa información completa del entorno (observaciones y acciones de todos los agentes).
   - Permite que cada agente aprenda una política más robusta al modelar con precisión cómo sus decisiones interactúan con las de los demás.

3. **Ejecución descentralizada**:
   - En tiempo de ejecución, el **actor** solo requiere la observación local \( o_i \) para actuar.
   - Esto permite que los agentes operen de manera independiente, sin comunicación entre ellos.

4. **Ventajas del enfoque**:
   - **Desacopla el aprendizaje de la ejecución**: Se puede aprovechar la información completa durante el entrenamiento sin necesidad de compartirla en la práctica.
   - **Mejora la estabilidad**: Al modelar el entorno y otros agentes durante el aprendizaje, se reduce la no estacionariedad.
   - **Escalable**: Compatible con entornos donde los agentes no pueden o no deben compartir información en tiempo real.

## Ejemplo técnico

En [[Multi-Agent Deep Deterministic Policy Gradient (MADDPG)|MADDPG]], por ejemplo:
- El actor \( \pi_i \) de cada agente es entrenado para maximizar el valor estimado por su crítico:
  $$
  \nabla_{\theta_i} J(\theta_i) = \mathbb{E} \left[ \nabla_{\theta_i} \pi_i(a_i | o_i) \cdot \nabla_{a_i} Q_i(o, a_1, \dots, a_n) \right]
  $$
- El crítico \( Q_i \) tiene acceso a todas las observaciones y acciones \( (o_1, \dots, o_n, a_1, \dots, a_n) \), pero solo durante el entrenamiento.

## Enlaces de referencia

- [CTDE explicado en el paper de MADDPG](https://arxiv.org/abs/1706.02275)

## Conceptos relacionados

- [[Actor-crítico]]
- [[Multi-Agent Deep Deterministic Policy Gradient (MADDPG)|MADDPG]]
- [[Multi-Agent Reinforcement Learning (MARL)]]
- [[Reinforcement Learning (RL)]]
