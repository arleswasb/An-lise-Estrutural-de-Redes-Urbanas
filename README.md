
# Análise Estrutural da Malha Viária: Lagoa Nova, Natal/RN

**Disciplina:** DCA3702 – Estrutura de Dados II

**Instituição:** UFRN – Universidade Federal do Rio Grande do Norte

**Área de Estudo:** Bairro de Lagoa Nova (Natal/RN)

**Ferramentas:** OSMnx · NetworkX · Gephi · Seaborn

---

## 📍 Recorte Geográfico: Lagoa Nova

Lagoa Nova foi selecionado para este estudo por ser o coração geográfico e funcional da Zona Sul de Natal. Diferente de uma análise macro da cidade, o foco aqui é entender como um bairro planejado lida com o fluxo de passagem e a conectividade local.

**Características da Malha:**

* **Eixos Arteriais:** Delimitado por vias de alta capacidade (Av. Prudente de Morais, Av. Salgado Filho e Av. Bernardo Vieira).
* **Estrutura Interna:** Presença de malha em xadrez (grid) que favorece a resiliência e múltiplas rotas.
* **Polos de Atração:** Concentra o Midway Mall, hospitais, escolas e órgãos governamentais, gerando pontos de alta centralidade.

---

## 🎯 Objetivos da Análise Local

1. **Hubs de Bairro:** Identificar quais cruzamentos internos (além das grandes avenidas) sustentam a conectividade do bairro.
2. **Caminhos Mínimos:** Analisar como a estrutura viária facilita ou dificulta o acesso aos serviços essenciais dentro de Lagoa Nova.
3. **Decomposição K-Shell:** Localizar o "núcleo duro" do bairro — as ruas que formam a sub-rede mais densamente conectada.
4. **Pontos de Estrangulamento:** Verificar se o tráfego interno de Lagoa Nova possui dependência crítica de poucas vias.

---

## 📊 Métricas e Visualizações (Escopo Local)

Para o bairro, as figuras agora refletem detalhes mais granulares:

| Ref. | Foco da Análise em Lagoa Nova | Arquivo |
| --- | --- | --- |
| **Fig 02** | Distribuição de Grau: Frequência de cruzamentos de 3 e 4 vias. | `fig02_grau.png` |
| **Fig 04** | **Betweenness:** Identifica ruas residenciais que servem de "atalho" para fugir do trânsito das avenidas principais. | `fig04_betweenness.png` |
| **Fig 05** | **Closeness:** Mostra o centro geométrico-funcional do bairro (onde o acesso a todos os outros pontos é mais rápido). | `fig05_closeness.png` |
| **Fig 06** | **K-Core:** Revela o bloco de ruas mais robusto de Lagoa Nova (geralmente o setor planejado). | `fig06_kshell.png` |
| **Fig 07** | **Eigenvector:** Destaca os nós vizinhos aos grandes eixos comerciais. | `fig07_eigenvector.png` |

---

## 📝 Respostas às Questões (Foco em Lagoa Nova)

* **Q1. Hubs vs. Betweenness:** Em Lagoa Nova, os hubs são as rotatórias e cruzamentos semaforizados. A betweenness alta destaca ruas como a **Jaguarari** e a **São José**, que funcionam como veias de escoamento paralelas às grandes avenidas.
* **Q2. Núcleo k-core:** O núcleo mais denso tende a coincidir com as áreas residenciais mais antigas e planejadas do bairro, onde a conectividade é redundante e eficiente.
* **Q3. O que a Betweenness revela:** Ela aponta quais ruas pequenas sofrem maior pressão de tráfego por servirem de ligação entre a Av. Prudente de Morais e a Av. Salgado Filho.
* **Q4. Visualização Geográfica vs. Estrutural:** No mapa geográfico, vemos as quadras bonitas; no estrutural, percebemos que o bairro é um "sanduíche" pressionado por dois grandes eixos norte-sul.
* **Q5. Regiões Críticas:** As zonas próximas ao Shopping Midway Mall e aos complexos hospitalares apresentam as maiores métricas de centralidade e potencial de congestionamento.

---

## 📁 Estrutura do Repositório

```bash
.
├── project2_lagoa_nova.ipynb  # Notebook com análise focada no bairro
├── rede_lagoa_nova.graphml    # Grafo local exportado
├── figuras/                   # Visualizações detalhadas do bairro
└── README.md                  # Esta documentação

```

---

*Este estudo demonstra como a ciência de redes pode auxiliar no micro-planejamento urbano e na gestão de tráfego local.*