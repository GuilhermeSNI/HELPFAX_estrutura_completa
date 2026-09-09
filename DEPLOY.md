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
- `FRONTEND_URL` = a origem do seu GitHub Pages, por exemplo `https://guilhermesni.github.io`
  (sem precisar colocar `/HELPFAX_estrutura_completa` no final).
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


## Login funcionando
Após o deploy do backend e a configuração do PostgreSQL:
- Usuário: `guilherme`
- Senha: `1234`

O servidor cria/atualiza automaticamente esse usuário na inicialização. Se o frontend estiver no GitHub Pages, confirme que `FRONTEND_URL` no Render corresponde exatamente ao domínio do Pages e que `api-config.js` aponta para a URL do backend.
