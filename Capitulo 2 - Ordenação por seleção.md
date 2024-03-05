
### Array X Listas

###### Arrays 
- guarda espaços lado a lado na memoria
- pode não precisar dos espaços e impede que outros usem
- pode faltar espaços e ter que realocar

Listas
 - guarda em qualquer lugar da memoria
 - não impede que o espaço seja utilizado
 - não precisa realocar ninguém a cada inserção


Quando o assunto é percorrer todos os itens as listas encadeadas são ótimas pois você passará um a um por todos os itens, mas quando é necessário pular de um item para o outro os array são melhores pois você sabe o endereço de cada item no array.  
##### Tempo de execução
|  | *Array* | *Listas* |
| ---- | ---- | ---- |
| *Leitura* | O(1) | O(n) |
| *Inserção* | O(n) | O(1) |
| Eliminação | O(n) | O(1) |

### Inserindo algo no meio da lista
Listas encadeadas são melhores quando você quer inserir elementos no meio da lista, pois será preciso somente apontar o elemento da lista onde você quer inserir para o novo elemento e o novo elemento aponta para o próximo

algo como: 

 x => y => z
 x => o => y => z

#### Seleções
Segue a mesma linha de inserir, é mais rápido na lista encadeada, pois não precisara remanejar ninguém de posição apenas trocar o endereço para qual o anterior ou o próximo estiver apontando.
sempre lembrando que somente será  O(1) se tiver guardado o endereço do primeiro e do último valor da lista que é oque geralmente é feito para realizar essas atualizações de maneira rápida.

#### Ordenação por seleção
imagina que possua uma lista com 10 números e você queira ordenar esses 10 números.
a ordenação por seleção procurará o menor número e adicionará em uma lista nova e removendo da anterior e depois repetirá o processo buscando o novo primeiro maior numero e adicionará no segundo lugar da nova lista assim sucessivamente até acabar os 10 números.

dessa forma a ordenação por seleção executa (n x n) buscas nos itens para fazer a sua ordenação sendo ela um algoritmo não tão rápido. 
O(n x n) ou O(n²).

```python
def BuscaMenor(array):
  menor = array[0]
  menorIndice = 0

  for i in range(1, len(array)):
    if(array[i] < menor):
      menor = array[i]
      menorIndice = i  
  return menorIndice

def ordernacaoPorSelecao(array):
  novoArray = []

  for i in range(len(array)):
    menor = BuscaMenor(array)
    novoArray.append(array.pop(menor))

  return novoArray


print(ordernacaoPorSelecao([5, 3,6,2,10]))

## algoritmo de complexidade O(n²)
```
