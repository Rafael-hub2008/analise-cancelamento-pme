# Laboratório de Análise de Dados de PMEs - Cancelamento de Clientes (Texto otimizado com auxílio de IA)

## 📋 Sobre o Projeto

Análise completa de dados de cancelamento de clientes em uma empresa de SaaS. O objetivo é identificar os principais fatores que levam ao churn (cancelamento) e fornecer insights acionáveis para reduzir a taxa de cancelamentos.

## 🎯 Problema de Negócio

Uma PME com base de clientes em crescimento enfrenta uma taxa alarmante de cancelamentos. Precisamos entender:
- **Por que** os clientes estão cancelando?
- **Quais** são os padrões comportamentais dos clientes que cancelam?
- **Como** podemos reduzir a taxa de churn?

## 📊 Dados

### Estrutura do Dataset
- **Total de registros**: 200 clientes
- **Colunas analisadas**:
  - `tipo_contrato`: Mensal, Trimestral ou Anual
  - `ligacoes_suporte`: Número de vezes que o cliente ligou para o suporte
  - `dias_atraso`: Dias de atraso no pagamento
  - `cancelou`: Variável alvo (0 = Ativo, 1 = Cancelou)

### Taxa de Cancelamento
- **Geral**: ~60% dos clientes cancelaram
- **Com baixo suporte (< 3 ligações)**: ~57% de cancelamento

## 🔍 Principais Insights

1. **Tipo de Contrato é crítico**
   - Contratos mensais têm taxa de cancelamento muito mais alta
   - Contratos anuais/trimestrais apresentam maior retenção

2. **Múltiplas Ligações para Suporte indicam problemas não resolvidos**
   - Clientes que ligam frequentemente tendem a cancelar
   - Sinal de insatisfação persistente

3. **Atraso no Pagamento é indicador de stress financeiro**
   - Clientes com atraso > 15 dias mostram maior propensão ao cancelamento
   - Oportunidade para intervenção precoce

## 🛠️ Como Usar

### Pré-requisitos
- Python 3.8+
- pip (gerenciador de pacotes Python)

### Instalação

1. Clone o repositório:
```bash
git clone <seu-repositorio>
cd "Laboratório de análise de dados de PMES"
```

2. Instale as dependências:
```bash
pip install pandas matplotlib
```

### Executar a Análise

**Gerar dados de teste:**
```bash
python dados_cancelamento_pme
```

Isso criará um arquivo `dados_cancelamento_pme.csv` com 200 registros simulados.

**Executar análise e gráficos:**
```bash
python analise_de_dados
```

Isso irá:
- Carregar os dados
- Exibir estatísticas de cancelamento
- Gerar gráficos interativos comparando variáveis vs. cancelamento
- Mostrar análise segmentada por tipo de contrato e suporte

## 📁 Estrutura do Projeto

```
Laboratório de análise de dados de PMES/
├── dados_cancelamento_pme          # Script para gerar dados de teste
├── analise_de_dados                # Script principal de análise
├── dados_cancelamento_pme.csv      # Dataset gerado (criado na primeira execução)
└── README.md                       # Este arquivo
```

## 📈 Gráficos Gerados

1. **Histograma: Tipo de Contrato vs Cancelamento**
   - Mostra distribuição de cancelamentos por tipo de contrato

2. **Histograma: Ligações de Suporte vs Cancelamento**
   - Correlação entre número de ligações e cancelamento

3. **Histograma: Dias de Atraso vs Cancelamento**
   - Impacto do atraso no pagamento

4. **Pie Chart: Resumo Geral**
   - Proporção de clientes ativos vs. cancelados

## 💡 Recomendações

Baseado na análise, recomendo:

1. **Incentive contratos anuais/trimestrais**
   - Ofereça desconto significativo vs. plano mensal
   - Aumenta compromisso do cliente

2. **Melhore qualidade do suporte**
   - Objetivo: resolver problemas em máximo 3 ligações
   - Treinar equipe para identificar raiz do problema

3. **Implemente programa de prevenção de atrasos**
   - Intervir antes que atinja 15 dias
   - Oferecer planos de pagamento alternativos

4. **Acompanhamento proativo**
   - Clientes com 4+ ligações precisam de atenção especial
   - Oferecer account manager ou suporte premium

## 🔧 Tecnologias Utilizadas

- **Python 3**: Linguagem base
- **Pandas**: Manipulação e análise de dados
- **Matplotlib**: Visualização de dados
- **Random**: Geração de dados simulados

## 📝 Metodologia

1. **Coleta de Dados**: Simulação de base de clientes realista
2. **Limpeza**: Remoção de dados faltantes
3. **Exploração**: Estatísticas descritivas
4. **Visualização**: Gráficos comparativos
5. **Análise**: Identificação de padrões e correlações
6. **Recomendações**: Sugestões acionáveis baseadas em insights

**Desenvolvido como parte do laboratório de análise de dados para PMEs**
