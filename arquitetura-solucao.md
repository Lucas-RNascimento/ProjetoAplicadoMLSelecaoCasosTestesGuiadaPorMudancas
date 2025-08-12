#  Arquitetura da Solução — Priorização de Testes Guiada por Mudanças

##  Objetivo
Definir os componentes e o fluxo da solução que prioriza testes com base nas mudanças de código associadas a bugs.

---

##  Visão Geral da Arquitetura

###  1. Entrada de Dados
- **Fonte:** Dataset com bugs (`bug_id`, `func_before`, `func_after`)
- **Formato:** JSON, CSV ou banco de dados
- **Pré-processamento:** Extração de funções modificadas, linhas alteradas

###  2. Análise de Mudanças
- **Componentes:**
  - Parser de funções (via regex ou AST)
  - Comparador de versões (`func_before` vs `func_after`)
- **Saída:** Lista de funções impactadas por bug

###  3. Mapeamento de Cobertura
- **Objetivo:** Associar funções modificadas aos testes que as cobrem
- **Fontes possíveis:**
  - Dados simulados
  - Logs de cobertura (ex: JaCoCo, cobertura.py)
  - Histórico de execução de testes

###  4. Módulo de Priorização
- **Critérios:**
  - Frequência de falha
  - Impacto da mudança
  - Cobertura cruzada
- **Algoritmos possíveis:**
  - Heurístico simples (pontuação por função)
  - Machine Learning (se houver dados históricos)
  - Greedy ou ranking por peso

### 5. Simulador de Execução
- **Função:** Simular execução dos testes priorizados
- **Saída:** Métricas como tempo estimado, cobertura acumulada, bugs detectados

### 🔹 6. Visualização e Relatórios
- **Ferramentas:** Matplotlib, Seaborn, Dash ou Streamlit
- **Saídas:**
  - Gráficos de cobertura
  - Ordem de execução
  - Histórico de falhas

---

## Diagrama de Componentes (em texto)
[ Dataset de Bugs ] ↓ [ Parser de Funções ] ↓ [ Comparador de Mudanças ] ↓ [ Mapeador de Cobertura ] ↓ [ Módulo de Priorização ] ↓ [ Simulador de Execução ] ↓ [ Visualização / Relatórios ]

