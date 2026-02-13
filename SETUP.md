# Configuração do Ambiente

Para reproduzir este projeto, você precisa de:

## Requisitos do Sistema
- Python 3.8 ou superior
- pip (gerenciador de pacotes)
- ~100 MB de espaço em disco

## Dependências

### Instalação via pip

```bash
pip install pandas==2.0.3
pip install matplotlib==3.7.2
```

### Arquivo requirements.txt

Alternativamente, instale todas as dependências de uma vez:

```bash
pip install -r requirements.txt
```

## Versões Testadas

- Python 3.10+
- Pandas 2.0+
- Matplotlib 3.7+

## Troubleshooting

### Erro: "No module named 'pandas'"
```bash
pip install --upgrade pandas
```

### Erro: "No module named 'matplotlib'"
```bash
pip install --upgrade matplotlib
```

### Resolvendo problemas de caminho
Se os scripts não encontram `dados_cancelamento_pme.csv`:
1. Certifique-se de executar `python dados_cancelamento_pme` primeiro
2. Verifique se ambos os arquivos estão no mesmo diretório
3. Verifique as permissões de escrita da pasta
