# Atividade Challenge Enterprise - Sprint2

## Introdução

Este projeto tem como objetivo prever o rendimento agrícola da cultura da laranja, com foco na microrregião de Bebedouro (SP), por meio da aplicação de técnicas de Machine Learning supervisionado sobre dados históricos de produção e índices espectrais derivados de sensoriamento remoto (NDVI).

A solução desenvolvida integra diferentes fontes de dados estruturados em uma base unificada, permitindo identificar padrões produtivos relevantes e fornecer suporte analítico à tomada de decisão no agronegócio, com foco em maior eficiência, previsibilidade e sustentabilidade das safras.

---

## Dados utilzados

Os arquivos usados para a predição do modelo são:
- [NDVI da região](satveg_planilha.xlsx)
- [Produção de Laranja - 2023](Produção_2023_São_Paulo.xlsx)
- [Produção de Laranja - 2022](Produção_2022_São_Paulo.xlsx)
- [Produção de Laranja - 2021](Produção_2021_São_Paulo.xlsx)
  
## Pré-processamento e Integração dos Dados

Durante a construção do modelo, foi necessário realizar etapas fundamentais de preparação dos dados:

- ✅ Filtragem direcionada para a cultura da laranja nos arquivos de produção dos anos de 2021, 2022 e 2023, assegurando que o modelo fosse exclusivamente treinado com dados relevantes à cultura em estudo.
- ✅ Formatação e padronização dos quatro conjuntos de dados principais (NDVI e tabelas de produção), estruturando-os uniformemente com base em Ano, Mês e Município.
- ✅ O dataset de NDVI, originalmente abrangendo o período de 2000 a 2023, foi restrito ao intervalo de 2021 a 2023 para garantir compatibilidade temporal com os dados de produtividade agrícola disponíveis.
- ✅ Aplicou-se um filtro geográfico para considerar apenas os municípios da microrregião de Bebedouro — como Catanduva, Cajobi, Monte Azul Paulista, entre outros — buscando capturar padrões produtivos que compartilham características edafoclimáticas semelhantes.
- ✅ Por fim, os dados foram integrados em uma única base consolidada, combinando variáveis como Ano, Mês, Município, NDVI, Área colhida (ha) e Rendimento (kg/ha), resultando em um conjunto de dados completo e consistente para o treinamento dos modelos de aprendizado de máquina.

---

## Modelos e Avaliação

Foram treinados e comparados os seguintes modelos de regressão:

- **Random Forest Regressor**
- **Decision Tree Regressor**
- **K-Nearest Neighbors**
- **Regressão Linear**
- **SVM** com kernels: linear, polinomial e RBF

### 🔎 Métricas utilizadas:
- R² (Coeficiente de Determinação)
- MAE (Erro Médio Absoluto)
- RMSE (Raiz do Erro Quadrático Médio)
- MAPE (Erro Percentual Absoluto Médio)

---

## Resultados

| Modelo             | R²     | MAE     | RMSE     | MAPE     |
|--------------------|--------|---------|----------|----------|
| **Random Forest**  | 0.9997 | 50.46   | 19.68    | 0.24%    |
| **Decision Tree**  | 1.0000 | 0.00    | 0.00     | 0.00%    |
| **KNN**            | 0.8023 | 2027.02 | 14.59K   | 8.87%    |
| Regressão Linear   | 0.2529 | ~6930   | Alto     | 24.78%   |
| SVM (Linear)       | 0.0796 | ~7000   | Alto     | 25%+     |
| SVM (RBF/Poly)     | ~0.00  | >7000   | Alto     | 30%+     |

> 🔍 **Random Forest foi escolhido como o modelo principal**, pois combinou alta precisão (MAPE < 0.3%) com generalização estável.  
> **Decision Tree**, apesar de excelente, apresentou sinais de overfitting.  
> Os demais modelos serviram de referência para validação.

Foram gerados gráficos de **Real vs Predito** para cada modelo. Eles demonstraram que:

- Random Forest e Decision Tree reproduzem fielmente os valores reais;
- KNN mantém boa aproximação visual;
- Modelos SVM e Regressão Linear mostraram grande dispersão e erros.

---

## Conclusão

O modelo desenvolvido demonstrou alta capacidade preditiva para estimar o rendimento agrícola da cultura da laranja, integrando variáveis ambientais (NDVI) e dados produtivos públicos com precisão.

Com métricas de erro extremamente baixas e desempenho consistente, a solução proposta se mostra uma ferramenta eficiente para apoiar a tomada de decisão no agronegócio, permitindo maior planejamento e otimização das safras.

A metodologia aplicada é escalável, podendo ser facilmente adaptada para outras culturas, regiões e safras, consolidando-se como uma estratégia inteligente e sustentável para a gestão agrícola moderna.

---

### **Vídeo Demonstrativo**
O vídeo apresentando o processo de execução do código desenvolvido:
[https://youtu.be/F8Najp-2RS](https://youtu.be/F8Najp-2RSE)
