# Desafio de programção

Criar uma [API Rest](https://pt.wikipedia.org/wiki/REST) para gerenciamento de Pokemon.

## Pré-requisitos

* Usar o [Node.js](https://nodejs.org/en/) para construção da API.
* Usar o [Express](https://expressjs.com/pt-br/) para construção das rotas.

## Rotas

A API deverá fornecer as seguintes rotas:

### POST /pokemon: Criar um novo Pokémon

#### Especificações

* Requisição
  * Método: `POST`
  * Rota: `/pokemon`
  * Corpo: Objeto JSON com os dados do Pokémon
* Resposta
  * _Status_: 200
  * Corpo: Objeto JSON com os dados do Pokémon inserido

#### Corpo da requisição

Objeto do tipo JSON com os dados do Pokémon. Exemplo:

```json
{
  "number": 47,
  "name": "Parasect",
  "photo": "https://cdn.bulbagarden.net/upload/thumb/8/80/047Parasect.png/250px-047Parasect.png",
  "types": ["Bug", "Grass"]
}
```

#### Corpo da resposta

O objeto de saída deve ser igual ao objeto de entrada:

```json
{
  "number": 47,
  "name": "Parasect",
  "photo": "https://cdn.bulbagarden.net/upload/thumb/8/80/047Parasect.png/250px-047Parasect.png",
  "types": ["Bug", "Grass"]
}
```

### GET /pokemon/{{number}}: Obter um Pokémon

* Requisição
  * Método: `GET`
  * Rota: `/pokemon/{{number}}`
  * Corpo: _Vazio_
* Resposta
  * Quando o Pokémon foi encontrado
    * _Status_: 200
    * Corpo: Objeto JSON com os dados do Pokémon encontrado
  * Quando o Pokémon não foi encontrado
    * _Status_: 404
    * Corpo: Objeto de erro

A variável `{{number}}` representa o número do Pokémon que deseja-se procurar. Exemplo: `/pokemon/47`.

#### Corpo da resposta (200)

O objeto de saída deve ser o Pokémon encontrado. Por exemplo, ao procurar o Pokémon 47, deve retornar o seguinte objeto:

```json
{
  "number": 47,
  "name": "Parasect",
  "photo": "https://cdn.bulbagarden.net/upload/thumb/8/80/047Parasect.png/250px-047Parasect.png",
  "types": ["Bug", "Grass"]
}
```

#### Corpo da resposta (404)

Caso o Pokémon procurado não exista, deves-se retornar o seguinte corpo como resposta da requisição.

```json
{
  "statusCode": 404,
  "message": "Pokémon not found",
  "error": "Not Found"
}
```

### GET /pokemon: Listar todos os Pokémon

* Requisição
  * Método: `GET`
  * Rota: `/pokemon`
  * Corpo: _Vazio_
* Resposta
  * _Status_: 200
  * Corpo: Vetor com a lista de Pokémon encontrado

#### Corpo da resposta

Deve retornar um vetor com a lista de todos os Pokémon criados anteriormente. Exemplo:

```json
[
 {
   "number": 47,
   "name": "Parasect",
   "photo": "https://cdn.bulbagarden.net/upload/thumb/8/80/047Parasect.png/250px-047Parasect.png",
   "types": ["Bug", "Grass"]
 },
 {
  "number": 105,
  "name": "Marowak",
  "photo": "https://cdn.bulbagarden.net/upload/thumb/9/98/105Marowak.png/250px-105Marowak.png",
  "types": ["Ground"]
 },
 {
  "number": 123,
  "name": "Scyther",
  "photo": "https://cdn.bulbagarden.net/upload/thumb/b/ba/123Scyther.png/250px-123Scyther.png",
  "types": ["Bug", "Flying"]
 }
]
```

### DELETE /pokemon/{{number}}: Excluir um Pokémon

* Requisição
  * Método: `DELETE`
  * Rota: `/pokemon/{{number}}`
  * Corpo: _Vazio_
* Resposta
  * Quando o Pokémon for encontrado
    * _Status_: 200
    * Corpo: Objeto Pokémon que foi excluído
  * Quando o Pokémon não foi encontrado
    * _Status_: 404
    * Corpo: Objeto de erro

A variável `{{number}}` representa o número do Pokémon que deve ser excluído. Exemplo: `/pokemon/47`.

#### Corpo da resposta (200)

O objeto de saída deve ser o Pokémon excluído. Por exemplo, ao excluir o Pokémon 47, deve retornar o seguinte objeto:

```json
{
  "number": 47,
  "name": "Parasect",
  "photo": "https://cdn.bulbagarden.net/upload/thumb/8/80/047Parasect.png/250px-047Parasect.png",
  "types": ["Bug", "Grass"]
}
```

#### Corpo da resposta (404)

Caso o Pokémon que deseja-se excluir não exista, deves-se retornar o seguinte corpo como resposta da requisição.

```json
{
  "statusCode": 404,
  "message": "Pokémon not found",
  "error": "Not Found"
}
```

## Armazenamento

Os Pokémon criados deverão ser armazenados em um arquivo denominado `pokemon.json`, que deverá ser criado na pasta raiz do projeto. Inicialmente, o conteúdo desse arquivo deve ser um vetor vazio:

```json
[]
```

Quando um Pokémon é criado ou excluído, esse arquivo deverá ser atualizado.

## Entrega

O projeto deve ser entregue via e-mail em um arquivo no formato `.zip`. O conteúdo do arquivo deve ser um pasta, dentro da qual deve-se encontrar:

* Fontes do projeto.
* Arquivo `packages.json`.
* Arquivo `pokemon.json`.
* Outros arquivos necessários para o funcionamento do projeto.

**Observação**: Excluir a pasta `node_modules` antes de enviar o projeto.

## Fontes de pesquisa

* [Configurando o Node como ambiente de desenvolvimento](https://developer.mozilla.org/pt-BR/docs/Learn/Server-side/Express_Nodejs/ambiente_de_desenvolvimento)
* [Express - Instalação](https://expressjs.com/pt-br/starter/installing.html)
* [Começando uma API REST com Node.JS](https://ezdevs.com.br/comecando-uma-api-rest-com-node-js/)
* [Criando uma API RESTful com NodeJS e Express](https://medium.com/xp-inc/https-medium-com-tiago-jlima-developer-criando-uma-api-restful-com-nodejs-e-express-9cc1a2c9d4d8)
* [API HTTP + REST – Conceito e exemplo em Node.js](https://imasters.com.br/back-end/api-http-rest-conceito-e-exemplo-em-node-js)
* [Reading and Writing JSON Files with Node.js](https://stackabuse.com/reading-and-writing-json-files-with-node-js/)
* [Read/Write JSON Files with Node.js](https://medium.com/@osiolabs/read-write-json-files-with-node-js-92d03cc82824)
