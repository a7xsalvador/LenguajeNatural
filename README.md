# LenguajeNatural

## Fases de entrenamiento de una red neuronal

Importamos los datos de un corpus en español.

Corpus de español:
- AnCora | Github: https://github.com/UniversalDependencies/UD_Spanish-AnCora

- usamos el conllu parser para leer el corpus: https://pypi.org/project/conllu/ . Es muy usado, se puede trabajar con pip install conllu

- Etiquetas Universal POS (Documentación): https://universaldependencies.org/u/pos/ . Hay referencias universales para clasificar palabras.

## Entrenamiento del modelo- Calculo de conteos
La primera etapa es el cálculo de conteos

- tags(tags) ``tagCountDict``: $C(tag)$
- emisiones(word|tag) ``emissionProbDict``: $C(word|tag)$
- transiciones(tag|prevtag) ``transitionDict``: $C(tag|prevtag)$

## Cálculo de probabilidades

- Probabilidades de transición
$$
P(tag|prevtag)=\frac{C(prevtag,tag)}{C(prevtag)}
$$


- Probabilidades de emisión

$$
P(word|tag)=\frac{C(word,tag)}{C(tag)}
$$


## Algoritmo de Viterbi

Se trata de hallar la probabilidad de viterbi $v_t(j)$ en cada elemento $j$ de una cadena de palabras.

$$
v_t(j) = \max_i{(v_{t-1}(i) \times C_{ij}\times P(palabra|j))}
$$

Para el primer elemento, la probabilidad de Viterbi está dada por
$$
v_1(j)= \rho_j^{(0)} \times P(palabra|j)
$$

donde $\rho_j^{(0)}$ es la probabilidad de encontrar la categoría gramatical $j$.
