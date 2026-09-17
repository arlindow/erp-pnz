  ### 1. Visão Geral do Projeto

  O projeto ERP PNZ (também referenciado como ERP Petrolina) encontra-se atualmente em estágio inicial de
  infraestrutura e planejamento arquitetural.
  O repositório ainda não possui o código-fonte da aplicação (backend Django), mas já possui a base de serviços de
  suporte (banco de dados e cache) e a especificação de domínio documentada.
  ──────
  ### 2. Estrutura Atual de Arquivos

   Arquivo                      | Finalidade
  ------------------------------|----------------------------------------------------------------------------------
   docker-compose.yml           | Orquestração dos serviços de infraestrutura local via Docker.
   README.md                    | Manual de instruções para inicialização e verificação do ambiente de containers.
   doc.md                       | Especificação de arquitetura da futura aplicação (backend/).
   .env.example                 | Modelo das variáveis de ambiente para o banco, cache e Django.
   .env                         | Arquivo de ambiente local com as credenciais configuradas.
   .gitignore                   | Regras para evitar versionamento de arquivos sensíveis, virtuais e temporários.
  ──────
  ### 3. Diagnóstico de Infraestrutura e Serviços

  • PostgreSQL (16-Alpine):
      • Container: erp_postgres
      • Porta exposta: 5432
      • Volume persistente: pgdata
      • Status: Ativo e saudável (healthy).
  • Redis (7-Alpine):
      • Container: erp_redis
      • Porta exposta: 6379 com AOF habilitado (--appendonly yes)
      • Volume persistente: redisdata
      • Status: Ativo e saudável (healthy).
  • Versionamento: O diretório ainda não é um repositório Git inicializado (.git não criado).
  ──────
  ### 4. Arquitetura Planejada (conforme doc.md)

  O documento projeta uma aplicação Django REST Framework na pasta backend/ orientada a domínios de negócio com
  características fiscais e regionais:

  1. config/: Módulo central de orquestração do Django (settings.py, urls.py, WSGI/ASGI, integração Celery/Cache).
  2. empresas/: Gestão de empresas, filiais e enquadramentos fiscais (MEI, Simples Nacional, Produtor Rural).
  3. produtos/: Catálogo de itens, unidades de medida, preços, código de barras e dados fiscais (NCM).
  4. estoque/: Auditoria física estilo ledger (MovimentoEstoque imutável) com cálculo atômico e bloqueio de linha
  (row-level lock) para evitar race conditions.
  5. vendas/: Pedidos de venda, orçamentos, vendas condicionais e faturamento.
  ──────
  ### 5. Próximos Passos Naturais (quando desejar iniciar a implementação)

  1. Inicialização do controle de versão: Executar git init para rastrear as mudanças.
  2. Setup do ambiente Python: Criação do ambiente virtual (.venv) e definição do requirements.txt (Django, Django
  REST Framework, psycopg/psycopg2, django-environ, celery, redis).
  3. Scaffolding do Django: Criar o diretório backend/, iniciar o projeto config e gerar as apps descritas
  (empresas, produtos, estoque, vendas).



  