# mvp-estabilidade-capabilidade-processos
MVP de Engenharia de Dados para análise de estabilidade e capabilidade de processos industriais utilizando Databricks.
# MVP — Estabilidade e Capabilidade de Processos Industriais

MVP desenvolvido com foco em Engenharia de Dados e Qualidade Industrial, utilizando Databricks para construção de um pipeline de dados e aplicação de técnicas de Controle Estatístico de Processo e análise de capabilidade.

## Objetivo

Desenvolver um pipeline de dados em ambiente cloud para coleta, armazenamento, tratamento, modelagem e análise de dados de qualidade de um processo industrial, permitindo avaliar sua estabilidade estatística e sua capacidade de atender aos limites de especificação estabelecidos.

## Problema

Em processos industriais, a conformidade individual das medições com os limites de especificação não garante que o processo esteja estatisticamente estável ou possua capacidade adequada para manter esse desempenho ao longo do tempo.

O MVP busca avaliar esse comportamento por meio de:

- Controle Estatístico de Processo;
- cartas X̄ e R;
- índices Cp e Cpk;
- índices Pp e Ppk;
- comparação entre uma fase histórica e uma fase posterior de monitoramento.

## Perguntas do MVP

1. O processo apresenta comportamento estatisticamente estável?
2. O processo possui capacidade suficiente para atender aos limites de especificação?
3. Qual é a diferença entre a capacidade potencial e o desempenho global observado?
4. A deterioração do processo está mais relacionada à variabilidade ou ao deslocamento da média?
5. Existem alterações relevantes entre a Fase I e a Fase II?
6. Os indicadores de curto e longo prazo apresentam diferenças relevantes?

## Fonte dos Dados

Foi utilizado o conjunto de dados **Piston Rings**, disponibilizado no pacote `qcc` da linguagem R.

A base contém:

- 200 medições de diâmetro;
- 40 subgrupos;
- 5 medições por subgrupo;
- 25 subgrupos na Fase I;
- 15 subgrupos na Fase II.

A característica analisada é o diâmetro interno de anéis de pistão.

Limites utilizados:

- LSL: 73,95 mm
- Alvo: 74,00 mm
- USL: 74,05 mm

## Arquitetura da Solução

O pipeline foi estruturado utilizando uma arquitetura em camadas.

```text
Dataset CSV
    ↓
Bronze
bronze_piston_rings
    ↓
Silver
silver_piston_rings
    ↓
Gold
gold_subgroup_statistics
gold_process_control
gold_phase_comparison
    ↓
Análises
X̄-R | Cp | Cpk | Pp | Ppk
