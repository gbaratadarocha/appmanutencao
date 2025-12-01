# 🔧 App de Manutenção Industrial

Aplicação web completa para gestão de pedidos de manutenção industrial com integração Google Sheets e **gestão de stock**.

---

## 🔴 ERRO DE LOGIN? LEIA ISTO!

**Mensagem na consola:**  
❌ "Login falhado: Username ou password incorretos"

### 🎯 Causa Mais Comum:
**Utilizador "admin" não existe na sheet!**

**Solução IMEDIATA (30s):**  
Fazer login com utilizador real da sheet:
```
Username: Goncalo
Password: 1234
```

📄 Detalhes: `SOLUCAO_IMEDIATA.txt` | `PROBLEMA_IDENTIFICADO.md`

---

### 🔧 Outras Causas Possíveis:
- Apps Script não atualizado/deployed
- Sheet "utilizadores" mal configurada

**Solução rápida (2 min):** 📄 `CHECKLIST_VISUAL_2MIN.txt`  
**Solução completa (5 min):** 📄 `RESOLVER_ERRO_LOGIN_AGORA.txt`

---

## 🚨 Setup Obrigatório (Primeira Vez)

⚠️ **ANTES DE USAR, FAZER ISTO** (5 minutos):

### 1️⃣ Atualizar Google Apps Script
```
Google Sheets → Extensions → Apps Script
→ Copiar código de: GoogleAppsScript_COM_STOCK_VAR.js
→ Colar (substituir tudo) → Save
→ Deploy → Nova versão (v3.2.6 - Login normalizado)
→ Acesso: "Qualquer pessoa"
```

📄 Guia: `CODIGO_CORRIGIDO_AGORA.txt` (2 min)

### 2️⃣ Criar Sheet "utilizadores" (minúsculas!)
```
Headers:
Username | Password | Nome Completo | Departamento | Role | Pode Editar Planeamento | Ativo | Último Login

Admin (linha 2):
admin | admin123 | Administrador | TI | admin | TRUE | TRUE | 
```

💡 **Excel converte "true" para "TRUE"** - É NORMAL! Código aceita ambos.

📄 **Guia completo**: `CORRIGIR_LOGIN_AGORA.txt` (5 minutos, passo a passo)

---

## ✨ Funcionalidades

### 🔐 Sistema de Autenticação (v3.2.5)
- ✅ **Login obrigatório** (username/password)
- ✅ **Gestão de utilizadores** via Google Sheets
- ✅ **Permissões baseadas em roles** (admin/técnico/visualizador)
- ✅ **Auto-preenchimento de campos** baseado no utilizador logado
- ✅ **Controlo de acesso** ao planeamento
- ✅ **Aceita TRUE/true/1** (compatível com Excel) 🆕
- ✅ **Sessão persistente** (localStorage)
- ✅ **Logo personalizado** (transparente, sem fundo) 🆕
- ✅ **Segurança melhorada** (credenciais não expostas) 🆕

### 🔧 Gestão de Manutenção
- ✅ Criar pedidos de manutenção
- ✅ **Departamento e nome preenchidos automaticamente** 🆕
- ✅ Lista de pedidos com filtros
- ✅ Planeamento semanal (com controlo de permissões) 🆕
- ✅ Standards de manutenção (PDFs)
- ✅ **Exportar para Excel com fotos clicáveis** 📸 🆕
- ✅ Captura de fotografias
- ✅ **Dados partilhados** via Google Sheets

### 📦 Gestão de Stock (v2.0 - REDESENHADO!)
- ✅ **Pesquisa inteligente** de artigos (nome, ref, código, fornecedor)
- ✅ **Baixa rápida** com validações automáticas
- ✅ **Consulta de stock** em tempo real
- ✅ **Histórico editável** de movimentos
- ✅ **Responsável preenchido automaticamente** 🆕
- ✅ Registo completo de entradas/saídas/ajustes
- ✅ Cálculo automático de stock
- ✅ Indicadores visuais (stock baixo/OK)
- ✅ Interface intuitiva em duas secções
- ✅ Notificações toast de feedback
- ✅ Filtros por tipo e limite de registos

### 🎨 Interface
- ✅ Design responsivo (mobile-friendly)
- ✅ PWA - Pode ser instalado no telemóvel
- ✅ Funciona offline
- ✅ Interface estilo Apple

## 🚀 Como Usar

### Acesso Web
Abre no browser (PC ou telemóvel):
```
https://SEU-USERNAME.github.io/app-manutencao/
```

### Instalar no iPhone
1. Abre no Safari
2. Clica **Partilhar** (ícone em baixo)
3. **Adicionar ao Ecrã Principal**

### Instalar no Android
1. Abre no Chrome
2. Menu → **Instalar App**

## 🔐 Sistema de Login (v3.1 - NOVO!)

### 🚀 Início Rápido (5 min)
1. **Criar sheet `utilizadores`** no Google Sheets
2. **Copiar colunas** (ver `COPIAR_PARA_SHEET_UTILIZADORES.txt`):
   ```
   Username | Password | Nome Completo | Departamento | Role | Pode Editar Planeamento | Ativo | Último Login
   ```
3. **Adicionar utilizador admin**:
   ```
   admin | admin123 | Administrador | TI | admin | true | true |
   ```
4. **Atualizar Google Apps Script** (v3.1.4)
5. **Testar login** em `index.html`

### 📚 Documentação Completa
- **COMECE_AQUI_LOGIN.md** - Guia de implementação
- **AUTO_PREENCHIMENTO_CORRIGIDO.md** - Como funciona o auto-preenchimento
- **TESTE_ESTE_FICHEIRO.txt** - Checklist de testes ⭐
- **ESTRUTURA_SHEET_UTILIZADORES.md** - Estrutura da sheet

### 🎯 O Que Faz
✅ **Auto-preenchimento baseado no utilizador**:
- Novo Pedido → Departamento + Nome (read-only)
- Novo Movimento → Responsável (editável)

✅ **Controlo de permissões**:
- Admin → Acesso total
- Técnico → Pode criar pedidos/movimentos + editar planeamento (se autorizado)
- Visualizador → Apenas visualização

✅ **Sessão persistente**:
- Login mantém-se após fechar o browser
- Token armazenado em localStorage

### 👥 Roles Disponíveis
- `admin` - Controlo total (sempre pode editar planeamento)
- `tecnico` - Criar pedidos/movimentos + planeamento (se `Pode Editar Planeamento = true`)
- `visualizador` - Apenas visualização

## 📊 Google Sheets

Os dados são sincronizados automaticamente com Google Sheets.

**Estrutura do Google Sheets:**
- 👤 **utilizadores** - Gestão de utilizadores e permissões (v3.1)
- 📋 **Pedidos de Manutenção** - Registo de pedidos (com fotos)
- 📅 **Planeamento** - Planeamento semanal
- 📦 **Artigos** - Catálogo de stock
- 📝 **Movimentos** - Histórico de stock
- 📝 **Logs** - Logs de erros e ações (opcional)

## 📸 Fotos no Excel (v3.2 - NOVO!)

### 🎯 O Que Faz
Ao exportar pedidos para Excel, as fotos aparecem como **hiperlinks clicáveis**:
- ✅ Célula mostra: **"Ver Foto"** (azul e sublinhado)
- ✅ Ao clicar: **Abre a foto no navegador**
- ✅ Funciona offline (foto embutida no Excel)

### 📚 Documentação
- **TESTE_FOTOS_EXCEL.txt** - Teste rápido (5 min) ⭐
- **ATUALIZACAO_FOTOS_EXCEL.md** - Documentação técnica completa

### ✨ Vantagens
- 📸 Fotos ficam **dentro do Excel** (não precisa servidor)
- 🔗 Um clique para ver a foto
- 📦 Pode copiar Excel e fotos vão junto
- 🌐 Funciona em Excel 2007+ e Google Sheets

## 📦 Módulo de Stock

### 🆕 Redesign v2.0 (Jan 2025)
O tab de stock foi **completamente redesenhado** com base no feedback do utilizador:
- **STOCK_TAB_REDESIGN_COMPLETE.md** - Documentação completa do redesign ⭐
- **GUIA_RAPIDO_STOCK.md** - Guia de utilização rápida 🚀

### Começar Aqui
Para implementar o módulo de stock, consultar:
1. **COMECE_AQUI_STOCK.md** - Guia de início rápido (5 min)
2. **GUIA_IMPLEMENTACAO_STOCK.md** - Tutorial passo-a-passo (20 min)
3. **README_STOCK.md** - Documentação técnica completa

### Ficheiros do Módulo
- `GoogleAppsScript_COM_STOCK.js` - Backend API
- `stock-module.html` - Frontend (HTML/CSS/JS)
- `TEMPLATE_Artigos.csv` - Template de artigos
- `TEMPLATE_Movimentos.csv` - Template de movimentos
- `processar-artigos.html` - Conversor Excel→CSV

### 🎯 Funcionalidades do Redesign
1. **Secção 1**: Consulta de stock + Baixa rápida
2. **Secção 2**: Histórico completo de movimentos
3. Edição e eliminação de movimentos
4. Validações robustas
5. Interface tabular otimizada

### Famílias de Artigos
- ⚙️ ROLAMENTOS
- 🔩 PARAFUSOS E FIXAÇÕES
- 🔌 ELÉTRICO
- 🛢️ HIDRÁULICA
- ⛓️ CORREIAS E CORRENTES
- 🔧 FERRAMENTAS
- 🧴 LUBRIFICANTES E QUÍMICOS
- 🏭 PEÇAS MÁQUINAS
- 🚨 SEGURANÇA
- 📦 DIVERSOS

## 🛠️ Tecnologias

- HTML5 + CSS3 + JavaScript
- Google Apps Script (backend)
- Google Sheets (base de dados)
- Service Worker (offline support)
- PWA (Progressive Web App)

## 📱 Compatibilidade

✅ iPhone Safari  
✅ Android Chrome  
✅ Desktop (Chrome, Firefox, Safari, Edge)  

## 📄 Licença

Uso interno - Manutenção Industrial

## 📚 Documentação

### Documentação Geral
- `README.md` - Este ficheiro (visão geral)
- `DEPLOY-GITHUB.md` - Como fazer deploy no GitHub Pages
- `COMO-VER-FOTOS-GOOGLE-SHEETS.md` - Ver fotos no Sheets
- `ATUALIZACAO-RESPONSAVEIS.md` - Atualizar lista de responsáveis

### Documentação do Módulo de Stock
- `STOCK_TAB_REDESIGN_COMPLETE.md` - **Redesign v2.0** (NOVO!) ⭐⭐⭐
- `GUIA_RAPIDO_STOCK.md` - **Guia rápido de utilização** (NOVO!) 🚀
- `INDICE_MODULO_STOCK.md` - Índice completo do módulo
- `COMECE_AQUI_STOCK.md` - Guia de início rápido ⭐
- `GUIA_IMPLEMENTACAO_STOCK.md` - Tutorial detalhado ⭐
- `README_STOCK.md` - Documentação técnica 📊

---

**Versão:** 2.4.0 (filtro de família no modal) 🔍  
**Última atualização:** 2025-01-20  

### 🆕 Novidades da v2.4 (LATEST!)
- ✅ **Filtro de família no modal** - Seleciona categoria antes do artigo
- ✅ **Filtragem automática** - Dropdown atualiza ao escolher família
- ✅ **Pesquisa por família** - Procura artigos pela categoria
- ✅ **Interface com cards visuais** - Design moderno e profissional
- ✅ **Layout em grid responsivo** - 1 a 3+ colunas automáticas
- ✅ **Stock em destaque visual** - Cores verde/vermelho intuitivas
- ✅ **Pré-seleção inteligente** - Baixa rápida pré-seleciona família
- ✅ **3 secções organizadas** - Consulta, Novo Movimento, Histórico
