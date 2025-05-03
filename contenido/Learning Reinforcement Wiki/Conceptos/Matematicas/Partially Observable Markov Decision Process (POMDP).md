---
aliases:
  - POMDP
  - Partially Observable MDP
tags:
  - matematicas
  - reinforcement_learning
---
# Partially Observable Markov Decision Process (POMDP)

Un Partially Observable Markov Decision Process (POMDP) es una extensión del modelo [[Markov Decision Process (MDP)]] que se utiliza cuando un agente no puede observar completamente el estado del entorno. Es un modelo ampliamente usado en inteligencia artificial para representar decisiones secuenciales bajo incertidumbre tanto en la dinámica del entorno como en la percepción del mismo.

## Cómo funciona

1. **Definición formal**: Un POMDP se define como una tupla (S, A, T, R, Ω, O, γ), donde:
   - *S* es el conjunto de estados posibles.
   - *A* es el conjunto de acciones que el agente puede tomar.
   - *T* es la función de transición: T(s, a, s') = P(s'|s, a).
   - *R* es la función de recompensa: R(s, a).
   - *Ω* es el conjunto de observaciones posibles.
   - *O* es la función de observación: O(s', a, o) = P(o|s', a).
   - *γ* es el factor de descuento (0 ≤ γ ≤ 1).

2. **Incertidumbre observacional**: A diferencia de un MDP, el agente no observa directamente el estado *s*, sino una observación *o* que proporciona información parcial sobre el estado real.

3. **[[Belief State]]**: El agente mantiene una distribución de probabilidad sobre los estados posibles, llamada *belief state*, que se actualiza a medida que el agente actúa y recibe observaciones.

4. **Política de decisión**: El objetivo del agente es encontrar una política π(b) que maximice la recompensa esperada a largo plazo basada en su *belief* actual.

5. **Solución**: Resolver un POMDP implica métodos complejos como algoritmos de aproximación (por ejemplo, punto-base, POMCP) debido a su alta complejidad computacional.

## Ejemplo

- Un robot de rescate que se mueve en un edificio colapsado no puede ver todo el entorno (estado verdadero) pero recibe lecturas de sensores ruidosas (observaciones) para decidir su próximo movimiento y maximizar vidas salvadas.

## Conceptos relacionados

- [[Markov Decision Process (MDP)]]
- [[Belief State]]