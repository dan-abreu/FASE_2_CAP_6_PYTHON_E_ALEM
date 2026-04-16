# AgroVision IA - Sistema de Monitorização da Cultura do Tomate

## 1. Problema e Contexto (Agronegócio)
Este projeto aborda um dos grandes desafios na horticultura moderna: a gestão de riscos fitossanitários baseada em dados ambientais. Focamos na cultura do tomate, uma das mais sensíveis a variações de temperatura e humidade.

O AgroVision IA atua na detecção precoce de condições favoráveis ao aparecimento de fungos (como a requeima e a pinta-preta) e problemas fisiológicos. O sistema não apenas regista dados, mas orienta o produtor através de protocolos de decisão, sugerindo inspeções visuais e ações preventivas diretas em campo.

## 2. Inovação e Diferencial
A solução diferencia-se pela sua abordagem de apoio à decisão assistida:
* Protocolo de Verificação: Ao detetar humidade crítica, o sistema apresenta sinais visuais específicos (como manchas ou lesões) que o produtor deve procurar antes de confirmar uma aplicação química.
* Interação em Tempo Real: Fornece recomendações imediatas no prompt de comando para correção de irrigação ou pulverização.
* Gestão de Dados Robusta: Combina a agilidade da memória local e ficheiros JSON com a segurança institucional de um banco de dados Oracle.

## 3. Requisitos Técnicos Implementados
O sistema foi desenvolvido seguindo rigorosamente os padrões de engenharia de software estudados nos capítulos 3 a 6:

* Cap 3 (Subalgoritmos): Modularização completa do código. Todas as ações (cálculo de risco, conexão ao banco, logs) estão encapsuladas em funções com parâmetros e retornos definidos.
* Cap 4 (Estruturas de Dados):
  - Listas: Utilizadas como tabela de memória dinâmica para gerir os registos durante a execução.
  - Dicionários: Estrutura base para cada registo de monitorização, facilitando o acesso às chaves de dados.
  - Tuplas: Armazenamento de constantes de negócio (mensagens de erro e sinais de fungo) que não devem ser alteradas.
* Cap 5 (Manipulação de Arquivos):
  - Persistência em JSON para exportação de relatórios.
  - Geração de ficheiro de Log (TXT) para auditoria de todas as operações realizadas no sistema.
* Cap 6 (Banco de Dados Oracle): Integração completa com Oracle Database através da biblioteca "oracledb", implementando o ciclo CRUD (Create, Read, Update, Delete) para gestão histórica.

## 4. Estrutura do Repositório
* main.py: Script principal contendo toda a lógica do sistema.
* README.txt: Documentação detalhada da solução (este ficheiro).
* operacoes.log: Registo de eventos do sistema (gerado automaticamente).
* monitoramentos.json: Dados exportados para integração (gerado opcionalmente).

## 5. Como Executar
1. Pré-requisitos: Certifique-se de ter o Python 3.10+ instalado e a biblioteca do Oracle. No terminal, execute:
   pip install oracledb

2. Execução:
   python main.py

3. Fluxo: Utilize o menu numérico para registar novas leituras, consultar o histórico local ou gerir os dados no banco Oracle.

---