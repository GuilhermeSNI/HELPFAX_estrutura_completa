# HELPFAX — Sistema de Estoque de Toners

Aplicação com **frontend estático + API Node.js/Express + PostgreSQL**.

## Estrutura recomendada

```text
GitHub Pages
   ↓
index.html + CSS + JS
   ↓ HTTPS
API Node.js / Express (Render, Railway, VPS etc.)
   ↓
PostgreSQL
```

A pasta `public` **não é necessária**. O conteúdo do frontend permanece na raiz do projeto.

## 1. Frontend no GitHub Pages

O GitHub Pages publica o `index.html` e os arquivos estáticos da raiz.

Antes de publicar, abra `api-config.js` e troque:

```js
window.HELPFAX_API_URL = "";
```

pela URL pública da sua API, por exemplo:

```js
window.HELPFAX_API_URL = "https://helpfax-api.onrender.com";
```

Não coloque `DATABASE_URL` ou `JWT_SECRET` nesse arquivo. Essas informações ficam **somente no backend**.

## 2. Backend Node.js

Publique o mesmo repositório em uma hospedagem que execute Node.js, como Render, Railway ou uma VPS.

Comando de instalação:

```bash
npm install
```

Comando de inicialização:

```bash
npm start
```

O serviço precisa executar `server.js`.

## 3. Variáveis do backend

Configure no serviço Node.js:

```env
DATABASE_URL=postgresql://USUARIO:SENHA@HOST:5432/NOME_DO_BANCO
JWT_SECRET=uma-chave-longa-e-aleatoria
FRONTEND_URL=https://SEU_USUARIO.github.io/SEU_REPOSITORIO
PGSSL=true
```

`FRONTEND_URL` deve ser a origem do seu GitHub Pages, sem precisar colocar `/index.html`.

## 4. Testar a API

Depois do deploy do backend, abra:

```text
https://SEU-BACKEND/api/health
```

O resultado esperado é:

```json
{"ok":true,"banco":"conectado"}
```

Se aparecer `banco: "indisponível"`, o problema está na conexão do PostgreSQL ou na `DATABASE_URL`.

## 5. Banco de dados

O servidor cria as tabelas necessárias automaticamente ao iniciar e garante o usuário padrão:

- Usuário: `guilherme`
- Senha: `1234`

Para produção, recomenda-se trocar a senha padrão depois do primeiro acesso.

## Desenvolvimento local

```bash
npm install
npm start
```

Abra `http://localhost:3000` somente se estiver usando o backend para servir o frontend externamente. Para testar o frontend separado, configure `api-config.js` com a URL da API local.
