---
aliases:
  - Credit Assignment
tags:
  - reinforcement_learning
  - multi_agent
---
# Credit Assignment en MARL

El **problema de credit assignment** en [[Multi-Agent Reinforcement Learning (MARL)]] se refiere a la dificultad de determinar qué tan responsable fue cada agente por los resultados obtenidos en una tarea compartida. Es especialmente crítico en entornos **cooperativos**, donde los agentes reciben una **recompensa global** común, pero deben aprender políticas individuales.

## El problema

Cuando todos los agentes reciben la misma recompensa \( R \), no está claro cuál de sus acciones individuales contribuyó más (o menos) al resultado. Esto puede generar:

- **Aprendizaje ineficiente**: los agentes no reciben señales informativas sobre su desempeño.
- **Agentes pasivos ("lazy agents")**: algunos aprenden a no actuar para no perjudicar la recompensa común.
- **Coordinación pobre**: si el crédito no se asigna bien, la cooperación no emerge de forma efectiva.

## Ejemplo

En un entorno donde varios robots deben mover objetos juntos, una recompensa positiva si el objeto llega al destino no indica cuál robot hizo la mayor contribución, ni quién estorbó.

## Soluciones comunes

### Recompensas individuales diseñadas a mano

Asignar a cada agente una señal de recompensa específica basada en su acción. Difícil de escalar o generalizar.

### Recompensa diferencia (Difference Rewards)

Se define una recompensa que estima el aporte de un agente \( i \) comparando el resultado global con el que se obtendría si el agente no participara:

$$
D_i = R - R_{-i}
$$

Donde \( R_{-i} \) es la recompensa obtenida sin el agente \( i \).

### Ventaja contrafactual (como en [[Counterfactual Multi-Agent (COMA)|COMA]])

Se calcula la [[Ventaja Contrafactual]] comparando la acción real del agente con una acción hipotética promedio:

$$
A^i(s, a^i) = Q(s, a^i, a^{-i}) - \sum_{\tilde{a}^i} \pi^i(\tilde{a}^i | s) Q(s, \tilde{a}^i, a^{-i})
$$

Esto aísla el efecto de la acción del agente \( i \) manteniendo fijas las de los demás.

### Críticos factorables (QMIX)

Descomponen el valor global \( Q_{tot} \) como una función de los valores individuales \( Q_i \), asegurando que la política individual siga mejorando el valor conjunto:

$$
Q_{tot}(s, \mathbf{a}) = f(Q_1(s, a_1), \dots, Q_n(s, a_n))
$$

Bajo la condición de monotonía para permitir entrenamiento descentralizado.

## En resumen

El credit assignment es un obstáculo fundamental para la eficiencia y coordinación en entornos multiagente. Resolverlo bien es clave para el éxito de algoritmos de [[Multi-Agent Reinforcement Learning (MARL)]], y ha dado lugar a una gran variedad de métodos especializados.

## Conceptos relacionados

- [[Multi-Agent Reinforcement Learning (MARL)]]
- [[Centralized Training with Decentralized Execution (CTDE)]]
