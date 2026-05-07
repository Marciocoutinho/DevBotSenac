# 🚀 Guia de Deploy no Vercel - DevBot

## ✅ Alterações Realizadas

Seu projeto foi preparado para ser hospedado no Vercel com as seguintes mudanças:

### 1. **package.json** ✓

- Adicionado script `start: "node server.js"`
- Vercel usará este script para iniciar a aplicação

### 2. **vercel.json** ✓ (Novo)

- Configuração específica do Vercel
- Define Node.js como runtime
- Configura rotas para o servidor Express
- Placeholder para variáveis de ambiente

### 3. **script.js** ✓

- URL hardcoded `http://localhost:3000/chat` → `/chat` (URL relativa)
- Funcionará automaticamente em qualquer domínio (local ou produção)

### 4. **.gitignore** ✓

- Expandido com padrões de segurança
- Protege `.env` e arquivos sensíveis

---

## 📋 Passos para Deploy

### **Passo 1: Preparar o Repositório Git**

```bash
git add .
git commit -m "Preparar projeto para Vercel"
git push origin main
```

### **Passo 2: Conectar no Vercel**

1. Acesse [vercel.com](https://vercel.com)
2. Clique em **"New Project"**
3. Selecione seu repositório GitHub
4. Clique em **Import**

### **Passo 3: Configurar Variáveis de Ambiente**

Na página de configuração do Vercel, adicione:

**Nome:** `OPENAI_API_KEY`  
**Valor:** Sua chave da API OpenAI (ex: `sk-...`)

> Para obter a chave: https://platform.openai.com/api-keys

### **Passo 4: Deploy**

1. Clique em **Deploy**
2. Aguarde a conclusão (1-2 minutos)
3. Vercel fornecerá uma URL (ex: `https://devbot-senac.vercel.app`)

---

## 🔍 Verificação de Compatibilidade

| Item                  | Status | Detalhes                                 |
| --------------------- | ------ | ---------------------------------------- |
| Node.js/Express       | ✅     | Suportado nativamente                    |
| Port dinâmica         | ✅     | Configurado para usar `process.env.PORT` |
| CORS                  | ✅     | Habilitado para acesso frontend          |
| Arquivos estáticos    | ✅     | `express.static()` configurado           |
| Variáveis de ambiente | ✅     | Suportadas via `.env`                    |
| API OpenAI            | ✅     | Integrada e funcional                    |

---

## ⚠️ Limitações do Vercel (Serverless)

1. **Tempo máximo de requisição: 60 segundos** (função serverless)
2. **Sem persistência local** (banco de dados local não funciona)
3. **Sem WebSocket nativo** (apenas HTTP)

> Para seu chat API OpenAI, estas limitações não são problema!

---

## 🧪 Teste Local Antes de Deploy (Opcional)

```bash
npm install
npm start
```

Acesse `http://localhost:3000` em seu navegador.

---

## 🐛 Troubleshooting

### "OPENAI_API_KEY not defined"

- Verifique se a variável foi configurada no Vercel Dashboard
- Recrie o Deploy após adicionar a variável

### "Cannot POST /chat"

- Verifique se `server.js` está na raiz do projeto
- Confirme que `vercel.json` está presente

### "404 - index.html not found"

- Certifique-se de que `index.html` está no root
- Verifique se o caminho em `express.static()` está correto

---

## 📚 Recursos Úteis

- [Documentação Vercel com Node.js](https://vercel.com/docs/frameworks/nodejs)
- [Variáveis de Ambiente](https://vercel.com/docs/concepts/projects/environment-variables)
- [Troubleshooting Deploy](https://vercel.com/docs/platform/frequently-asked-questions)

---

## ✨ Próximas Melhorias (Opcional)

1. Adicionar tela de loading melhorada
2. Implementar autenticação para proteger a API
3. Adicionar rate limiting para evitar abuso
4. Usar banco de dados para histórico de chat (MongoDB, Supabase)
5. Adicionar testes automatizados

---

**Seu projeto está pronto para Vercel! 🎉**
