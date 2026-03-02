
```markdown
# 📊 Student Performance Prediction: Análise de Desempenho Escolar

## 📄 Sobre o Projeto

Este projeto visa prever a nota final de estudantes e diagnosticar os fatores comportamentais que levam ao sucesso ou fracasso escolar. 

Diferente de abordagens tradicionais de "caixa preta", este projeto focou na **interpretabilidade estatística**. Utilizamos testes de hipótese (ANOVA) e regressão multivariada (OLS) para eliminar redundâncias nos dados, resultando em um modelo enxuto e altamente explicativo.

---

## 💼 O Problema de Negócio

Instituições de ensino sofrem com a identificação tardia de alunos em risco. Intervenções feitas após as provas finais costumam ser ineficazes.
* **Objetivo:** Criar um modelo preditivo para identificar alunos com tendência de baixa performance *durante* o semestre.
* **Pergunta Chave:** Monitorar a frequência é suficiente, ou precisamos de métricas complexas de "Risco"?

---

## 🛠️ Tecnologias e Estrutura

* **Linguagem:** Python
* **Bibliotecas:** Pandas, Seaborn, Scikit-Learn, Statsmodels, Joblib.

```text
├── Data/
│   ├── Raw/               # Dados brutos
│   └── Processed/         # Dados limpos (X_train_final.csv, etc.)
├── img/                   # Gráficos exportados
├── models/                # Modelo serializado (.pkl)
├── notebooks/             # Análise completa (Storytelling)
└── README.md              # Documentação

```

---

## 🚀 Metodologia (O Diferencial)

1. **Exploração de Dados (EDA):** Identificação de linearidade forte entre dedicação e nota.
2. **Validação Estatística (ANOVA):** Comprovação de que o tipo de escola e envolvimento dos pais impactam estatisticamente a média.
3. **Detecção de Multicolinearidade (OLS):**
* Identificamos que a variável `Risk_Student` tinha um **P-Valor alto (>0.05)** quando analisada junto com `Attendance`.
* **Decisão:** *Backward Elimination*. Removemos a variável de Risco, pois ela era apenas uma redundância da Frequência. Isso simplificou o modelo sem perder precisão.


4. **Modelagem:** Regressão Linear vs. Random Forest.

---

## 📊 Resultados e Performance

A complexidade não venceu. A **Regressão Linear** superou modelos de árvore (Random Forest) devido à natureza linear dos dados, evitando *overfitting*.

| Modelo | MAE (Erro Médio) | R² (Explicação) | Resultado |
| --- | --- | --- | --- |
| **Regressão Linear** | **0.95 pontos** | **68.49%** | 🏆 **Escolhido** |
| Random Forest | 1.21 pontos | 61.50% | Overfitting |

> **Conclusão:** O modelo erra, em média, menos de 1 ponto na nota final (escala 0-100).

---

## 📈 Visualização dos Resultados

### 1. Previsão vs. Realidade

O modelo criou um "tubo de precisão" para a maioria dos alunos.
*Nota: Observe que o modelo tende a subestimar levemente alunos "gênios" (notas > 95), indicando um teto comportamental.*

### 2. O Que Impacta a Nota? (Feature Importance)

Aqui está a resposta para a diretoria.

1. **Frequência (Attendance):** É o maior preditor isolado de sucesso.
2. **Horas de Estudo:** Relação direta e linear.
3. **Pais Envolvidos:** Alunos com suporte familiar têm "bônus" na nota.

### 3. Confiabilidade (Análise de Resíduos)

A distribuição dos erros forma uma **Curva de Sino (Normal) centrada no Zero**. Isso prova matematicamente que o modelo não é enviesado (não "chuta" sempre para cima ou para baixo).

---

## 🏁 Insights de Negócio & Próximos Passos

1. **Simplificação Operacional:** A escola não precisa gastar recursos classificando alunos como "Risco". O monitoramento simples da **Frequência** já entrega 90% da previsibilidade.
2. **Ação Preventiva:** Criar alertas automáticos para alunos com frequência abaixo de 70%, pois a queda na nota é exponencial.
3. **Próximo Passo (V2):** Coletar dados cognitivos (notas de entrada) para tentar prever melhor os alunos "outliers" de alta performance.

---

## 💻 Como Reproduzir

```bash
# Clone o repositório
git clone [https://github.com/felipetamiozzo/student-performance-prediction.git](https://github.com/felipetamiozzo/student-performance-prediction.git)

# Instale as dependências
pip install -r requirements.txt

# Execute o Notebook ou use o modelo salvo
jupyter notebook notebooks/student_performance.ipynb

```

---

## 📞 Contato

**Felipe Tamiozzo** 💼 [LinkedIn](https://www.google.com/search?q=https://linkedin.com/in/felipetamiozzo/) | 🐱 [GitHub](https://github.com/felipetamiozzo)

```

