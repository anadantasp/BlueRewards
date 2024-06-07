# BlueRewards

## Escopo do produto
Leia o escopo do produto [aqui](https://github.com/anadantasp/BlueRewards/blob/main/Documentacao/Escopo%20Produto/Escopo%20do%20Produo%20-%20BlueRewards%20.pdf)

## Vídeo pitch
Acesse [aqui](link)


## Passo a passo de como executar o projeto
Acesse [aqui](https://www.youtube.com/watch?v=IAD5RYQ5E7o) o vídeo mostrando a execução do projeto

Repositório .Net: [BlueRewards.NET](https://github.com/anadantasp/BlueRewards.NET)
Collection Postman: [endpoints](https://github.com/anadantasp/BlueRewards/blob/main/Documentacao/Postman/GlobalSolution%20-%20BlueRewards.postman_collection.json)

# Documentação da API

Esta documentação descreve os endpoints disponíveis na API, incluindo exemplos de requisições e respostas. Todas as requisições, exceto login e cadastro de usuário, requerem um token JWT no cabeçalho de autorização.

## Endpoints

### 1. Pontos de Coleta

#### `GET /pontoscoleta`

Retorna uma lista de pontos de coleta.

**Requer JWT:** Sim

**Resposta:**

```json
[
    {
        "id": "integer",
        "nome": "string",
        "endereco": "string"
    }
]
```

### 2. Registrar Coleta

#### `POST /coletas`

Registra uma nova coleta.

**Requer JWT:** Sim

**Requisição:**

```json
{
    "peso": "number",
    "pontoColeta": {
        "id": "integer"
    }
}
```

**Resposta:**

```json
{
    "id": "integer",
    "peso": "number",
    "pontoColeta": {
        "id": "integer",
        "nome": "string",
        "endereco": "string"
    },
    "usuarioResponse": {
        "id": "integer",
        "nome": "string",
        "email": "string",
        "pontuacao": "integer"
    }
}
```

### 3. Login

#### `POST /login`

Realiza login e retorna o token JWT.

**Requer JWT:** Não

**Requisição:**

```json
{
    "email": "string",
    "senha": "string"
}
```

**Resposta:**

```json
{
    "token": "string",
    "type": "string",
    "prefix": "string"
}
```

### 4. Informações do Usuário

#### `GET /usuario`

Retorna as informações do usuário.

**Requer JWT:** Sim

**Resposta:**

```json
{
    "id": "integer",
    "nome": "string",
    "email": "string",
    "pontuacao": "integer"
}
```

### 5. Atualizar Usuário

#### `PUT /usuario`

Atualiza as informações do usuário.

**Requer JWT:** Sim

**Requisição:**

```json
{
    "nome": "string"
}
```

**Resposta:**

```json
{
    "id": "integer",
    "nome": "string",
    "email": "string",
    "pontuacao": "integer"
}
```

### 6. Atualizar Senha do Usuário

#### `PUT /usuario/password`

Atualiza a senha do usuário.

**Requer JWT:** Sim

**Requisição:**

```json
{
    "senhaAntiga": "string",
    "senha": "string"
}
```

**Resposta:**

```json
{
    "message": "string"
}
```

### 7. Deletar Usuário

#### `DELETE /usuario`

Deleta o usuário.

**Requer JWT:** Sim

### 8. Cadastro de Usuário

#### `POST /usuario`

Cadastra um novo usuário.

**Requer JWT:** Não

**Requisição:**

```json
{
    "nome": "string",
    "email": "string",
    "senha": "string"
}
```

**Resposta:**

```json
{
    "id": "integer",
    "nome": "string",
    "email": "string",
    "pontuacao": "integer"
}
```

### 9. Listar Cupons

#### `GET /cupons`

Retorna uma lista de cupons.

**Requer JWT:** Sim

**Resposta:**

```json
[
    {
        "descricao": "string",
        "codigo": "string",
        "validade": "string",
        "pontuacao": "integer",
        "empresa": {
            "cnpj": "string",
            "nome": "string"
        },
        "disponivel": "boolean",
        "desbloqueado": "boolean"
    }
]
```

### 10. Resgatar Cupom

#### `POST /usuario/cupons`

Resgata um cupom para o usuário.

**Requer JWT:** Sim

**Requisição:**

```json
{
    "descricao": "string",
    "codigo": "string",
    "validade": "string",
    "pontuacao": "integer",
    "empresa": {
        "cnpj": "string",
        "nome": "string"
    },
    "disponivel": "boolean"
}
```

**Resposta:**

```json
{
    "id": "integer",
    "nome": "string",
    "email": "string",
    "pontuacao": "integer",
    "cupons": [
        {
            "id": "integer",
            "codigo": "string",
            "descricao": "string",
            "validade": "string",
            "pontuacao": "integer",
            "empresa": {
                "id": "integer",
                "cnpj": "string",
                "nome": "string"
            }
        }
    ]
}
```

