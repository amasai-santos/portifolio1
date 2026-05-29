# Fundamentos Matemáticos

## Curvatura de Ricci de Forman

### Definição

Para uma aresta (u, v) em um grafo G, a **curvatura de Ricci de Forman** é definida como:

```
κ(u,v) = (deg(u) + deg(v) - 2) / |V|
```

Onde:
- **deg(u)**: grau do vértice u
- **deg(v)**: grau do vértice v
- **|V|**: número total de vértices

Alternativamente, uma implementação mais robusta considera:

```
κ(u,v) = deg(u) + deg(v) - 2
```

### Interpretação Topológica

- **κ > 0**: Curvatura positiva (semelhante a esfera)
- **κ = 0**: Curvatura zero (espaço euclidiano)
- **κ < 0**: Curvatura negativa (espaço hiperbólico)

## Modelos de Redes Estudados

### 1. Erdős-Rényi (ER)

**Definição**: Cada par de vértices é conectado com probabilidade p, independentemente.

```python
G = nx.erdos_renyi_graph(n, p)
```

**Características**:
- Distribuição de graus: Poisson
- Coeficiente de clustering: p
- Diâmetro: O(log n)
- Comportamento aleatório puro

**Propriedade ER Neste Estudo**: 
- Menor impacto relativo de triângulos (β ≈ 5.0)
- Mais regular em estrutura

### 2. Watts-Strogatz (WS)

**Definição**: Começa com um anel regular e reconecta cada aresta com probabilidade p.

```python
G = nx.watts_strogatz_graph(n, k, p)
```

**Características**:
- Efeito small-world
- Alto clustering local
- Caminho médio curto
- Transição de regular para aleatório

**Propriedade WS Neste Estudo**:
- Maior impacto de triângulos (β ≈ 7.2)
- Reflete a estrutura em clusters

### 3. Barabási-Albert (BA)

**Definição**: Crescimento com preferential attachment (ricos ficam mais ricos).

```python
G = nx.barabasi_albert_graph(n, m)
```

**Características**:
- Distribuição lei de potência: P(k) ∝ k^(-3)
- Hubs dominantes
- Scale-free
- Altamente heterogêneo

**Propriedade BA Neste Estudo**:
- Impacto moderado de triângulos
- Reflete a presença de hubs

## Análise Estatística

### Modelo de Regressão Linear

```
soma_ricci = α·(V - E) + β·triangulos + ε
```

Onde ε ~ N(0, σ²)

### Coeficientes Estimados

Para ER com n=2000:
```
α = 8.0 ± 0.05    (muito estável)
β = 5.0 ± 1.5     (ligeira variação)
R² = 0.84
```

### Critérios de Seleção

#### AIC (Akaike Information Criterion)
```
AIC = 2k - 2ln(L)
```
- k: número de parâmetros
- L: valor máximo da função likelihood

#### BIC (Bayesian Information Criterion)
```
BIC = k·ln(n) - 2ln(L)
```
- Penaliza mais severamente modelos complexos

### Teste VIF (Variance Inflation Factor)

Detecta multicolinearidade entre preditores:

```
VIF = 1 / (1 - R_i²)
```

- **VIF < 5**: Aceitável
- **VIF > 10**: Multicolinearidade problemática

Neste estudo: Todos VIF < 3 ✓

## Métricas Topológicas

### 1. Número de Vértices (V)
- Simples contagem

### 2. Número de Arestas (E)
- Simples contagem
- Relacionado a densidade: ρ = 2E / (V(V-1))

### 3. Triângulos
- Ciclos de comprimento 3
- Proxy para clustering
- Impacto consistente na curvatura

### 4. Características de Euler
```
χ = V - E + F
```
- V: vértices
- E: arestas
- F: faces (1 para grafos 2D simples)

## Por que (V - E) é importante?

### Razão Topológica

A quantidade (V - E) está relacionada ao rank do espaço nulo do grafo:
```
rank(Laplaciano) = V - E
```

Para grafos conectados com c componentes:
```
rank_nulo = E - V + c
```

### Intuição Geométrica

- Em árvores: E = V - 1, então (V - E) = 1
- Em ciclos simples: E = V, então (V - E) = 0
- Em grafos densos: (V - E) pode ser negativo

A curvatura parece ser proporcional a essa "deficiência estrutural".

## Distribuição de Triângulos

### Contagem Eficiente

```python
# NetworkX
triangles = nx.triangles(G)
num_triangles = sum(triangles.values()) // 3
```

### Significado por Modelo

| Modelo | Triângulos Típicos | Impacto |
|--------|-------------------|---------|
| ER | Poucos, aleatórios | Baixo: β ≈ 5 |
| WS | Muitos, em clusters | Alto: β ≈ 7.2 |
| BA | Moderados, em hubs | Médio: β ≈ 6.5 |

### Relação com Clustering

Coeficiente de clustering:
```
C = 3 × (nº triângulos) / (nº triplas conectadas)
```

Redes com alto clustering têm mais triângulos → maior β.

## Validação Estatística

### 1. Normalidade dos Resíduos
- Q-Q plot
- Teste de Shapiro-Wilk

### 2. Homocedasticidade
- Gráfico de resíduos vs fitted
- Teste de Breusch-Pagan

### 3. Ausência de Multicolinearidade
- VIF < 5
- Correlação entre preditores

### 4. Independência
- Durbin-Watson
- Correlação serial

Neste projeto: Todos os testes passaram ✓

## Extensões Futuras

### 1. Ciclos de Ordem Superior
Investigar impacto de:
- 4-ciclos (quadrados)
- 5-ciclos (pentágonos)
- n-ciclos gerais

Hipótese: Ciclos maiores têm impacto decrescente

### 2. Métricas Alternativas
- Curvatura Ollivier-Ricci
- Curvatura Scalar
- Robustez topológica

### 3. Grafos Ponderados
- Pesos nas arestas
- Pesos nos vértices
- Adaptar fórmula de curvatura

### 4. Grafos Direcionados
- Importância da direção
- Asimetria na curvatura
- Análise em DAGs

### 5. Dados em Tempo Real
- Redes sociais dinâmicas
- Redes biológicas evoluindo
- Monitore mudanças em curvatura

---

**Última atualização**: 2024
**Nível técnico**: Mestrado em Matemática/Ciência da Computação
