# Análise de Dados com Python & PostgreSQL - Controladoria

Projeto avaliativo do Módulo 2 - Análise de Dados com Python e PostgreSQL.

##  Contexto do Problema
A Controladoria identificou gargalos nas compras públicas federais: indícios de sobrepreço, concentração de contratos em poucos fornecedores, morosidade nos certames e baixa adesão competitiva. O objetivo deste projeto é construir uma esteira analítica ponta a ponta (End-to-End) para transformar dados brutos do PNCP em um ambiente analítico confiável, auditável e executivo.

##  Tecnologias Utilizadas
- **Python (Pandas):** Limpeza, tratamento e montagem das tabelas.
- **PostgreSQL:** Modelagem dimensional (Star Schema) e carga dos dados.
- **Power BI (DAX):** Criação de dashboard executivo e medidas analíticas.
- **Git/GitHub:** Versionamento de código.

##  Dicionário de Inconsistências Tratadas
Durante a limpeza (src/limpeza.py), os seguintes problemas foram resolvidos:
- **CNPJ/CPF:** Remoção de máscaras e restauração de zeros à esquerda.
- **Valores Monetários:** Conversão de textos como "R$ 1.234,56" para float, tratamento de negativos entre parênteses e separadores.
- **Datas:** Padronização de múltiplos formatos e anulação de homologações anteriores à publicação.
- **Nulos Disfarçados:** Substituição de "N/A", "NULL", "-", "SEM INFORMAÇÃO" por valores nulos reais.
- **Encoding:** Correção de caracteres corrompidos (Latin-1/UTF-8).

##  Modelagem Dimensional (Star Schema)
O banco foi estruturado com 1 tabela Fato e 4 Dimensões:
- **Fato:** `fato_item_contratado` (6.126 linhas)
- **Dimensões:** `dim_orgao` (363), `dim_fornecedor` (2.652), `dim_modalidade` (7), `dim_localidade` (27).

*(Insira aqui um print do seu modelo no Power BI ou do banco no pgAdmin)*

##  Instruções de Execução
Para reproduzir o projeto do zero, siga os passos:
1. Clone o repositório.
2. Instale as dependências: `pip install pandas psycopg2-binary`
3. Execute a limpeza: `python -m src.limpeza`
4. Monte as tabelas: `python -m src.montar_tabelas`
5. Crie o banco e carregue os dados: `python -m src.carregar` (certifique-se de que o PostgreSQL está rodando).
6. Abra o arquivo `powerbi/projeto.pbix` no Power BI Desktop.

##  Planejamento em Sprints
O projeto foi dividido em 7 Sprints (0 a 6):
- **Sprint 0:** Entendimento dos dados.
- **Sprint 1:** Auditoria dos problemas.
- **Sprint 2:** Limpeza (src/limpeza.py).
- **Sprint 3:** Montagem da Fato e Dimensões.
- **Sprint 4:** Criação do Banco e Carga.
- **Sprint 5:** Consultas SQL (02_perguntas.sql).
- **Sprint 6:** Dashboard Power BI (15 medidas DAX e 6 páginas).

![Sprints do projeto](docs/img/sprints.png)

## Link do Vídeo
[Clique aqui para assistir à apresentação do projeto](EM_BREVE)

##  Melhorias Futuras
- Automatizar a ingestão dos dados via API do PNCP.
- Incluir análise de séries temporais para prever gastos.
- Criar alertas automáticos para itens com sobrepreço.
