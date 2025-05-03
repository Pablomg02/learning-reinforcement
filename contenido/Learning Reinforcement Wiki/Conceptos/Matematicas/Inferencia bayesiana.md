---
tags:
  - matematicas
  - bayes
aliases:
  - bayes
---
# Inferencia bayesiana

La **inferencia bayesiana** es un enfoque estadístico que permite actualizar las creencias sobre un fenómeno o parámetro a medida que se obtiene nueva información, utilizando el Teorema de Bayes como base matemática. Es fundamental en contextos donde la incertidumbre y la evidencia progresiva juegan un papel clave, como en los [[Partially Observable Markov Decision Process (POMDP)]]s o en la actualización de un [[Belief State]].

## Cómo funciona

1. **Definición del problema**: Se parte de una hipótesis \( H \) y se observa un conjunto de datos \( D \).

2. **Aplicación del Teorema de Bayes**:

   $$
   P(H|D) = \frac{P(D|H) \cdot P(H)}{P(D)}
   $$

   Donde:
   - \( P(H) \): Probabilidad *a priori* de la hipótesis.
   - \( P(D|H) \): Verosimilitud de los datos dados la hipótesis.
   - \( P(D) \): Probabilidad marginal de los datos.
   - \( P(H|D) \): Probabilidad *a posteriori*, es decir, la creencia actualizada.

3. **Actualización iterativa**: Cada vez que se observa nueva evidencia, se puede volver a aplicar el teorema para refinar la creencia.

## Ejemplo

- Si un agente cree inicialmente que un sensor tiene un 70% de fiabilidad, pero recibe datos contradictorios con frecuencia, puede reducir su confianza en ese sensor mediante inferencia bayesiana.

## Aplicaciones

- Sistemas de diagnóstico médico.
- Modelos de decisión como [[Partially Observable Markov Decision Process (POMDP)|POMDP]]s.
- Motores de recomendación.
- Aprendizaje automático (machine learning).

## Enlaces de referencia

- [Teorema de Bayes explicado visualmente](https://seeing-theory.brown.edu/bayesian-inference/index.html)

## Conceptos relacionados

- [[Belief State]]
- [[Partially Observable Markov Decision Process (POMDP)]]
