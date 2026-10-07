# AP1 — Grafos

Atividade prática 1 de Teoria dos Grafos: representações de um grafo não direcionado, operações básicas e buscas em largura (BFS) e profundidade (DFS), implementadas em Python puro.

## Descrição

O trabalho usa um grafo com 10 vértices (`A`–`J`) e 11 arestas, representado de três formas: **lista de adjacência**, **matriz de adjacência** e **lista de arestas**.

```
A — B
|   |
C — D — F — G — H — I
|       |
E ——————┘
|
J
```

| Problema | Conteúdo |
|---|---|
| **1.1** | Construção da lista de adjacência: para cada aresta `(u, v)`, adiciona `v` na lista de `u` e `u` na lista de `v`. |
| **1.2** | Conversões entre representações: `adj_para_matriz`, `matriz_para_adj`, `arestas_para_matriz`, `matriz_para_arestas`, `lista_para_arestas` (usa um conjunto `vistos` para não duplicar `(u,v)`/`(v,u)`) e `arestas_para_lista_adj`. |
| **1.3** | Vértices alcançáveis em até 2 conexões a partir de uma origem, nas três representações (todas retornam o mesmo resultado). Comparação de desempenho com `timeit`: a lista de adjacência foi a mais rápida. |
| **2** | Operações básicas: `vizinhos(grafo, v)`, `grau(grafo, v)` e `ha_aresta(grafo, u, v)`. |
| **3** | BFS a partir de `A` com fila: ordem de descoberta, distância até a origem, antecessores, árvore de busca e grau de cada vértice na árvore. |
| **4** | DFS a partir de `A` com pilha de tuplas `(vértice, pai, nível_do_pai)`, empilhando vizinhos em ordem reversa. Comparação de níveis e graus com a BFS. |

### Resultados principais

- **1.3:** a partir de `A`, as estações alcançáveis em até 2 conexões são `B`, `C`, `D` e `E`; a lista de adjacência é a representação mais eficiente.
- **Níveis:** na BFS o nível de cada vértice é a distância mínima real até `A`. Na DFS só `A`, `B` e `D` mantêm o nível; os demais ficam 2 níveis mais profundos, porque a DFS percorre `A → B → D → C` e perde o atalho `A → C`. A diferença surge no único ciclo do grafo (`A-B-D-C-A`).
- **Graus:** a árvore BFS é mais "larga" perto da raiz (`A` tem grau 2); a DFS é mais "linear" (`A` tem grau 1), mas `E` ganha um filho a mais (`F` e `J`).

| Vértice | A | B | C | D | E | F | G | H | I | J |
|---|---|---|---|---|---|---|---|---|---|---|
| Nível BFS | 0 | 1 | 1 | 2 | 2 | 3 | 4 | 5 | 6 | 3 |
| Nível DFS | 0 | 1 | 3 | 2 | 4 | 5 | 6 | 7 | 8 | 5 |
| Grau BFS | 2 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 |
| Grau DFS | 1 | 1 | 1 | 1 | 2 | 1 | 1 | 1 | 0 | 0 |

## Instalação

Requer apenas **Python 3.8+**. Não há dependências externas (usa só a biblioteca padrão, incluindo `timeit`).

```bash
git clone https://github.com/boeckg/ap1-grafos.git
cd ap1-grafos
```

## Uso

**Notebook (recomendado)** — abra `AP1_grafos.ipynb` no Jupyter ou no [Google Colab](https://colab.research.google.com/) e execute as células em ordem (cada problema depende das células anteriores).

**Script** — executa todos os problemas de uma vez:

```bash
python ap1_grafos.py
```

## Estrutura

```
.
├── AP1_grafos.ipynb   # notebook com código, saídas e respostas
├── ap1_grafos.py      # mesmo código exportado como script
├── README.md
├── LICENSE
└── .gitignore
```

## Autor

**Gustavo Boeck da Silva** — Ciência de Dados e Inteligência Artificial, UFSM Campus Cachoeira do Sul
[LinkedIn](https://www.linkedin.com/in/gustavo-boeck-da-silva-1774b2233)


## Status do projeto

Concluído — trabalho acadêmico entregue.
