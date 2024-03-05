[[Capitulo 3 - Recursão]]
O Quicksort é um algoritmo elegante de ordenação que utiliza a técnica de dividir para conquista. Mas oque é essa técnica?

### Dividir Para Conquistar
Podemos dizer que DC(Dividir para Conquistar) é basicamente uma maneira de olhar os problemas. Quando utilizamos DC queremos diminuir o cenário que estamos lidando para ficar tão pequeno que a solução ficaria fácil.

Para resolver um problema com DC precisamos de duas coisas.

1 - Descobrir o caso base, que seria o caso mais simples possível.
2 - Dividir ou diminuir o problema até que se torne o caso base.

Um bom exemplo que utiliza DC é o [algoritmo de Euclides](https://pt.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/the-euclidean-algorithm#:~:text=O%20Algoritmo%20Euclidiano%20para%20encontrar,e%20podemos%20parar%20a%20verifica%C3%A7%C3%A3o.) . 
Ele busca encontrar o MDC entre dois números executando um conjunto de operações(Item 2) repetitivas até que consiga chegar no valor correto (item 1)


Um outro exemplo de resolução de problema que utilizaria DC é:

Imagine que você tenha que somar os valores de um item de um array utilizando recursão.
1- qual o caso base?
	 Geralmente quando se está lidando com arrays o caso bases é quando tiver 1 elemento e/ou 0 elementos.
2- como diminuir o problema?
	 Para diminuir o problema até que chegue no caso base você precisa ir diminuindo o tamanho do array a cada passo. algo como.
	 dado um array [5, 6, 7] poderíamos diminuir com a operação  5 + soma([6,7]) posteriormente com soma 6 + ([7]) até que chegamos no caso base.
	 Como a recursão salva o valor de chamada teríamos algo como 
		6 + ([7]) = 13
		5 + 13 =  18 


4.1 Escreva o código para função soma visto anteriormente

```python
def soma(lista):
  if lista == []:
    return 0
  return lista[0] + soma(lista[1:])

print(soma([1,2,3,4,5]))
```

4.2 Escreva uma função recursiva que conte o número de itens em uma lista.

```python
def count_itens(lista):
  if lista == []:
    return 0
  lista.pop()
  return 1 + count_itens(lista)    

print(count_itens([1,2,3,4,5,6,7,8]))
```

4.3 maior valor de uma lista

```python
def maior_da_lista(lista):
  if len(lista) == 1:
    return lista[0]
  else:
    return max(lista[0], maior_da_lista(lista[1:]))

print(maior_da_lista([1,6,8,3,7,2,7]))
```

4.4. caso base e caso recursivo de uma busca binaria

```python
import random

def busca_binaria(lista, item, esq, dir):
  if esq > dir:
    return None
  meio = (esq + dir) // 2
  if lista[meio] == item:
    return meio
  elif lista[meio] < item:
    return busca_binaria(lista, item, meio + 1, dir)
  else:
    return busca_binaria(lista, item, esq, meio - 1)

lista = sorted([random.randint(1, 100) for _ in range(10)])
item = random.choice(lista)

print('lista', lista)
print('item', item)
print('índice do item', busca_binaria(lista, item, 0, len(lista) - 1))
```



#### Quicksort

É um algoritmo de ordenação que utiliza conceitos de divisão e conquista para ordenar um array de itens.
Ele parte para o caso base que.
arrays de 1 e 0 itens podem simplesmente retornar a si mesmos.
**logo:** 

```python
if len(array) < 2:
	return array
```

Já o próximo caso é caso tenham dois elementos, ai fica simples, compara os dois caso um seja menor que o outro é só troca-los de lugar

**e caso seja 3?**
bom como está usando quicksort que utiliza conceitos de divisão e conquista, você quer diminuir o seu caso em busca do caso base.
Escolha o pivô, que vai ser o número de referencia a partir dai faça a verificação de todos os maiores e todos os menores e repita o processo de quicksort novamente até chegar no caso base.
[5, 4, 1]
escolhendo o 5 como pivô temos
[4,1] + [5] +[]
continuando pois não chegou no caso base o array com itens menores, temos:
[1] + [4] + []
que ao final chegará no caso base por meio da recursão e se unirá com o cinco transformando em
[1, 4, 5]

**e caso seja 4,5,6,...?**

Bom, sempre vai ser possível diminuir casos maiores em casos menores assim como no de 3 itens, seguindo os passos.
1- escolha o pivô
2- separe todos os menores que o pivô
3- separe todos os maiores que o pivô
4- faça um quicksort de todos os menores + pivo  + quicksort de todos os maiores
5- deixe a recursão trabalhar e vá tomar um café   

### Mas como seria o código?

```python
def quicksort(array):
  if len(array) < 2: ## caso base
    return array
  else:
    pivo = array[0] ## escolhendo o pivo
    menores = [i for i in array[1:] if i<= pivo] ## separando menores que o pivo
    maiores = [i for i in array[1:] if i > pivo] ## separando maiores que o pivo
    return quicksort(menores) + [pivo] + quicksort(maiores) ## quebrando em array menores caso até que chegue no caso base
  


desordenado = [10, 53,123,432,675,1,5,8,3,90,2,5,9,2312,6765,12321]
print('Este é um teste do algoritmo quicksort: ', desordenado)
print('resultado ordenado: ', quicksort(desordenado))
```


#### Merge sort x Quicksort
[[Capitulo 1 - Introdução a algoritmos]]

Merge sort e quicksort ambos possuem o complexidade de tempo em notação Big O de O(n log n) mas porque usar um ou o outro?
bem no pior caso o quicksort pode se tornar um algoritmo O(n²) pois caso o array já esteja ordenado não será levado em consideração e ao pegar sempre do inicio eu teria que criar uma  pilha de chamada para cada item, porém a estrategia é escolher o item de maneira aleatória visto que o caso médio será menor que o merge sort na média, pois sua constante O é menor. 

```python
import random

def quicksort(array):
  if len(array) < 2:
    return array
  else:
    indexPivo = random.randint(0, len(array) -1)
    pivo = array[indexPivo]
    menores = [i for i in array[1:] if i<= pivo]
    maiores = [i for i in array[1:] if i > pivo]
    return quicksort(menores) + [pivo] + quicksort(maiores)
  


desordenado = [10, 53,123,432,675,1,5,8,3,90,2,5,9,2312,6765,12321]
print('Este é um teste do algoritmo quicksort: ', desordenado)
print('resultado ordenado: ', quicksort(desordenado))
```

**Um dos poucos casos em que a constante de fato influencia.** 

####  Exercícios
 Quanto tempo levaria em notação bio para completar essas operações
 
 4.5 - Imprimir o valor de cada elemento de um array? 
	 O(n)
 4.6 - Duplicar o valor de cada elemento de um array? 
	 O(n)
 4.7 - Duplicar o valor apenas do primeiro elemento do array? 
	 O(1)
 4.8 - Criar uma tabela de multiplicação com cada elemento do array? ex [1, 2, 3, 4, 5]. multiplicaria cada elemento por 1 depois por 2 depois por 3...? 
	 O(n²)
  