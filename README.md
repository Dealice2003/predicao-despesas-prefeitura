# 📊 Aplicação de Modelos Preditivos para Prever Despesas Futuras – Salto Grande, SP

Este repositório apresenta o processo de construção do dataset de despesas públicas da Prefeitura de **Salto Grande (SP)** e a aplicação de modelos de aprendizado de máquina para prever gastos futuros, com base em dados do sistema **Gemmap** e do **Portal da Transparência**.

---

## 🔎 1. Construção do Dataset

### Fonte dos Dados
Os dados foram extraídos do sistema **Gemmap**, plataforma utilizada pela Prefeitura de Salto Grande para gestão administrativa e financeira.  
As mesmas informações estão disponíveis no **Portal da Transparência**, garantindo acesso público e maior confiabilidade.

Inicialmente, os registros estavam distribuídos em cinco tabelas distintas, referentes aos exercícios de **2020 a 2024**.

### Consolidação e Limpeza
- Unificação das tabelas anuais em um único dataset.  
- Padronização de nomes de colunas e tipos de dados.  
- Exclusão de variáveis redundantes.  
- Tratamento de valores nulos e inconsistências.  
- Padronização da coluna **Data Pagamento** para formato de série temporal.  

### Colunas Mantidas
- **Ano** → identifica o exercício financeiro.  
- **Texto do Item do Elemento da Despesa** → descreve a natureza do gasto.  
- **Aplicação Nome** → identifica a secretaria ou departamento responsável.  
- **Valor Pago** → montante financeiro desembolsado em cada empenho.  
- **Data Pagamento** → permite análise temporal e detecção de sazonalidade.  

### Variável-Alvo
A variável escolhida para predição foi **Valor Pago**, por refletir o montante efetivamente desembolsado pela Prefeitura.  
Outras alternativas, como **Valor Empenhado** e **Valor Liquidado**, podem ser exploradas em estudos futuros.

---

## 📈 2. Análise Exploratória

### Estatísticas Gerais (2020–2024)
- **Total gasto:** R$ 232.765.328,52  
- **Número de pagamentos:** 89.212  
- **Média por transação:** R$ 2.609,13  
- **Mediana:** R$ 300,00  
- **Maior pagamento:** R$ 2.014.200,00  
- **Menor valor:** –R$ 109.338,45 (estornos/ajustes)  

A distribuição apresenta **alta assimetria**, com muitas transações de baixo valor e alguns pagamentos de grande magnitude.

### Análise Temporal
- Oscilações mensais entre **R$ 2 milhões e R$ 7,3 milhões**.  
- Crescimento acumulado de **+199,4%** no período de 5 anos.  
- **Dezembro/2024** registrou o maior gasto mensal (R$ 7,3 milhões).  

### Principais Áreas de Gasto
- **Ações de Governo**: *Manutenção do Centro de Saúde* e *Serviços Administrativos* (≈ R$ 30 milhões).  
- **Tipos de Despesa**: *Vencimentos e Salários* (≈ R$ 50 milhões), seguidos por *Serviços de Terceiros – Pessoa Jurídica* e *Contribuições Previdenciárias*.  

➡️ Apenas **36 ações (21,8% do total)** concentraram **80% dos gastos**, confirmando a **Lei de Pareto**.

---

## 🤖 3. Modelagem Preditiva

Três abordagens foram aplicadas para previsão das despesas:

- **ARIMA** → modelo estatístico de séries temporais.  
- **Prophet** → modelo desenvolvido pelo Facebook para séries temporais com sazonalidade.  
- **Random Forest Regressor** → modelo baseado em aprendizado de máquina supervisionado.  

### Resultados dos Modelos
O **Random Forest** apresentou melhor desempenho, com menor erro médio (RMSE ≈ R$ 1,7 milhão), superando ARIMA e Prophet.

---

## 📊 4. Previsão para Jan–Jun/2025

### Valores Previsto x Real
| Mês | Previsto (R$) | Real (R$) | Diferença | Erro (%) |
|-----|--------------|-----------|-----------|-----------|
| Jan | 2.570.313,72 | 2.484.689,28 | –85.624,44 | –3,33% |
| Fev | 3.123.835,04 | 3.818.685,01 | +694.849,97 | +22,24% |
| Mar | 4.527.858,13 | 5.861.197,87 | +1.333.339,54 | +29,45% |
| Abr | 5.516.944,27 | 5.528.872,06 | +11.928,30 | +0,28% |
| Mai | 4.531.431,73 | 4.832.134,98 | +100.703,26 | +2,22% |
| Jun | 4.457.428,89 | 4.439.538,30 | –17.892,58 | –0,40% |
| **Total** | **23.727.811,78** | **26.965.117,50** | **+2.037.504,19** | **+8,59%** |

---

## 📌 5. Conclusões

- O modelo de **Random Forest** obteve os melhores resultados entre os testados.  
- O **erro médio foi de 8,59%** no primeiro semestre de 2025.  
- A maior divergência ocorreu em **fevereiro e março**, meses atípicos com gastos acima do padrão histórico.  
- A análise exploratória revelou concentração de recursos em poucas áreas e crescimento contínuo das despesas.  

### Próximos Passos
- Incluir variáveis adicionais (ex.: valor empenhado e liquidado).  
- Testar modelos híbridos (Machine Learning + Séries Temporais).  
- Aplicar análise setorial detalhada (saúde, educação, obras etc.).  

---


