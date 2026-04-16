# Atividade Fase 2 - Sistema de Monitoramento da Cultura do Tomate

## 1. O Problema (Agronegócio)
Para esta atividade, escolhemos focar no controle de pragas e doenças na agricultura, especificamente na cultura do tomate. O tomateiro é muito sensível às variações de temperatura e umidade, o que facilita a proliferação de fungos.

Nosso sistema simula a coleta desses dados climáticos para ajudar o produtor a tomar decisões mais rápidas. Se a umidade estiver muito alta, o programa alerta sobre o risco de fungos, pede uma checagem visual e sugere o tratamento adequado.

## 2. Conteúdos Aplicados (Capítulos 3 ao 6)
O projeto foi desenvolvido para atender aos requisitos técnicos da disciplina, aplicando os seguintes conceitos:

* Subalgoritmos (Cap 3): Todo o sistema foi modularizado. Criamos funções com passagem de parâmetros para separar as regras de negócio (como classificar a umidade) e as operações de banco de dados.
* Estruturas de Dados (Cap 4): 
  - Usamos Tuplas para guardar dados que não mudam (como as listas de doenças).
  - Usamos Dicionários para montar a estrutura de cada registro de leitura.
  - Usamos uma Lista como "Tabela de Memória" para ir guardando os dicionários enquanto o programa roda.
* Manipulação de Arquivos (Cap 5): O sistema gera um arquivo "operacoes.log" em texto (TXT) para auditar o que acontece no programa. Também criamos uma opção no menu para exportar a tabela de memória para um arquivo JSON.
* Banco de Dados Oracle (Cap 6): Usamos a biblioteca oracledb para fazer a conexão. Criamos um menu exclusivo de CRUD, onde é possível dar INSERT (salvando a leitura no banco), SELECT (para listar), UPDATE (para mudar a recomendação) e DELETE.

## 3. Como testar o projeto
1. Primeiro, é necessário ter a biblioteca do banco instalada. No terminal, rode:
   pip install oracledb

2. O script do banco de dados (DDL) para criar a tabela está comentado bem no início do arquivo main.py.

3. Para iniciar o programa, rode:
   python main.py

4. Siga as opções do menu. Recomendamos primeiro "Registrar nova leitura" (Opção 1) e depois usar a Opção 4 para salvar esse dado no banco Oracle.