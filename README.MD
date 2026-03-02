
```markdown
# 🎓 Student Performance Prediction: Análise Estratégica de Desempenho Escolar

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-Statistics-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Concluído-brightgreen?style=for-the-badge)

## 📄 Sobre o Projeto

Este projeto utiliza Ciência de Dados para prever notas finais de estudantes e, mais importante, **diagnosticar as causas do sucesso ou fracasso escolar**.

Diferente de uma abordagem "caixa preta", este projeto focou na **interpretabilidade**. Utilizamos técnicas estatísticas avançadas (ANOVA e OLS) para limpar ruídos, identificar redundâncias e entregar um modelo que não apenas prevê a nota, mas diz à diretoria da escola **onde agir**.

---

## 💼 Problema de Negócio & Objetivo

Uma instituição de ensino enfrenta dificuldades em identificar precocemente alunos em risco de reprovação. As intervenções atuais são tardias (após as provas).

* **O Desafio:** Criar um modelo preditivo capaz de estimar a nota final com base em comportamentos observáveis durante o semestre.
* **A Pergunta de 1 Milhão de Dólares:** *Quais fatores são, estatisticamente, os maiores ofensores do desempenho?*

---

## 🛠️ Estrutura do Repositório

```text
├── Data/
│   ├── Raw/               # Dados brutos originais
│   └── Processed/         # Dados limpos e otimizados (X_train_final.csv, etc.)
├── img/                   # Gráficos e visualizações do projeto
├── models/                # Modelo serializado (.pkl) pronto para deploy
├── notebooks/             # Jupyter Notebook com o Storytelling completo
├── src/                   # Scripts auxiliares
└── README.md              # Documentação oficial

```

---

## 🚀 Estratégia da Solução

O projeto seguiu um pipeline rigoroso de Data Science:

1. **Análise Exploratória (EDA):** Entendimento profundo das distribuições e correlações.
2. **Feature Engineering:** Criação da variável `Total_Dedication` para capturar a sinergia entre estudo e presença.
3. **Validação Estatística (O Diferencial):**
* Uso de **ANOVA** para validar variáveis categóricas.
* Uso de **OLS (Ordinary Least Squares)** do *Statsmodels* para análise multivariada.


4. **Detecção de Multicolinearidade:**
* O teste OLS revelou que a variável `Risk_Student` era redundante (P-Valor > 0.05) quando analisada junto com a `Attendance`.
* **Ação:** *Backward Elimination* (remoção da variável), tornando o modelo mais leve sem perder precisão.


5. **Modelagem:** Comparação entre Regressão Linear, Ridge e Random Forest.

---

## 📊 Resultados e Métricas

A análise revelou que o desempenho escolar segue um padrão **linear robusto**. Modelos complexos (Random Forest) sofreram com *overfitting* e ruído, enquanto a Regressão Linear brilhou pela simplicidade e eficiência.

| Modelo | MAE (Erro Médio Absoluto) | R² (Explicação da Variância) | Conclusão |
| --- | --- | --- | --- |
| **Regressão Linear (Otimizada)** | **0.95** | **68.49%** | 🏆 **Campeão (Eficiência)** |
| Ridge Regression | 0.95 | 68.49% | Empate Técnico |
| Random Forest | 1.21 | 61.50% | Pior desempenho (Complexidade desnecessária) |

> **Impacto:** O modelo erra, em média, menos de **1 ponto** na nota final do aluno.

---

## 📈 Visualização e Insights de Negócio

### 1. O Veredito: Realidade vs. Previsão

O gráfico abaixo mostra a precisão do modelo. A "linha rosa" representa a previsão perfeita.

* **Insight:** O modelo cria um "tubo de precisão" excelente para a grande maioria dos alunos (notas entre 60 e 80).
* **Ponto de Atenção:** O modelo tende a subestimar alunos "gênios" (notas > 90), indicando que fatores cognitivos (QI, facilidade natural) não estão presentes na base de dados.

### 2. O Que Define a Nota? (Feature Importance)

Para a diretoria da escola, este é o gráfico mais importante. Ele mostra o peso matemático de cada comportamento.

* **Insight 1:** A **Frequência (Attendance)** é o fator #1. Faltar às aulas é estatisticamente fatal para a nota.
* **Insight 2:** O **Envolvimento dos Pais** tem impacto positivo mensurável, validando a necessidade de reuniões de pais e mestres.
* **Insight 3:** A variável de Risco foi removida por ser redundante, provando que monitorar a frequência bruta é mais eficaz do que classificações subjetivas.

### 3. Confiabilidade do Modelo (Resíduos)

A análise técnica dos erros mostra uma **Distribuição Normal (Curva de Sino)** centrada no zero.

* **Conclusão Técnica:** O modelo é não-viesado. Ele não tem tendência a "chutar" sempre para cima ou para baixo. É matematicamente sólido.

---

## 🏁 Conclusão Final

O projeto entregou um modelo preditivo com **68.5% de assertividade explicativa** e um erro marginal de **0.95 pontos**.

Recomendações para a Escola baseadas nos dados:

1. **Foco Total na Presença:** Criar alertas automáticos para alunos com queda de frequência, pois é o maior preditor de queda de nota.
2. **Engajamento Familiar:** Programas que aumentam o envolvimento dos pais terão retorno direto no desempenho acadêmico.
3. **Simplificação de Processos:** Não é necessário criar métricas complexas de "Risco". O acompanhamento básico de horas de estudo e frequência já fornece 90% da inteligência necessária.

---

## 💻 Como Reproduzir

1. **Clone o repositório:**
```bash
git clone [https://github.com/felipetamiozzo/-student-performance-prediction.git](https://github.com/felipetamiozzo/-student-performance-prediction.git)

```


2. **Instale as dependências:**
```bash
pip install -r requirements.txt

```


3. **Execute o Notebook:**
Abra o arquivo `notebooks/student_performance.ipynb` ou utilize o modelo salvo em `models/` para previsões imediatas.

---

## 📞 Contato

**Felipe Tamiozzo** 💼 [LinkedIn](https://www.google.com/search?q=https://linkedin.com/in/felipetamiozzo/)

🐱 [GitHub](https://github.com/felipetamiozzo)

```

```