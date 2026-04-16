# Sistema CLI de Monitoramento da Cultura do Tomate

## 1) Problema tratado

Este projeto simula um sistema de apoio à decisão para o agronegócio, focado na cultura do tomate.
A proposta é monitorar **temperatura** e **umidade relativa do ar** para apoiar o controle de pragas e doenças,
principalmente riscos ligados a fungos.

### Regras de negócio implementadas

- **Umidade baixa** gera riscos de:
  - Paralisação do crescimento
  - Murcha e transpiração excessiva
  - Aumento de pragas (mosca-branca e pulgão)
- **Umidade alta** gera riscos de:
  - Doenças fúngicas e bacterianas (requeima, pinta-preta)
  - Podridão apical (fundo preto)
  - Rachaduras
  - Queda de flores
  - Raízes sufocadas
- **Alerta de fungo**:
  - Se houver condição de fungo (umidade alta), o sistema exige verificação visual.
  - Se o fungo for confirmado, recomenda: **"Aplicação do Fungicida X via pulverização"**.

## 2) Inovação da solução

A inovação é combinar, em um único fluxo CLI:

- Análise imediata de risco ambiental (temperatura + umidade)
- Protocolo operacional de campo (checagem visual guiada)
- Recomendação de ação padronizada para tomada de decisão rápida
- Persistência híbrida:
  - memória local (lista de dicionários)
  - exportação em JSON
  - CRUD em Oracle para histórico institucional

Isso facilita rastreabilidade, padronização da resposta agronômica e suporte acadêmico para os capítulos de algoritmos, estruturas de dados, arquivos e banco relacional.

## 3) Requisitos técnicos atendidos

- **Cap 3 (Subalgoritmos)**:
  - Sistema totalmente modularizado em funções/procedimentos com tipagem explícita.
- **Cap 4 (Estruturas de Dados)**:
  - Tuplas para dados imutáveis (problemas de umidade e sinais visuais de fungo)
  - Dicionários para registro de monitoramento
  - Lista dinâmica de dicionários como tabela de memória
- **Cap 5 (Arquivos)**:
  - `with open` para exportação JSON
  - `with open` para log TXT (`operacoes.log`)
- **Cap 6 (Oracle)**:
  - Biblioteca `oracledb`
  - Conexão com `try...except`
  - CRUD com `cursor()`, `execute()` e `commit()`
  - DDL comentado no topo de `main.py`
- **Consistência de dados**:
  - Validação de entradas numéricas com `while` + `try...except ValueError`

## 4) Estrutura esperada

- `main.py` -> codigo principal CLI
- `README.md` -> este documento
- `monitoramentos.json` -> gerado na exportação
- `operacoes.log` -> log TXT de operações

## 5) Como executar

## 5.1 Pre-requisitos

- Python 3.10+
- Oracle Database acessível (local ou remoto)
- Biblioteca Oracle para Python:

```bash
pip install oracledb
```

## 5.2 Criar tabela no Oracle

No início de `main.py` existe o script DDL comentado.
Execute esse DDL no seu schema Oracle antes de usar o CRUD.

## 5.3 Rodar aplicação

No terminal, dentro da pasta do projeto:

```bash
python main.py
```

## 6) Fluxo de uso

1. Registrar monitoramento (temperatura e umidade).
2. Ver a classificação e riscos.
3. Se umidade alta, realizar verificação visual de fungo.
4. Receber recomendação automática.
5. Opcionalmente:
   - Exportar tabela local para JSON
   - Usar menu Oracle para CRUD

## 7) Observações importantes

- A opção de inserção no Oracle utiliza o **último monitoramento local** registrado.
- O arquivo de log (`operacoes.log`) registra eventos principais do sistema.
- Este projeto é didático/acadêmico e pode ser expandido com sensores reais, dashboard web e alertas automatizados.
