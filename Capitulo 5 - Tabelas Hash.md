Tabelas Hash são estrutura de dados mais complexas usadas para armazenar informações indexadas assim como em arrays, mas qual a diferença?

As tabelas hash utilizam de todos os benefícios de indexação de um array aliado a funções hash, basicamente  uma função hash é uma função que recebe um valor como entrada e retorna um valor único como saída.
por exemplo.
f(maca) = 3
f(ovo) = 0
sempre que eu insiro como entrada o valor maca para minha função hash ela me retorna o valor 3 como resultado, e esse valor só é retornando com o valor maca.

Cada linguagem possui uma implementação nativa de uma tabela hash

```python
precos = dict()

precos["lapis"] = 1.23
precos["caneta"] = 2.23
precos["caderno"] = 8.23

print(precos["caderno"])
```


São muito úteis quando queremos
- modelar relações entre itens
- filtrar por duplicatas
- caching/memorização de dados

#### Colisões
nem sempre uma função hash consegue gerar números diferentes para os valores, pode acontecer de um rato ser igual a um mouse e quando isso acontece a maneira mais simples de resolver é criando uma lista encadeada naquele index.
