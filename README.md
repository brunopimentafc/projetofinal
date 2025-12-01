# 📦 Previsão de Atrasos Logísticos no Marketplace Olist  
**Projeto Final — EBAC | Parceria Semantix**  
**Autor:** Bruno Pimenta  

---

## 🎯 Objetivo do Projeto
O objetivo deste projeto é desenvolver um modelo de *Machine Learning* capaz de prever se um pedido realizado no marketplace da Olist será entregue com atraso.

Esse modelo fornece suporte operacional, permitindo:

- Redução de reclamações relacionadas à entrega  
- Aumento da precisão dos prazos informados  
- Diminuição de custos logísticos e indenizações  
- Melhoria da eficiência na distribuição  

O projeto segue todas as etapas do método **CRISP-DM**.

---

## 💼 Justificativa de Negócio
Atrasos nas entregas causam prejuízos financeiros e insatisfação do cliente. Um modelo capaz de identificar pedidos com maior risco de atraso permite:

- Priorização de pedidos críticos  
- Planejamento mais eficiente das rotas  
- Contratação adequada de transportadoras  
- Aumento da confiança do cliente no prazo prometido  

---

## ❓ Perguntas-Chave e Hipóteses

Antes da análise, levantei algumas hipóteses:

- Alguns estados têm índices maiores de atraso  
- Fretes mais caros podem indicar maior dificuldade logística  
- Prazos de entrega curtos podem aumentar o risco de atraso  
- Certos vendedores podem ser mais propensos ao atraso  
- Datas sazonais podem impactar o desempenho logístico  

Essas hipóteses foram verificadas durante a análise exploratória.

---

## 📊 1. Análise Exploratória (EDA)

Principais descobertas:

### 🔹 Estados com maior **custo logístico de atraso**
1. **RJ**  
2. **SP**  
3. **MG**  
4. **BA**  
5. **RS**

Esses estados concentram a maior parte do prejuízo.

### 🔹 Desbalanceamento da variável alvo
A proporção de pedidos atrasados é de aproximadamente **8%**, tornando o problema um caso típico de *imbalanced classification*.

---

## 💰 2. Cálculo do Custo do Atraso

Criei uma métrica de negócio estimando o prejuízo financeiro causado por atrasos:

\\[
\text{custo\_atraso} = 0.5 \times \text{freight\_value}
\\]

Essa estimativa representa custos como:

- Reenvio do item  
- Indenização ao cliente  
- Retrabalho operacional  
- Reputação afetada  

Essa métrica ajudou a identificar os estados com maior impacto financeiro.

---

## 🤖 3. Modelagem Preditiva

Avaliei três modelos:

### **1️⃣ Regressão Logística**
- Alta acurácia, porém recall muito baixo  
- Incapaz de identificar atrasos de forma eficiente  
- **Não recomendado**  

---

### **2️⃣ Random Forest (com `class_weight='balanced'`)**
- Melhorou o recall  
- AUC ~ 0.63  
- Melhor performance do que a regressão logística  

---

### **3️⃣ LightGBM — *Melhor Modelo***
- Melhor equilíbrio entre sensibilidade e precisão  
- Melhor recall da classe atraso (~59%)  
- Acurácia ~ 69%  
- Melhor custo-benefício para decisões logísticas  

O LightGBM foi escolhido como **modelo final do projeto**.

---

## 🏁 Conclusões Gerais

Este projeto permitiu:

- Identificar regiões com maior impacto financeiro causado por atrasos  
- Criar uma métrica de custo aplicável ao negócio  
- Construir modelos preditivos para identificar pedidos críticos  
- Demonstrar um processo completo CRISP-DM aplicado à logística  

O modelo final pode apoiar empresas em:

- Reduzir prejuízos  
- Melhorar a operação logística  
- Aumentar a satisfação do cliente  

---

## 📂 Estrutura do Repositório

