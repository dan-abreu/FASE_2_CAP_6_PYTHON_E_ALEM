# Sistema CLI de Monitoramento da Cultura do Tomate

## 1) Problema tratado

Este projeto simula um sistema de apoio a decisao para o agronegocio, focado na cultura do tomate.
A proposta e monitorar **temperatura** e **umidade relativa do ar** para apoiar o controle de pragas e doencas,
principalmente riscos ligados a fungos.

### Regras de negocio implementadas

- **Umidade baixa** gera riscos de:
  - Paralisacao do crescimento
  - Murcha e transpiracao excessiva
  - Aumento de pragas (mosca-branca e pulgao)
- **Umidade alta** gera riscos de:
  - Doencas fungicas e bacterianas (requeima, pinta-preta)
  - Podridao apical (fundo preto)
  - Rachaduras
  - Queda de flores
  - Raizes sufocadas
- **Alerta de fungo**:
  - Se houver condicao de fungo (umidade alta), o sistema exige verificacao visual.
  - Se o fungo for confirmado, recomenda: **"Aplicacao do Fungicida X via pulverizacao"**.

## 2) Inovacao da solucao

A inovacao e combinar, em um unico fluxo CLI:

- Analise imediata de risco ambiental (temperatura + umidade)
- Protocolo operacional de campo (checagem visual guiada)
- Recomendacao de acao padronizada para tomada de decisao rapida
- Persistencia hibrida:
  - memoria local (lista de dicionarios)
  - exportacao em JSON
  - CRUD em Oracle para historico institucional

Isso facilita rastreabilidade, padronizacao da resposta agronomica e suporte academico para os capitulos de algoritmos, estruturas de dados, arquivos e banco relacional.

## 3) Requisitos tecnicos atendidos

- **Cap 3 (Subalgoritmos)**:
  - Sistema totalmente modularizado em funcoes/procedimentos com tipagem explicita.
- **Cap 4 (Estruturas de Dados)**:
  - Tuplas para dados imutaveis (problemas de umidade e sinais visuais de fungo)
  - Dicionarios para registro de monitoramento
  - Lista dinamica de dicionarios como tabela de memoria
- **Cap 5 (Arquivos)**:
  - `with open` para exportacao JSON
  - `with open` para log TXT (`operacoes.log`)
- **Cap 6 (Oracle)**:
  - Biblioteca `oracledb`
  - Conexao com `try...except`
  - CRUD com `cursor()`, `execute()` e `commit()`
  - DDL comentado no topo de `main.py`
- **Consistencia de dados**:
  - Validacao de entradas numericas com `while` + `try...except ValueError`

## 4) Estrutura esperada

- `main.py` -> codigo principal CLI
- `README.md` -> este documento
- `monitoramentos.json` -> gerado na exportacao
- `operacoes.log` -> log TXT de operacoes

## 5) Como executar

## 5.1 Pre-requisitos

- Python 3.10+
- Oracle Database acessivel (local ou remoto)
- Biblioteca Oracle para Python:

```bash
pip install oracledb
```

## 5.2 Criar tabela no Oracle

No inicio de `main.py` existe o script DDL comentado.
Execute esse DDL no seu schema Oracle antes de usar o CRUD.

## 5.3 Rodar aplicacao

No terminal, dentro da pasta do projeto:

```bash
python main.py
```

## 6) Fluxo de uso

1. Registrar monitoramento (temperatura e umidade).
2. Ver a classificacao e riscos.
3. Se umidade alta, realizar verificacao visual de fungo.
4. Receber recomendacao automatica.
5. Opcionalmente:
   - Exportar tabela local para JSON
   - Usar menu Oracle para CRUD

## 7) Observacoes importantes

- A opcao de insercao no Oracle utiliza o **ultimo monitoramento local** registrado.
- O arquivo de log (`operacoes.log`) registra eventos principais do sistema.
- Este projeto e didatico/academico e pode ser expandido com sensores reais, dashboard web e alertas automatizados.
