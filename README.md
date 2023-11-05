<h1 align="center">
  <img alt="KenzieHub" title="KenzieHub" src="https://kenzie.com.br/_next/image?url=%2Fimages%2Flogo.png&w=640&q=75" width="100px" />
</h1>

<h1 align="center">
  FashionStore - API
</h1>

<p align="center">
  <a href="#endpoints">Endpoints</a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</p>

A API tem um total de 13 endpoints, sendo em volta principalmente do usuário (dev) - podendo cadastrar seu perfil, tecnologias que estuda e trabalhos realizados. <br/>

A url base da API é [https://fashion-store-api.onrender.com](https://fashion-store-api.onrender.com/)

## Rotas que não precisam de autenticação

<h2 align ='center'> Listagem de produtos </h2>

Nessa aplicação o usuário sem fazer login ou se cadastrar pode ver os produtos já cadastrados na plataforma, na API podemos acessar a lista dessa forma:

`GET /products - FORMATO DA RESPOSTA - STATUS 200`

```json
[
  {
    "id": 1,
    "name": "Blazer Branco Elegante",
    "price": 490,
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin massa metus, tempus nec ex ac, condimentum convallis diam. Donec at nisi lorem. Aliquam non dolor bibendum, venenatis ante ac, lobortis justo. Vestibulum nec pretium mi, eu consequat dolor.",
    "image": "https://res.cloudinary.com/dsbkp5841/image/upload/v1687807062/Rectangle_4_hwrkgf.jpg"
  },
  {
    "id": 2,
    "name": "Blazer Laranja",
    "price": 320,
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin massa metus, tempus nec ex ac, condimentum convallis diam. Donec at nisi lorem. Aliquam non dolor bibendum, venenatis ante ac, lobortis justo. Vestibulum nec pretium mi, eu consequat dolor.",
    "image": "https://res.cloudinary.com/dsbkp5841/image/upload/v1687807062/Rectangle_7_ofhcmq.jpg"
  },
  {
    "id": 3,
    "name": "Sapatos Amarelo",
    "price": 490,
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin massa metus, tempus nec ex ac, condimentum convallis diam. Donec at nisi lorem. Aliquam non dolor bibendum, venenatis ante ac, lobortis justo. Vestibulum nec pretium mi, eu consequat dolor.",
    "image": "https://res.cloudinary.com/dsbkp5841/image/upload/v1687807062/Rectangle_6_p53ulc.jpg"
  },
  {
    "id": 4,
    "name": "Calça Preta",
    "price": 140,
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin massa metus, tempus nec ex ac, condimentum convallis diam. Donec at nisi lorem. Aliquam non dolor bibendum, venenatis ante ac, lobortis justo. Vestibulum nec pretium mi, eu consequat dolor.",
    "image": "https://res.cloudinary.com/dsbkp5841/image/upload/v1687807062/Rectangle_8_ijrp7v.jpg"
  }
]
```

Também é possível acessar um produto específico passando o id para rota:

`GET /products/:id - FORMATO DA RESPOSTA - STATUS 200`
```json
{
  "id": 4,
  "name": "Calça Preta",
  "price": 140,
  "description": "https://res.cloudinary.com/dsbkp5841/image/upload/v1687807062/Rectangle_8_ijrp7v.jpg"
}
```

<h2 align ='center'> Criação de usuário </h2>

`POST /users - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "johndoe@email.com",
  "password": "123456",
  "name": "John Doe",
}
```

Caso dê tudo certo, a resposta será assim:

`POST /users - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImpvaG5kb2VAZW1haWwuY29tIiwiaWF0IjoxNjg3ODA4MTYzLCJleHAiOjE2ODc4MTE3NjMsInN1YiI6IjMifQ.nWj1gqD4t3x00UTQvfFiK-PQjcgSpzbGeHknpncgC9E",
  "user": {
    "email": "johndoe@email.com",
    "name": "John Doe",
    "id": 3
  }
}
```


<h2 align = "center"> Login </h2>

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "johndoe@email.com",
  "password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImpvaG5kb2VAZW1haWwuY29tIiwiaWF0IjoxNjg3ODA4MTYzLCJleHAiOjE2ODc4MTE3NjMsInN1YiI6IjMifQ.nWj1gqD4t3x00UTQvfFiK-PQjcgSpzbGeHknpncgC9E",
  "user": {
    "email": "johndoe@email.com",
    "name": "John Doe",
    "id": 3
  }
}
```

## Rotas que necessitam de autorização

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

> Authorization: Bearer {token}


<h2 align = "center"> Autologin </h2>

Essa rota exige autorização mas não precisa de um corpo.

`GET /users/:userId - FORMATO DA RESPOSTA`

```json
{
  "email": "johndoe@email.com",
  "name": "John Doe",
  "id": 3
}
```




<h2 align ='center'> Cadastrar produto </h2>

`POST /products - FORMATO DA REQUISIÇÃO`

```json
{
  "name": "Blazer Branco Elegante",
  "price": 490,
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin massa metus, tempus nec ex ac, condimentum convallis diam. Donec at nisi lorem. Aliquam non dolor bibendum, venenatis ante ac, lobortis justo. Vestibulum nec pretium mi, eu consequat dolor.",
  "image": "https://res.cloudinary.com/dsbkp5841/image/upload/v1687807062/Rectangle_4_hwrkgf.jpg"
}
```


<h2 align ='center'> Atualizar produto </h2>

`PUT /products/:id - FORMATO DA REQUISIÇÃO`

```json
{
  "name": "Blazer Branco Elegante",
  "price": 490,
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin massa metus, tempus nec ex ac, condimentum convallis diam. Donec at nisi lorem. Aliquam non dolor bibendum, venenatis ante ac, lobortis justo. Vestibulum nec pretium mi, eu consequat dolor.",
  "image": "https://res.cloudinary.com/dsbkp5841/image/upload/v1687807062/Rectangle_4_hwrkgf.jpg"
}
```

Também é possível deletar um produto, utilizando este endpoint:

`DELETE /products/:id`

```
Não é necessário um corpo da requisição.
```
