---
tags:
  - matematicas
  - reinforcement_learning
---
# Belief-State

El belief state o estado de creencia es una representación probabilística del conocimiento que tiene un agente sobre el estado real del entorno cuando este no es completamente observable. Es un componente clave en los modelos de decisión como los [[Partially Observable Markov Decision Process (POMDP)|POMDP]]s, donde el agente debe tomar decisiones basadas en información incompleta o incierta.

## Cómo funciona

1. **Definición**: Un belief state es una distribución de probabilidad sobre todos los posibles estados del entorno. Representa la creencia del agente sobre cuál podría ser el estado real.

2. **Inicialización**: El agente comienza con una distribución inicial (por ejemplo, uniforme si no tiene información previa).

3. **Actualización bayesiana**: Cada vez que el agente toma una acción y recibe una observación, actualiza su *belief state* usando la regla de Bayes:

   $$
   b'(s') = \eta \cdot O(s', a, o) \sum_{s \in S} T(s, a, s') \cdot b(s)
   $$

   Donde:
   - $b$ es el belief previo.
   - $T$ es la función de transición.
   - $O$ es la función de observación.
   - $\eta$ es un factor de normalización.

4. **Toma de decisiones**: El agente elige sus acciones con base en el *belief state*, como si fuera el estado real.

## Ejemplo

- En un juego de cartas ocultas, un jugador no ve las cartas del oponente, pero mantiene una *creencia* probabilística sobre qué cartas puede tener basándose en las jugadas previas.

## Enlaces de referencia
- [Insertar enlace](https://www.google.es)

## Conceptos relacionados

- [[Partially Observable Markov Decision Process (POMDP)]]
- [[Inferencia bayesiana]]

