# HELPFAX — GitHub Pages + API Node.js + PostgreSQL

## 1. GitHub Pages
Envie `index.html`, `app.js`, `style.css`, `images/` e `api-config.js` para o repositório do GitHub Pages.

Em `api-config.js`, coloque a URL do backend:
```js
window.HELPFAX_API_URL = "https://SUA-API.onrender.com";
```

## 2. Backend
O backend é o `server.js` deste mesmo projeto. Publique-o em Render, Railway ou outro serviço que execute Node.js.

Variáveis de ambiente:
- `DATABASE_URL` = URL do PostgreSQL
- `JWT_SECRET` = uma chave secreta forte
- `FRONTEND_URL` = `https://guilhermesni.github.io` (ou a origem exata do seu Pages)
- `NODE_ENV` = `production`

## 3. Teste
Depois do deploy, abra:
`https://SUA-API.onrender.com/api/health`

Deve retornar:
```json
{"ok":true,"banco":"conectado"}
```

## Importante
GitHub Pages não executa Node.js nem acessa PostgreSQL diretamente. Ele hospeda apenas o frontend. O `server.js` precisa estar rodando em um servidor Node.
