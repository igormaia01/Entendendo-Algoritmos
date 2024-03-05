 
 
 ### Qual objetivo?
 
 Em pesquisa em largura você descobre como encontrar o menor caminho entre um ponto e outro relacionado ao números de segmentos ou pulos que há entre eles, em outras palavras não é necessariamente o caminho mais rápido, mas sim o caminho mais curto. Agora com o algoritmo de dijkistra é possível encontrar o caminho mais rápido entre dois segmentos.

![[Pasted image 20240203133209.png]]

### Funcionamento do algoritmo de dijkstra
cada segmento(aresta) tem um tempo de deslocamento em minutos

![[Pasted image 20240203142557.png]]

Caso a pesquisa seja feita utilizando o algoritmo do caminho mais curto (pesquisa em largura) teremos essa reposta.

![[Pasted image 20240203142834.png]]


Porém esse caminho tem duração de 7 minutos, vamos ver se o algoritmo de djikstra consegue encontrar outro caminho em menos tempo

#### Etapas
O algoritmo de dijkstra funciona em 4 etapas, sendo elas:
1 - Encontre o vértice mais "barato". Este é o vértice em que você consegue chegar no menor tempo possível
2 - Atualize o custo dos vizinhos dese vértice. 
3 - Repita até que você tenha feito isso para cada vértice do grafo
4 - Calcule o caminho final

utilizando o exemplo

**Passo 1:** Encontre o vértice mais barato. Como é o início e você está parado no ponto inicial, pensando se deve ir ao vértice A ou ao vértice B. Quanto tempo leva para alcançar cada um ?

![[Pasted image 20240203143311.png]]

Você leva 6 para chegar ao A e 2 para chegar ao B e outros vertices você não conhece ainda, fazendo uma tabela com essas informações temos.

![[Pasted image 20240203143417.png]]
(obs: como voce nao sabe o tempo para chegar até o fim vamos definir como infinito)

Passo 2: Ao encontrar o vértice, calcule quanto tempo leva para chegar até todos os vizinhos de B, seguindo suas arestas


![[Pasted image 20240203143519.png]]

Opa acabamos de encontrar um caminho mais curto para o vértice A que antes era 6 mas agora o menor é 5 então devemos atualizar o tempo de A na tabela de tempos

e você também encontrou um custo até chegar o fim, que é o custo de chegar ao b mais custo do b até o fim que seria 2 + 5, então temos que até o momento custo para chegar ao fim é 7.

**Passo 3: ** Repita!

Encontre o vértice a qual voce consegue chegar em menor tempo, como já fez isso para o vertice B então agora é o vertice A.

![[Pasted image 20240203143841.png]]

**Passo 2:** Atualize o custos para os vizinhos do vértice A

o unico vizinho do vértice A é o fim, olhando o custo temos que.
![[Pasted image 20240203143923.png]]

olha voce encontrou um caminho menor para chegar até o fim que antes era 7 vindo do vértice B mas quando vem do vertice A é 6.

Como voce verificou todos os vertices, voce descobriu que o menor tempo para chegar do inicio ao fim é de 6 minutos

### Terminologia

Pesos

![[Pasted image 20240203144508.png]]



Ponderado x Não ponderado
![[Pasted image 20240203144521.png]]


Ciclo

![[Pasted image 20240203144547.png]]


grafo direcionado x grafo não direcionado

![[Pasted image 20240203144617.png]]

![[Pasted image 20240203144626.png]]

O algoritmo de dijkistra só funciona com [grafos acíclicos dirigidos](https://pt.wikipedia.org/wiki/Grafos_ac%C3%ADclicos_dirigidos#:~:text=Um%20grafo%20ac%C3%ADclico%20dirigido%20%C3%A9,voc%C3%AA%20e%20termina%20em%20v.)

### Adquirindo um piano

Agora em um exemplo mais "real"

Rama está tentando trocar um livro de música por um piano.

alex: "Eu troco este poster pelo seu livro ou então lhe darei este LP raro do rick astley pelo seu livro e mais 5 reais"
amy: "Ohh ouvi dizer que esse LP tem músicas muito boas, trocarei com você meu baixo ou minha bateria pelo poster ou pelo LP"
beethoven: "Eu estava com vontade de aprender baixo e troco meu piano por qualquer uma das coisas da amy"

com pouco dinheiro rama consegue trocar seu livro de piano por um piano de verdade. Agora ele precisa descobrir como gastar menos ao fazer essas trocas, vamos fazer um grafo com as informações.

![[Pasted image 20240203145305.png]]


Precisamos calcular o menor custa até chegar no piano, seguindo os passos do algoritmo de dijkstra temos os custos por vértice até o momento

![[Pasted image 20240203145405.png]]

agora estamos tambem adicionando uma tabela pai que vai ser atualizada conforme for necessário

![[Pasted image 20240203145445.png]]

**Passo 1:** Encontre o vértice mais barato. Neste caso, o poster é a troca mais barata, pois tem custo 0. 
pergunta, existe alguma troca que o poster possa ficar menor que 0??

**Passo 2:** Descubra o custo ate os vizinhos do poster

voce chegou ate o baixo e a bateria a partir do poster, entao voce encontrou custos ate eles ate o momento e voce atualizou como seus pais sendo o poster


![[Pasted image 20240203145651.png]]



passo 1 novamente

Lp e o próximo vértice mais barato com custo 5


passo 2 novamente 

temos que voce descobriu que pelo lp o custo tanto da bateria quanto do baixo diminui logo voce atualiza o custo e o novo pai dos dois se torna o lp

![[Pasted image 20240203145839.png]]

Passo 1 novamente

o baixo e o proximo item mais barato 

Passo 2 novamente

entao voce atualiza os vizinhos do baixo

![[Pasted image 20240203145943.png]]

passo 1 novamente
 agora sobrou somente a bateria

passo 2 novamente

atualizando os vizinhos da bateria temos



![[Pasted image 20240203150018.png]]


olha voce encontrou um custo mais barato para chegar ao piano pela bateria, logo voce atualiza o pai do piano sendo a bateria e o custo também

Beleza, descobrimos agora que o menor custo para chegar até o piano é de 35.
Agora caso voce queira descrever como chegou até esse custo é só analisar os pais de cada um.
O pai do piano é a bateria


![[Pasted image 20240203150134.png]]

a bateria tem o LP como pai 

![[Pasted image 20240203150152.png]]

O LP tem o livro como pai

![[Pasted image 20240203150209.png]]

então por fim as trocas foram

![[Pasted image 20240203150220.png]]


### Arestas com pesos negativos

Utilizando o mesmo exemplo de troca, imagine o seguinte
![[Pasted image 20240203150633.png]]

Mas agora sarah chega e lhe oferece 7 reais pelo LP

![[Pasted image 20240203150651.png]]


perca que agora voce tem um caminho melhor para chegar ao poster que é comprando o lp vendendo a sara 

![[Pasted image 20240203150729.png]]

mas lembrando que o rama pode trocar o poster pela bateria temos

![[Pasted image 20240203150755.png]]


Seguindo a ideia do algoritmo de dijkstra encontrariamos o valor 35 pois como o poster foi a primeira opcao a partir do livro e o caminho mais curto ate aquele momento era de 0 então após atualizarmos o seus vizinhos ele não será mais levado em consideração pois voce ja havia encontrado o menor caminho.

![[Pasted image 20240203150934.png]]

Logo ele nunca fica assim
![[Pasted image 20240203150944.png]]


Para um algoritmo que leve em consideração valores negativos utilize o algoritmo de [bellman-fod](https://pt.wikipedia.org/wiki/Algoritmo_de_Bellman-Ford#:~:text=O%20Algoritmo%20de%20Bellman%2DFord,as%20arestas%20tenham%20pesos%20positivos.)

## Implemetancao 

```python
## populando inicio
grafo = {}
grafo["inicio"] = {}
grafo["inicio"]["a"] = 6
grafo["inicio"]["b"] = 2

## populando a
grafo["a"] = {}
grafo["a"]["fim"] = 1

## populando b
grafo["b"] = {}
grafo["b"]["a"] = 3
grafo["b"]["fim"] = 5

## populando fim
grafo["fim"] = {}

infinito = float("inf")

## tabela de custos
custos = {}
custos["a"] = 6
custos["b"] = 2
custos["fim"] = infinito

## tabela de pais
pais = {}
pais["a"] = "inicio"
pais["b"] = "inicio"
pais["fim"] = None

## para registrar vertices ja processados
processados = []

#1  Enquanto houver grafos a serem processados --
#2   -> pegue o vertice que esta mais proximo do inicio --
#3   -> atualize os custos para seus vizinhos --
#4   -> se qualquer um dos custos dos vizinhos for atualizado atualize o tambem o pai --
#5   -> marque o vertice como processado --
#6   -> volte ao passo 1

# Função para encontrar o nó com o menor custo que ainda não foi processado
def ache_no_custo_mais_baixo(custos):
  custo_mais_baixo = infinito
  nodo_custo_mais_baixo = None
  # Itera sobre todos os nós
  for nodo in custos:
    custo = custos[nodo]
    # Se o custo do nó atual for menor que o menor custo encontrado até agora
    # e o nó ainda não foi processado
    if custo < custo_mais_baixo and nodo not in processados:
      custo_mais_baixo = custo
      nodo_custo_mais_baixo = nodo
  # Retorna o nó com o menor custo que ainda não foi processado
  return nodo_custo_mais_baixo

# Inicia o processo com o nó de menor custo
nodo = ache_no_custo_mais_baixo(custos)
# Enquanto ainda houver nós para processar
while nodo is not None:
  custo = custos[nodo]
  vizinhos = grafo[nodo]
  # Para cada vizinho do nó atual
  for n in vizinhos.keys():
    # Calcula o novo custo para o vizinho
    novo_custo = custo + vizinhos[n]
    # Se o novo custo for menor que o custo atual do vizinho
    if custos[n] > novo_custo:
      # Atualiza o custo do vizinho
      custos[n] = novo_custo
      # Atualiza o pai do vizinho para o nó atual
      pais[n] = nodo
  # Marca o nó atual como processado
  processados.append(nodo)
  # Passa para o próximo nó de menor custo
  nodo = ache_no_custo_mais_baixo(custos)

# Imprime o grafo, os custos e os pais para verificação
print(grafo)
print(custos)
print(pais)
print("qual o menor custo de inicio até fim? resposta: " , custos["fim"])
```