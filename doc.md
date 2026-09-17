1. Estrutura Completa de Pastas e Arquivos

erp-petrolina/
├── docker-compose.yml              # Serviços auxiliares (Postgres e Redis)
├── .gitignore                      # Arquivos ignorados pelo controle de versão
│
└── backend/                        # Núcleo da API REST
    ├── manage.py                   # Utilitário de linha de comando do Django
    ├── requirements.txt            # Dependências Python fixadas
    ├── .env                        # Chaves de acesso e variáveis de ambiente
    │
    ├── config/                     # Módulo central de orquestração do Django
    │   ├── __init__.py
    │   ├── asgi.py
    │   ├── wsgi.py
    │   ├── urls.py                 # Roteador central de endpoints HTTP
    │   └── settings.py             # Configurações de banco, middlewares e apps
    │
    ├── empresas/                   # Domínio: Empresas, Filiais e Enquadramento Fiscal
    │   ├── migrations/
    │   │   └── __init__.py
    │   ├── __init__.py
    │   ├── admin.py
    │   ├── apps.py
    │   ├── models.py               # Tabelas: Empresa (MEI, Simples, Produtor Rural)
    │   ├── serializers.py          # Validação e serialização de dados (JSON)
    │   ├── views.py                # Endpoints REST (ViewSets)
    │   └── urls.py                 # Rotas específicas de empresas
    │
    ├── produtos/                   # Domínio: Itens, Códigos de Barras, Preços e NCM
    │   ├── migrations/
    │   │   └── __init__.py
    │   ├── __init__.py
    │   ├── admin.py
    │   ├── apps.py
    │   ├── models.py               # Tabelas: Produto, Unidades, Dados Fiscais
    │   ├── serializers.py
    │   ├── views.py
    │   └── urls.py
    │
    ├── estoque/                    # Domínio: Inventário Físico e Auditoria (Ledger)
    │   ├── migrations/
    │   │   └── __init__.py
    │   ├── __init__.py
    │   ├── admin.py
    │   ├── apps.py
    │   ├── models.py               # Tabela: MovimentoEstoque (imutável)
    │   ├── services.py             # Lógica de cálculo atômico com bloqueio de linha
    │   ├── serializers.py
    │   ├── views.py
    │   └── urls.py
    │
    └── vendas/                     # Domínio: Orçamentos, Condicionais e Vendas Gerenciais
        ├── migrations/
        │   └── __init__.py
        ├── __init__.py
        ├── admin.py
        ├── apps.py
        ├── models.py               # Tabelas: PedidoVenda, ItemPedido
        ├── serializers.py
        ├── views.py
        └── urls.py

Passo 1: Criação da Pasta Raiz e Configuração do Banco Local
Crie o arquivo docker-compose.yml na raiz:

Passo 2: Inicialização do Backend e Instalação de Dependências
