### Grafos
Suponha que você queira ir de uma cidade ate outra usando o menor caminho possível. por exemplo ir de  ARAD ate fagaras, existem mais de uma possibilidade e para representar essas possibilidades podemos desenhar um grafo.

![[Pasted image 20240122180023.png]]

mas oque é um grafo? é um representação de um conjunto de conexões entre pontos. por exemplo. posso dizer que felipe é amigo do marcos logo marcos está conectado ao felipe.
**grafo normal ou não direcionado**
felipe <-> marcos

também posso dizer que marcos deve dinheiro para o felipe logo
**grafo direcionado**
marcos -> felipe 

#### pesquisa em largura 
é um algoritmo que faz a busca de um item dentro de uma grafo, ele ajuda a responder duas questões básicas
1 - Existe algum caminho do vértice A ou vértice B?
2 - Qual o caminho mínimo do vértice A ao vértice B?


##### na prática

Supondo que você seja um agricultor que planta mangas e esteja procurando 
algum revendedor para vender suas mangas na cidade, sua primeira ideia é procurar entre seus amigos.

você -> bob, alice, claire

você vai perguntar primeiramente para seus amigos alice, bob e claire.
da seguinte maneira, você vende mangas? se sim, achou quem você queria se não pergunte o nome dos amigos deles para ir perguntar se eles vendem mangas.

então temos uma lista

lista [bob, alice, claire]

bob voce vende mangas? nao, mas talvez o anuj ou a peggy vendam

lista [alice, claire, anuj, peggy]

alice voce vende mangas ? nao mas talvez a peggy venda

ops a peggy ja havia sido adicionado, como nao queremos perguntar para a mesma pessoa mais de uma vez precisaremos guardar quem ja perguntamos
lista de quem ja perguntamos [bob, alice]

lista [claire, anuj, peggy] 


e assim por diante ate nossa lista esvaziar
### FIla

o algoritmo de busca em largura depende essencialmente de uma fila para funcionar, pois caso você queira encontrar o "menor" caminho entre os vértices você precisa consulta-los na ordem em que estão entrando na sua lista e a estrutura que provem esse comportamento é a fila, onde o primeiro a entrar é o primeiro a sair.


#### Código de uma busca em largura em python na prática
```python

from collections import deque


grafo = {}

grafo["voce"] = ["alice", "bob", "claire"]
grafo["bob"] = ["anuj", "peggy"]
grafo["alice"] = ["peggy"]
grafo["claire"] = ["thom", "jonny"]
grafo["anuj"] = []
grafo["peggy"] = []
grafo["thom"] = []
grafo["jonny"] = []

def pessoa_e_vendendor(nome):
    return len(nome) == 3  


def pesquisa(nome):
  fila_de_pesquisa = deque()
  fila_de_pesquisa += grafo[nome]
  verificadas = []

  while fila_de_pesquisa:
    pessoa = fila_de_pesquisa.popleft()
    if not pessoa in verificadas:
      if pessoa_e_vendendor(pessoa):
        print(pessoa + " e um vendendor de manga!")
        return True
      else:
        fila_de_pesquisa += grafo[pessoa]
        verificadas.append(pessoa)
  return False

print(pesquisa("voce"))

```

### tempo de execução
bom, nesse código você precisa  perguntar para todo os seus amigos se algum deles vende manga logo então precisa entrar em contato com cada item da sua rede (arestas), então é no mínimo O(arestas) mas também precisa controlar o número de pessoa já verificadas para adicionar é O(1) mas para verificar seria O(numero de pessoas) supondo que não esteja ordenado então temos um algoritmo de O(n de arestas  + n de pessoas)

