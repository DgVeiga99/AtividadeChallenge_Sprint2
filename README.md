# Atividade Challenge Enterprise - Sprint2

## Introdução

Este projeto visa prever o **rendimento agrícola da cultura da laranja**, com foco na **microrregião de Bebedouro (SP)**, por meio de técnicas de **Machine Learning supervisionado** aplicadas a dados de sensoriamento remoto (NDVI) e produção histórica. A solução integra múltiplos conjuntos de dados estruturados e fornece uma abordagem prática para auxiliar a tomada de decisão no agronegócio.

---
## Dados utilzados

Os arquivos usados para a predição do modelo são:
- [NDVI da região](satveg_planilha.xlsx)
- [Produção de Laranja - 2023](Produção_2023_São_Paulo.xlsx)
- [Produção de Laranja - 2022](Produção_2022_São_Paulo.xlsx)
- [Produção de Laranja - 2021](Produção_2021_São_Paulo.xlsx)
  
## Pré-processamento e Integração dos Dados

Durante a construção do modelo, foi necessário realizar etapas fundamentais de preparação dos dados:

- ✅ **Filtragem específica das culturas de laranja** nos arquivos de produção dos anos de 2021, 2022 e 2023, de forma a manter o foco do projeto apenas nessa cultura.
- ✅ **Padronização e pré-processamento** de quatro conjuntos de dados (NDVI e tabelas de produção), com formatação unificada por ano, mês e município.
- ✅ O arquivo NDVI original continha dados desde 2000. Para manter a coerência com os dados de produção, **filtramos apenas o período entre 2021 e 2023**.
- ✅ **Filtramos os municípios da microrregião de Bebedouro**, como Catanduva, Cajobi, Monte Azul Paulista, entre outros, com o objetivo de extrair padrões locais compatíveis com o clima e o solo da região.
- ✅ Por fim, os dados de NDVI e produtividade foram **relacionados e integrados** em uma única base, contendo: `Ano`, `Mês`, `Município`, `NDVI`, `Área colhida (ha)` e `Rendimento (kg/ha)`.

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

O modelo final é capaz de prever o **rendimento agrícola da laranja com alta acurácia**, utilizando dados públicos e acessíveis.  
Essa abordagem pode ser aplicada em outras culturas e regiões, oferecendo uma ferramenta inteligente de apoio à produção e gestão agrícola.

---

### **Vídeo Demonstrativo**
O vídeo apresentando o processo de execução do código desenvolvido:
[Challenge Enterprise_Sprint2](https://youtu.be/XWOVIXWogJM)
