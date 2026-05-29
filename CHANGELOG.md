# Changelog

Todas as mudanças notáveis neste projeto serão documentadas neste arquivo.

O formato é baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/)
e este projeto adere ao [Semantic Versioning](https://semver.org/lang/pt-BR/).

## [1.0.0] - 2024

### Added
- Análise completa de curvatura de Ricci em redes complexas
- Implementação de cálculo de curvatura de Forman
- Modelos de rede: Erdős-Rényi, Watts-Strogatz, Barabási-Albert
- Análise de redes reais: Autonomous System, Power Grid, PGP Network
- Análise estatística com regressão linear múltipla
- Validação cruzada e testes de qualidade de ajuste
- Documentação matemática completa
- Visualizações de distribuições de coeficientes
- Testes de estabilidade com 100 iterações por modelo

### Análise Detalhada
- Fórmula principal: soma = α·(V - E) + β·triângulos
- Coeficientes estimados para cada modelo de rede
- Análise de variância (ANOVA) 
- Teste VIF para multicolinearidade
- Intervalos de confiança dos coeficientes
- Critérios AIC/BIC para seleção de modelos

## Roadmap Futuro

### v1.1.0 (Próximo)
- [ ] Análise de ciclos de ordem superior (4, 5, n-ciclos)
- [ ] Suporte para grafos direcionados
- [ ] Otimização de performance para redes grandes
- [ ] Testes unitários com pytest

### v1.2.0
- [ ] Curvatura Ollivier-Ricci como alternativa
- [ ] Análise de grafos ponderados
- [ ] Dashboard interativo com plotly
- [ ] Exportação de resultados em múltiplos formatos

### v2.0.0
- [ ] Biblioteca Python independente (`network_curvature`)
- [ ] API pública
- [ ] CLI tools para análise
- [ ] Integração com outras bibliotecas de network analysis

## Versionamento

Este projeto usa [Semantic Versioning](https://semver.org/):
- MAJOR: Mudanças incompatíveis com API
- MINOR: Novas funcionalidades compatíveis
- PATCH: Correções de bugs

---

**Última atualização**: 2024
