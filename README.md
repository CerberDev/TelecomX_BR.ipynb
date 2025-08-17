# Análise de Evasão de Clientes (Churn) da TelecomX

## 🎯 1. Objetivo do Projeto

Este projeto consiste em uma análise exploratória completa sobre a base de clientes da **TelecomX**, uma empresa fictícia do setor de telecomunicações. O objetivo principal é identificar os principais fatores que influenciam a **evasão de clientes (Churn)**, ou seja, o cancelamento dos serviços.

Através da análise de dados demográficos, contratuais e de consumo, buscamos extrair insights acionáveis que possam embasar a criação de estratégias proativas de retenção, visando aumentar a lealdade dos clientes e a saúde financeira da empresa.

## 🛠️ 2. Estrutura e Metodologia

A análise foi conduzida seguindo um pipeline estruturado de Ciência de Dados, desde a obtenção dos dados brutos até a geração de insights e recomendações estratégicas.

### 2.1. Carga e Preparação dos Dados

  - **Fonte de Dados**: Os dados foram consumidos a partir de um arquivo `JSON` com estrutura aninhada, simulando um cenário real de consumo via API.
  - **Normalização**: A estrutura aninhada foi "achatada" (normalizada) para um formato tabular utilizando a biblioteca Pandas, facilitando a manipulação e análise.
  - **Limpeza e Tratamento**: Foi realizado um rigoroso processo de limpeza, que incluiu:
      - Correção do tipo de dado da coluna `TotalCharges` (de texto para numérico).
      - Remoção de registros com a variável alvo (`Churn`) em branco.
      - Padronização de categorias redundantes (ex: `"No internet service"` foi convertido para `"No"`).

### 2.2. Engenharia de Features

  - **Criação de `Fatura_Diaria`**: A coluna `Fatura_Mensal` foi usada para calcular o gasto diário médio, normalizando a métrica para facilitar comparações.
  - **Criação de `Qtd_Servicos_Adicionais`**: Uma nova feature foi criada para somar a quantidade de serviços extras contratados por cada cliente.

### 2.3. Transformação dos Dados

  - **Binarização**: Colunas categóricas com duas opções (ex: "Sim"/"Não", "Masculino"/"Feminino") foram convertidas para o formato numérico (1/0).
  - **Tradução**: Todas as colunas e seus respectivos valores foram traduzidos para o português, tornando o dataset mais acessível e intuitivo para stakeholders locais.

## 📊 3. Análise Exploratória e Principais Insights

A análise visual e estatística dos dados permitiu a identificação de padrões claros sobre o perfil dos clientes que evadem.

#### **Taxa de Evasão Geral: 26.6%**

A análise revelou que mais de um quarto dos clientes na base de dados cancelaram seus serviços, destacando a relevância do problema.

#### **Perfil do Cliente com Alto Risco de Evasão:**

A combinação das análises nos permitiu traçar um perfil claro do cliente com maior propensão a evadir:

> É um **cliente recente**, com **contrato Mês a Mês**, que paga uma **fatura mensal elevada** (geralmente por serviços como Fibra Óptica) e **não possui muitos serviços adicionais** contratados.

**Fatores de Maior Impacto (Confirmados por Correlação):**

1.  **Tipo de Contrato (Correlação com Evasão: +0.41)**: Ter um contrato "Mês a Mês" é, de longe, o fator que mais aumenta a chance de evasão.
2.  **Tempo de Contrato (Correlação: -0.35)**: O tempo de permanência é o fator de retenção mais forte. Quanto mais antigo o cliente, menor a chance de cancelamento.
3.  **Serviço de Internet Fibra Óptica (Correlação: +0.31)**: Clientes com este serviço, apesar de ser premium, apresentam uma taxa de evasão significativamente maior.
4.  **Fatura Mensal (Correlação: +0.19)**: Faturas mais altas estão diretamente associadas a uma maior probabilidade de evasão.

## 🚀 4. Recomendações Estratégicas

Com base nos insights gerados, as seguintes ações são recomendadas para reduzir a taxa de churn:

1.  **Incentivar Contratos de Longo Prazo (Alta Prioridade)**:

      - **Ação**: Criar campanhas focadas em clientes com contrato "Mês a Mês", oferecendo descontos ou benefícios claros para a migração para planos de 1 ou 2 anos.

2.  **Melhorar a Experiência para Clientes de Fibra Óptica**:

      - **Ação**: Investigar a causa da alta evasão neste segmento. Realizar pesquisas de satisfação sobre a estabilidade e o custo-benefício do serviço para identificar pontos de atrito.

3.  **Fortalecer o Onboarding de Novos Clientes**:

      - **Ação**: Implementar um programa de "boas-vindas" nos primeiros 90 dias, focando em garantir que o cliente entenda sua fatura e perceba o valor dos serviços contratados, mitigando o risco de cancelamento precoce.

4.  **Desenvolver um Modelo Preditivo**:

      - **Ação**: Utilizar este estudo como base para construir um modelo de Machine Learning capaz de prever a probabilidade de evasão de cada cliente. Isso permitirá que a equipe de retenção atue de forma proativa, com ofertas personalizadas, antes que o cliente decida cancelar.

## 💻 5. Como Executar o Projeto

### Pré-requisitos

  - Python 3.x
  - Bibliotecas:
      - Pandas
      - Matplotlib
      - Seaborn
      - Jupyter Notebook

### Instalação

Clone o repositório e instale as dependências:

```bash
git clone https://github.com/seu-usuario/TelecomX_BR.ipynb.git
cd TelecomX_BR.ipynb
pip install -r requirements.txt
```

### Execução

Abra e execute o notebook `TelecomX_BR.ipynb` em um ambiente Jupyter:

```bash
jupyter notebook TelecomX_BR.ipynb
```
