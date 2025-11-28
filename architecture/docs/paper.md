# Comparative Performance of Fractal Hexagonal Meshes vs LEO Dynamic Graphs Under Node Failure

## Abstract
Este trabalho apresenta um benchmark comparativo entre uma topologia fractal (malha hexagonal inspirada na "Flor da Vida") e um grafo dinâmico estilo LEO (Starlink-like), avaliando resiliência, conectividade pós-falha e tempo de recuperação sob remoção massiva de nós. O objetivo é fornecer um estudo reprodutível e métricas objetivas para comparação entre arquiteturas de rede com implicações para comunicações resilientes e infraestruturas distribuídas.

## 1. Método
### 1.1 Implementação
- Plataforma: Python + NetworkX + NumPy (versões: preencha aqui se quiser).
- Topologias:
  - **Fractal Hex Mesh**: malha hexagonal radial com redundância e conexões radiais.
  - **Starlink-like**: grafo aleatório com grau médio controlado para simular conectividade LEO.
- Experimentos:
  - N = 1000 nós em cada cenário.
  - Em cada rodada, removemos aleatoriamente 10% dos nós.
  - Reroteamento: simulação de self-healing básica com reroute por k-shortest paths e reconexão local (descrição do algoritmo no repositório).
  - Repetições: S seeds diferentes para estatística (preencher S).

### 1.2 Métricas
- **Diâmetro** pós-falha
- **Porcentagem de pares conectados** (parwise reachability)
- **Tempo de recuperação** (simulado, em ms)
- **Número médio de arestas** (densidade)

## 2. Resultados (modelo)
> **OBS:** Substitua os valores abaixo pelos resultados reais do seu run. Os números abaixo são placeholders — mantenha formatado como tabela para o paper final.

| Topologia | Diâmetro pós-falha | % pares conectados | Tempo médio recuperação (ms) | Arestas |
|---|---:|---:|---:|---:|
| Fractal Hex Mesh | 12 | 99.1% | 8.2 | X |
| Starlink-like | 9 | 99.8% | 4.1 | Y |

### 2.1 Análise
- Interprete as diferenças em termos de redundância estrutural, custo de arestas e complexidade de reroute.
- Discuta tradeoffs: fractal = menos arestas, quase tão resiliente; LEO = mais eficiente em tempo de recuperação.

## 3. Reprodutibilidade
- Scripts: `/fractal_mesh_sim/fractal_sim.py` (simulador), `/temporal_buffer/buffer.py`.
- Seeds: incluir lista de seeds usados.
- Como rodar (exemplo):
  1. Instalar dependências: `pip install -r requirements.txt`
  2. Rodar benchmark: `python fractal_mesh_sim/fractal_sim.py --runs 50 --seed 42`
  3. Gerar CSV/plots: saída salva em `results/` (detalhes no script)

## 4. Conclusão
- Resumo: a topologia fractal apresenta desempenho competitivo frente à topologia dinâmica LEO, com vantagens de custo em número de arestas e arquitetura mais simples de manter. Para aplicações específicas (latência crítica), o modelo LEO ainda leva vantagem.
- Próximos passos: simular mobilidade orbital realista, integrar métricas de carga e criar visualizações comparativas robustas.

## 5. Agradecimentos e Licença
- Autor: Alessander Pereira Oliveira (DelPaxton)  
- Licença: MIT (conforme repo)
