# Guia Técnico

## Descrição dos Scripts

### 1. `dados_cancelamento_pme` (Gerador de Dados)

**Função**: Simula uma base realista de clientes com dados de cancelamento

**O que faz**:
- Cria 200 registros de clientes
- Gera IDs únicos (1000-1199)
- Simula tipos de contrato aleatórios (Mensal/Trimestral/Anual)
- Gera número variável de ligações de suporte (0-8)
- Simula dias de atraso no pagamento (0-30)
- Define cancelamento baseado em lógica comportamental

**Lógica de Cancelamento**:
```
SE tipo_contrato == 'Mensal' E ligacoes_suporte > 4:
    cancelou = 1
SENÃO SE dias_atraso > 15:
    cancelou = 1
SENÃO:
    cancelou = 0
```

**Saída**: Arquivo CSV com estrutura:
```
id_cliente,tipo_contrato,ligacoes_suporte,dias_atraso,cancelou
1000,trimestral,2,5,0
1001,mensal,5,3,1
...
```

### 2. `analise_de_dados` (Análise Principal)

**Função**: Explorar dados e gerar visualizações

**Etapas**:

#### Fase 1: Preparação
- Carrega dados do CSV
- Remove coluna de ID (sem valor preditivo)
- Remove linhas com valores vazios

#### Fase 2: Exploração
- Calcula taxa geral de cancelamento (count e percentual)
- Exibe estatísticas descritivas

#### Fase 3: Visualização
- Gera 3 histogramas comparando cada variável vs. cancelamento
- Gera 1 pie chart com resumo geral
- Usa cores: Azul (Ativo) e Laranja (Cancelou)

#### Fase 4: Análise Segmentada
- Filtra clientes com baixo suporte (< 3 ligações)
- Compara taxa de cancelamento neste segmento

**Saída**: 
- Gráficos exibidos em janelas do Matplotlib
- Impressão de estatísticas no console

## Fluxo de Execução

```
1. Executar dados_cancelamento_pme
   ↓
   Cria: dados_cancelamento_pme.csv
   
2. Executar analise_de_dados
   ↓
   Lê: dados_cancelamento_pme.csv
   ↓
   Calcula: Estatísticas
   ↓
   Exibe: 4 Gráficos
   ↓
   Imprime: Análise segmentada
```

## Estrutura de Dados

### Input (CSV)

| Coluna | Tipo | Descrição | Exemplos |
|--------|------|-----------|----------|
| id_cliente | int | ID único do cliente | 1000-1199 |
| tipo_contrato | string | Tipo de contrato | 'mensal', 'trimestral', 'anual' |
| ligacoes_suporte | int | Número de ligações | 0-8 |
| dias_atraso | int | Dias de atraso | 0-30 |
| cancelou | int | Target (0/1) | 0=Ativo, 1=Cancelou |

### Output (Análise)

```
Taxa de cancelamento identificada:
cancelou
1    0.605  (60.5%)
0    0.395  (39.5%)

Taxa com baixo suporte:
cancelou
1    0.574  (57.4%)
0    0.426  (42.6%)
```

## Interpretação dos Gráficos

### Histograma de Tipo de Contrato
- Eixo X: Categoria (Mensal/Trimestral/Anual)
- Eixo Y: Quantidade de clientes
- Barras Azuis: Clientes ativos
- Barras Laranja: Clientes cancelados

**Leitura**: Se a barra laranja é muito mais alta para "Mensal", indica forte correlação.

### Histograma de Ligações de Suporte
- Eixo X: Número de ligações (0-8)
- Eixo Y: Quantidade de clientes
- Padrão esperado: Barra laranja cresce conforme aumentam ligações

### Histograma de Dias de Atraso
- Eixo X: Dias (0-30)
- Eixo Y: Quantidade
- Padrão esperado: Proporção de laranja aumenta com dias de atraso

### Pie Chart de Resumo
- Mostra proporção visual (60.5% vs 39.5%)
- Facilita comunicação com stakeholders

## Extensões Possíveis

1. **Integração com banco de dados**
   - Ler dados de banco em vez de CSV

2. **Machine Learning**
   - Treinar modelo de previsão de cancelamento
   - Usar features para calcular score de risco

3. **Dashboard interativo**
   - Usar Plotly/Dash para interface web
   - Filtros dinâmicos por período, contrato, etc.

4. **Análise Temporal**
   - Adicionar coluna de data
   - Analisar evolução de churn ao longo do tempo

5. **Segmentação**
   - Agrupar clientes por perfil
   - Análise por cohort

## Performance

- **Tempo de execução**: ~2-5 segundos
- **Memória necessária**: ~50 MB
- **Escalabilidade**: Funciona bem com até 1 milhão de registros
