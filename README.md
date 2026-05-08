# Análise Estrutural da Malha Viária de Petrópolis, Natal/RN

**Disciplina:** DCA3702 – Estrutura de Dados II  
**Instituição:** UFRN – Universidade Federal do Rio Grande do Norte  
**Ferramentas:** OSMnx · NetworkX · Gephi  

---

## Região analisada

**Bairro Petrópolis**, Natal – Rio Grande do Norte, Brasil.

Petrópolis foi escolhido por ser um bairro tradicional e central de Natal, com malha viária densa e diversificada, que favorece a análise de hubs, centralidade e decomposição k-core sem o custo computacional de regiões maiores. A região concentra serviços, comércio e residências, tornando a análise de mobilidade especialmente relevante.

---

## Objetivo

Aplicar conceitos de grafos em uma rede real — a malha viária de Petrópolis — para identificar:

- **Hubs**: nós de alto grau que concentram conexões viárias
- **Gargalos de mobilidade**: nós com alta betweenness centrality
- **Núcleo estrutural**: regiões densas identificadas pela decomposição k-core
- **Diferenças** entre a perspectiva geográfica e a estrutural da rede

---

## Metodologia

1. **Extração da rede viária** via OSMnx (`network_type="drive"`) a partir do OpenStreetMap
2. **Conversão** para grafo não direcionado (MultiGraph → Graph) para análise estrutural
3. **Cálculo das métricas** com NetworkX
4. **Exportação** do grafo com atributos para o Gephi (`.graphml`)
5. **Visualizações** geográfica e estrutural no Gephi

---

## Métricas calculadas

| Métrica | Descrição |
|---|---|
| **Grau** | Número de vias conectadas a cada nó (interseção) |
| **Distribuição de grau** | Frequência de cada valor de grau na rede |
| **Betweenness Centrality** | Frequência em que um nó aparece em caminhos mínimos |
| **Closeness Centrality** | Proximidade média de um nó a todos os outros |
| **Core Number** | Maior k para o qual o nó pertence a um k-core |
| **K-Core** | Subgrafos maximais onde todo nó tem grau ≥ k |

---

## Estrutura do repositório

```
.
├── project2_petropolis.ipynb   # Notebook principal com toda a análise
├── rede_petropolis.graphml     # Grafo exportado para o Gephi
├── README.md                   # Este arquivo
└── figuras/
    ├── fig01_malha_viaria.png
    ├── fig02_distribuicao_grau.png
    ├── fig03_betweenness.png
    ├── fig04_core_number.png
    ├── fig05_kcore_principal.png
    ├── fig06_scatter_metricas.png
    ├── fig07_correlacao.png
    └── gephi/
        ├── visualizacao_geografica.png
        └── visualizacao_estrutural_forceatlas2.png
```

---

## Respostas às questões obrigatórias

### Q1. Os nós com maior grau coincidem com os nós de maior betweenness?

Não necessariamente. Grau mede importância **local** (quantas vias convergem num ponto), enquanto betweenness mede importância **global** (quantas rotas passam por aquele ponto). Em Petrópolis, encontramos nós com grau moderado mas betweenness elevada — interseções que funcionam como pontes entre setores do bairro, sem serem grandes cruzamentos. A correlação empírica entre as métricas é positiva, mas fraca-moderada (ver heatmap no notebook).

### Q2. O núcleo k-core coincide com os principais hubs?

Parcialmente. O k-core agrupa nós cuja densidade é **mútua e recursiva**: pertencer ao núcleo exige que todos os vizinhos também sejam densamente conectados entre si. Hubs (alto grau) localizados em regiões esparsas do bairro podem ter core number baixo, pois seus vizinhos não formam uma rede densa. Já hubs no centro denso do bairro tendem a estar no núcleo principal.

### Q3. O que betweenness revela que o grau não revela?

Betweenness identifica **gargalos estruturais**: nós que, se removidos, fragmentam o grafo ou aumentam significativamente o comprimento dos caminhos. Um nó com grau 3 mas betweenness alta é uma ponte crítica — bloquear esta interseção (obra, acidente) impacta um grande número de rotas. O grau simplesmente não captura este papel de intermediação global.

### Q4. O que muda entre visualização geográfica e estrutural?

Na **visualização geográfica** (Geo Layout), os nós preservam suas posições reais em latitude/longitude. A forma do bairro é reconhecível, e é possível identificar regiões mais densas geograficamente. Na **visualização estrutural** (ForceAtlas2), nós altamente conectados gravitam para o centro e nós periféricos ficam nas bordas, independentemente de onde estão no mapa. Revela-se que alguns nós geograficamente periféricos são topologicamente centrais — e vice-versa.

### Q5. Existem regiões críticas para mobilidade urbana?

Sim. Os nós com maior betweenness concentrada em Petrópolis revelam os principais gargalos — cruzamentos pelos quais passam a maioria das rotas mais curtas. O núcleo k-core principal identifica a região mais robusta e resiliente (com mais rotas alternativas). Nós fora do núcleo principal, mas com alta betweenness, representam os pontos de maior vulnerabilidade: críticos para o fluxo, mas com baixa redundância de rotas alternativas.

---

## Principais conclusões

- A malha viária de Petrópolis apresenta distribuição de grau concentrada entre 2 e 4, típica de redes viárias planares, com poucos hubs de grau elevado.
- As métricas de grau, betweenness e k-core capturam dimensões distintas e complementares da importância de um nó.
- O núcleo k-core principal coincide geograficamente com as áreas de maior densidade viária do bairro.
- A análise integrada das métricas é essencial: nenhum indicador isolado é suficiente para caracterizar plenamente a estrutura da rede.

---

## Vídeo de apresentação

**Loom:** [link do vídeo — a ser inserido]

---

## Referências

- Boeing, G. (2017). OSMnx: New Methods for Acquiring, Constructing, Analyzing, and Visualizing Complex Street Networks. *Computers, Environment and Urban Systems*, 65, 126–139.
- NetworkX Developers. NetworkX Documentation. https://networkx.org
- Gephi Consortium. Gephi – The Open Graph Viz Platform. https://gephi.org
