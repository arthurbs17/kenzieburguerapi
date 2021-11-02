# kenzieburguerapi

# Registrar novos usuários e visualizar usuários cadastrados:

## Para registrar novo usuário:

POST/register ou /users

body para requisição:

{
"email": "user@mail.com",
"password": "bestPassw0rd",
"firstname": "New",
"lastname": "User"
}

Resposta:

201 Created
{
"accessToken": "xxx.xxx.xxx"
}

GET/users/userId

Resposta:

status 200

{ "email": "user3@mail.com", "password": "xxxxx", "name": "User", "id": x }

# Fazer login:

## Para realizar o login:

POST/login ou /signin

body para requisição:

{
"email": "user@mail.com",
"password": "bestPassw0rd"
}

Resposta:

200 OK
{
"accessToken": "xxx.xxx.xxx"
}

# Acessar os produtos:

## Para acessar os produtos:

GET/products

Qualquer pessoa poderá acessar os produtos, não será possível adicionar novos produtos.

Resposta:

"products": [
{
"id": 1,
"name": "Hamburguer",
"category": "Sanduíches",
"price": 7.99,
"image": "https://i.ibb.co/ncghLcC/hamburguer.jpg"
}
...

# Acesso ao carrinho:

## Para adicionar produtos ao carrinho:

POST/cart

O usuário deverá estar logado para adicionar o produto ao carrinho.

body para requisição:

Header: { Authorization: Bearer {token} }

Body:

{
"name": "Hamburguer",
"category": "Sanduíches",
"price": 7.99,
"image": "https://i.ibb.co/ncghLcC/hamburguer.jpg",
"userId": 1
}

Resposta:

status 200

# Para acessar o carrinho:

O usuário deverá estar logado para acessar o carrinho.

GET/cart

Requisição:

Header: { Authorization: Bearer {token} }

Resposta:

status 200

[
{
"name": "Hamburguer",
"category": "Sanduíches",
"price": 7.99,
"image": "https://i.ibb.co/ncghLcC/hamburguer.jpg",
"userId": 1,
"id": 1,
}, ...]

# Deletar produto do carrinho:

DELETE/cart/id

Requisição:

Requisição:

Header: { Authorization: Bearer {token} }

Resposta:

status 200

{}
