
#### Pesquisa Binária
A pesquisa binária é uma técnica que otimiza a busca por um valor em uma lista ordenada, cortando ao meio as possibilidades a cada iteração.

Por exemplo, considerando a lista [1, 2, 3, 4, 5, 6, 7, 8, 9]:

- Em uma pesquisa simples pelo número 8, seriam necessárias 8 interações.
- Já na pesquisa binária: 5 -> 7 -> 8, apenas 3 interações são necessárias.

**Pesquisa simples**: N etapas **Pesquisa binária**: log n etapas

## Exercícios

### 1.1

Suponha que você tenha uma lista com 128 nomes e esteja fazendo uma pesquisa binária. Qual seria o número máximo de etapas para encontrar o nome desejado?

**R:** log₂(128) = 7

### 1.2

Se você duplicar o tamanho da lista, qual seria o número máximo de etapas agora?

**R:** Apenas uma a mais, log₂(256) = 8

## Tempo de Execução

- Pesquisa simples: O(n)
- Pesquisa binária: O(log n)

### Notação Big O

É uma notação especial para indicar a rapidez de um algoritmo, considerando o pior caso.

#### Exemplos Clássicos

- **O(log n)**: Tempo logarítmico (ex: pesquisa binária)
- **O(n)**: Tempo linear (ex: pesquisa simples)
- **O(n * log n)**: Algoritmo rápido de ordenação (ex: quicksort)
- **O(n²)**: Algoritmo lento de ordenação (ex: ordenação por seleção)
- **O(n!)**: Algoritmos bastante lentos (ex: caixeiro viajante)

### Crescimento do Tempo de Execução

O tempo de execução cresce de maneira diferente para cada caso. Por exemplo:

- Em uma pesquisa simples, para 1 bilhão de itens (1 ms por item), levaria 1 bilhão de ms.
- Na pesquisa binária, para 1 bilhão de itens, levaria 30 milissegundos.

## Conclusões

- A quão rápido é um algoritmo é definido pelo crescimento no número de operações com base na quantidade itens.
- O tempo de execução dos algoritmos é definido pela notação Big O.
- O(log n) é mais rápido do que O(n) e torna-se ainda mais rápido conforme a quantidade de itens aumenta.


```python
def busca_binaria(lista, item):
  menor = 0;
  maior = len(lista) - 1;

  while(menor <= maior):
    meio = (menor + maior) // 2
    valorMeio = lista[meio]

    if valorMeio == item:
      return item
    if valorMeio > item:
      maior = meio - 1
    else:
      menor = meio + 1
  
  return None

lista = [1, 5, 7,9]

print(busca_binaria(lista, 3))
print(busca_binaria(lista, 9))
## algoritmo de complexidade O(log n)
```