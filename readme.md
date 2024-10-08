# Micro Serviço de Conversão Cambial

Este microserviço permite converter valores de uma moeda para outra usando a API da Alpha Vantage. Ele fornece suporte para conversões síncronas e assíncronas.

## Requisitos
- Python 3.11+
- Poetry para gerenciamento de dependências

## Instalação
Clone o repositório:

- git clone <URL_DO_REPOSITORIO>

## Navegue até o diretório do projeto:

- cd MsConversaoMoedas

# Instale as dependências usando o Poetry:

- poetry install

# Ative o ambiente virtual do Poetry:

- poetry shell

# Defina a variável de ambiente ALPHAVANTAGE_APIKEY com sua chave de API da Alpha Vantage:

- export ALPHAVANTAGE_APIKEY=<SUA_CHAVE_DE_API>

# Executando o serviço
# Inicie o servidor FastAPI:

> uvicorn main:app --reload

> O serviço estará disponível em localhost:8000
## Você pode acessar uma documentação e saber mais sobre as requisições acessando a rota /docs
- http://localhost:8000/docs
  

Notas
Certifique-se de que sua chave de API da Alpha Vantage esteja corretamente configurada como uma variável de ambiente.
O serviço oferece suporte para conversões síncronas e assíncronas.
