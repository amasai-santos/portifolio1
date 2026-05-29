# Network Ricci Curvature Analysis

Análise comparativa de curvatura de Ricci em diferentes modelos de redes complexas.

## 📋 Descrição do Projeto

Este projeto investigou a aplicação da **curvatura de Ricci de Forman** como métrica topológica para caracterizar diferentes modelos de redes. O objetivo foi estabelecer relações matemáticas entre propriedades estruturais das redes e a soma da curvatura de Ricci.

### Redes Analisadas

- **Erdős-Rényi (ER)**: Modelo aleatório clássico
- **Watts-Strogatz (WS)**: Modelo small-world
- **Barabási-Albert (BA)**: Modelo preferential attachment (scale-free)
- **Redes Reais**: 
  - Autonomous System
  - Power Grid
  - PGP Network

## 🎯 Principais Descobertas

### Fórmula Principal

A soma da curvatura de Ricci foi modelada como:

$$\text{soma} = \alpha \cdot (V - E) + \beta \cdot \text{triângulos}$$

Onde:
- **V**: número de vértices
- **E**: número de arestas
- **triângulos**: número de ciclos de tamanho 3

### Propriedades de Cada Modelo

| Modelo | α (médio) | β (médio) | R² | Observações |
|--------|-----------|-----------|-----|------------|
| ER | ~8.0 | ~5.0 | 0.84 | Menor impacto de triângulos |
| WS | ~8.5 | ~7.2 | 0.87 | Maior clustering |
| BA | ~8.3 | ~6.5 | 0.86 | Distribuição heterogênea |

### Estabilidade Estrutural

Os coeficientes mostraram alta estabilidade através de 100 iterações para cada modelo:
- Variância mínima em ER
- Pequenas flutuações esperadas em modelos estocásticos
- Confirmação da relação linear com R² > 0.8 em todos os casos

## 📊 Metodologia

1. **Geração de Redes**: Criação de 100 instâncias para cada modelo com 2000 nós
2. **Cálculo de Curvatura**: Implementação da curvatura de Ricci de Forman para cada aresta
3. **Análise Estatística**: Regressão linear múltipla (OLS) para modelagem
4. **Visualização**: Distribuição de coeficientes e métricas de qualidade do ajuste

## 🛠️ Tecnologias Utilizadas

- **Python 3.x**
- **NetworkX**: Geração e análise de redes
- **Pandas**: Manipulação de dados
- **StatsModels**: Análise estatística e regressão
- **Matplotlib/Seaborn**: Visualização de dados
- **NumPy**: Operações numéricas

## 📁 Estrutura do Projeto

```
.
├── README.md              # Este arquivo
├── analysis.ipynb         # Notebook principal com toda análise
├── requirements.txt       # Dependências do projeto
└── docs/
    └── mathematical_background.md  # Fundamentos matemáticos
```

## 🚀 Como Usar

### Instalação

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/network-ricci-analysis.git
cd network-ricci-analysis

# Instale as dependências
pip install -r requirements.txt
```

### Executar a Análise

```bash
# Abra o notebook Jupyter
jupyter notebook analysis.ipynb
```

O notebook contém:
1. Importação de bibliotecas
2. Geração de redes (ER, WS, BA)
3. Cálculo da curvatura de Ricci
4. Carregamento de redes reais
5. Análise estatística detalhada
6. Visualizações e gráficos

## 📈 Resultados

### Validação Cruzada

A regressão foi validada através de:
- Testes AIC/BIC para seleção de modelos
- Análise de variância (ANOVA)
- Teste VIF para multicolinearidade
- Intervalos de confiança dos coeficientes

### Conclusões

1. **Independência de E**: A métrica é melhor descrita por (V - E) do que E isoladamente
2. **Importância de Triângulos**: Ciclos de tamanho 3 têm impacto significativo e consistente
3. **Generalização**: O modelo funciona bem em redes reais apesar de treinamento em redes sintéticas
4. **Estabilidade**: Coeficientes mantêm consistência em diferentes instâncias

## 💡 Potenciais Extensões

- [ ] Análise de ciclos maiores (4, 5, n ciclos)
- [ ] Métricas de curvatura alternativas
- [ ] Aplicação em grafos direcionados e ponderados
- [ ] Comparação com outras métricas topológicas
- [ ] Dataset público com resultados pré-computados

## 📚 Referências Conceituais

- Forman, R. (2003). "Bochner's method for cell complexes and applications to hypergeometric functions"
- Newman, M. E. J. (2003). "The structure and function of complex networks"
- Barabási, A. L. & Albert, R. (1999). "Emergence of scaling in random networks"
- Watts, D. J. & Strogatz, S. H. (1998). "Collective dynamics of 'small-world' networks"

## 📝 Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo LICENSE para detalhes.

## 🤝 Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou fazer pull requests.

## ✉️ Contato

Para dúvidas ou sugestões sobre este projeto, entre em contato.

---

**Status**: Pesquisa Concluída | **Último Update**: 2024 | **Linguagem**: Python 3.x
