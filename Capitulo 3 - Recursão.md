Recursão comumente é usada para simplificar o programa. não necessariamente melhora o desempenho. [[Capitulo 1 - Introdução a algoritmos]]


#exemplo
 Imagine que você precisa procurar uma chave em um monte de caixas, porém algumas caixas possuem caixas dentro. qual seria as maneiras de procurar essa chave?

Uma possível solução
 
![[Pasted image 20240103012420.png]]

Uma solução mais elegante que utiliza o conceito de recursão.

![[Pasted image 20240103012608.png]]


Funções recursivas comumente podem cair em loops infinitos quando não tratadas, como no exemplo abaixo.

```python
def regressivo(i):
 print(i)
 regressivo(i-1)

regressivo(100)
```

Por isso toda função recursiva e divida em duas partes o caso base que não chama a função novamente e o caso recursivo. 
```python
def regressivo(i):
  print(i)
  if(i <= 1): ## caso base
    return
  else: ## caso recursivo
    regressivo(i-1)


regressivo(100)
```


##### A pilha
A pilha é uma estrutura de dados que faz somente duas operações.
pop e push.
pop: remove do topo
push: insere no topo

### Pilha de chamada
Suponha que temos uma função que chama 3 outras funções
```python
def fun3(a):
	print('a' + a)

def func2(b):
	print('b' + b)

def func1(c):
	print('c' + c)

def main(numero): 
	func1(numero)
	func2(numero)
	func3(numero)

main(100)
```

No exemplo a função recebe como parâmetro um numero, então assim que é chamada ela precisa alocar espaço para aquela variável.

Adicionando na pilha. o seguinte valor.

| main | numero | 2 |
| ---- | ---- | ---- |


Logo depois chama a func1

que faz a seguinte adição na pilha

| func1 | c | 2 |
| ---- | ---- | ---- |
| main | numero | 2 |
depois retorna e acontece e remove o func1 da pilha de chamada 

| main | numero | 2 |
| ---- | ---- | ---- |
vai fazer isso com todas as func ate finalizar a main e remover também da pilha de chamada.

sempre que uma função é chamada é adicionado na pilha de chamada suas variáveis.

### Pilha de chamada com recursão
a cada vez que fat é chamado é criado uma alocação de memoria para aquela execução para a variável n e cada chamada vai possuir o seu n sem que um interfira no outro.

```python
def fat(n):
  if(n == 1):
    return 1
  else:
    return n * fat(n-1)
  

print(fat(5))
```

### Relembrando
- Recursão é quando uma função chama a sí mesma
- todas possuem o caso base e o caso recursivo
- todas as chamadas de função vão para a pilha de chamada