# Currency Converter Microservice

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

Endpoints
GET /converter/{from_currency}
Converte o valor de uma moeda para várias outras. A conversão é feita de forma síncrona.

Parâmetros de caminho:

from_currency: Código de três letras da moeda de origem (ex: “USD”).
Parâmetros de query:

to_currencies: Lista separada por vírgula de códigos de três letras das moedas de destino (ex: “EUR,GBP”).
price: Valor a ser convertido (ex: 5.55).
Exemplo de requisição:

GET /converter/USD?to_currencies=EUR,GBP&price=100.00

Exemplo de resposta:

JSON

[
  95.25,
  85.75
]

GET /converter/async/{from_currency}
Converte o valor de uma moeda para várias outras de forma assíncrona.

Parâmetros de caminho:

from_currency: Código de três letras da moeda de origem.
Parâmetros de query:

to_currencies: Lista separada por vírgula de códigos de três letras das moedas de destino.
price: Valor a ser convertido.
Exemplo de requisição:

GET /converter/async/USD?to_currencies=EUR,GBP&price=100.00

Exemplo de resposta:

JSON

[
  {"EUR": 95.25},
  {"GBP": 85.75}
]
POST /converter/async/v2/{from_currency}
Converte o valor de uma moeda para várias outras de forma assíncrona, utilizando um corpo JSON para os dados de entrada.

Parâmetros de caminho:

from_currency: Código de três letras da moeda de origem.
Corpo da requisição:

JSON
{
  "price": 100.00,
  "to_currencies": ["EUR", "GBP"]
}

Exemplo de requisição:

POST /converter/async/v2/USD
Content-Type: application/json

{
  "price": 100.00,
  "to_currencies": ["EUR", "GBP"]
}

Exemplo de resposta:

JSON

{
  "message": "success",
  "data": [
    {"EUR": 95.25},
    {"GBP": 85.75}
  ]
}
Estrutura do Projeto
main.py: Ponto de entrada do aplicativo FastAPI.
converter.py: Funções de conversão síncronas e assíncronas utilizando a API da Alpha Vantage.
routers.py: Definições das rotas do FastAPI.
schemas.py: Definições dos modelos de entrada e saída usando Pydantic.
Tecnologias Utilizadas
FastAPI: Framework de alto desempenho para construir APIs web com Python.
Requests: Biblioteca HTTP para requisições síncronas.
Aiohttp: Biblioteca HTTP assíncrona.
Alpha Vantage API: API para obter taxas de câmbio em tempo real.

Notas
Certifique-se de que sua chave de API da Alpha Vantage esteja corretamente configurada como uma variável de ambiente.
O serviço oferece suporte para conversões síncronas e assíncronas.