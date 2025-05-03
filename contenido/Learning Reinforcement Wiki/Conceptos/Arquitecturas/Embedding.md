# Embedding

Un **embedding** es una representación vectorial de objetos discretos (como palabras, tokens, categorías o nodos) en un espacio continuo de dimensión fija. Su objetivo es capturar relaciones semánticas o estructurales entre esos objetos de manera que puedan ser procesados por modelos de aprendizaje automático.

## Propósito

- Permitir el uso de datos simbólicos (palabras, etiquetas, etc.) en redes neuronales.
- Capturar similitudes y relaciones entre objetos en el espacio geométrico.
- Reducir la dimensionalidad de representaciones como one-hot encodings.

## Representación

Sea un vocabulario de tamaño \( V \) y un embedding de dimensión \( d \), se define una matriz de embedding:

$$
E \in \mathbb{R}^{V \times d}
$$

Donde:
- Cada fila \( E_i \) representa el vector de embedding para el ítem \( i \).
- La entrada discreta (por ejemplo, un índice) se mapea al vector correspondiente: \( x_i \mapsto E_i \)

## Aplicaciones

1. **Procesamiento de lenguaje natural**:
   - Word2Vec, GloVe, FastText: embeddings preentrenados para palabras.
   - Embeddings aprendidos desde cero en tareas específicas (e.g., clasificación de texto).

2. **Modelos de recomendación**:
   - Usuarios e ítems representados como vectores embebidos para calcular afinidades.

3. **Visión por computadora**:
   - Representar regiones o clases en espacios vectoriales comparables.

4. **Redes neuronales en grafos**:
   - Embeddings para nodos que capturan su posición estructural.

## Propiedades deseables

- Vectores cercanos en el espacio deben representar entidades similares.
- Pueden ser **estáticos** (preentrenados y fijos) o **dinámicos** (ajustados durante el entrenamiento).

## Ejemplo

Un embedding simple para palabras en una frase:

| Palabra   | Embedding (3D)         |
|-----------|------------------------|
| "gato"    | [0.12, -0.07, 0.81]    |
| "perro"   | [0.15, -0.05, 0.79]    |
| "árbol"   | [-0.44, 0.31, 0.20]    |

Aquí, "gato" y "perro" tienen embeddings cercanos, lo que refleja su similitud semántica.

## Conceptos relacionados

- 
