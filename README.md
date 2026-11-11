# Monitoramento da Educação Infantil · Lagoa da Canoa

Sistema web interativo para acompanhamento e registro do desenvolvimento e aprendizagem na Educação Infantil do Município de Lagoa da Canoa - AL.

O sistema opera com frontend estático (SPA) hospedado no **GitHub Pages** e backend serverless no **Google Sheets** integrado via **Google Apps Script**.

---

## 🚀 Acesso ao Sistema (GitHub Pages)

- **URL do Aplicativo:** `https://douglas14031999.github.io/monitoramento-educacao-infantil/`
- **Página principal:** `index.html`

---

## 🛠️ Arquitetura e Tecnologias

- **Frontend:**
  - HTML5, CSS3 moderno com suporte a modo claro/escuro (`prefers-color-scheme`).
  - JavaScript Vanilla sem dependências pesadas externas.
  - Tipografia: Google Fonts (*Plus Jakarta Sans*).
  - Ícones e logomarca oficial de Lagoa da Canoa embutidos em base64.
- **Backend / Banco de Dados:**
  - Google Sheets (planilha institucional da Secretaria de Educação).
  - Google Apps Script exposto como Web App (`doGet` e `doPost`).
  - Cache de sessão e proteção contra força bruta por CPF.
  - Autenticação e validação de dígitos verificadores de CPF no cliente e no servidor.

---

## ⚙️ Configuração e Implantação

### 1. Planilha e Apps Script (Backend)
1. Crie uma nova planilha no Google Sheets na conta institucional da Secretaria.
2. Acesse **Extensões > Apps Script**.
3. Cole o conteúdo de [`Codigo.gs`](./Codigo.gs).
4. Edite a constante `ADMIN_INICIAL` com o CPF válido do administrador.
5. Selecione a função `configurarPlanilha` e clique em **Executar** (autorize as permissões solicitadas pelo Google).
   - *(Opcional)*: Para carregar turmas e indicadores padrão de demonstração, execute `carregarDadosDeExemplo`.
6. Vá em **Implantar > Nova implantação > Tipo: App da Web**:
   - **Executar como:** *Eu (seu e-mail)*
   - **Quem tem acesso:** *Qualquer pessoa*
7. Copie a URL gerada terminada em `/exec`.

### 2. Configuração do Frontend
A URL do Web App gerada é definida na constante `API_URL` dentro de [`index.html`](./index.html):

```javascript
const API_URL = "https://script.google.com/macros/s/AKfycbwxdl5pFK04PZ8grLDLZbol1NgeLitiWPxVMoZWeEhYJQuAozHU0r48Y8GujXVsTN4f/exec";
```

### 3. Ativar o GitHub Pages
1. No repositório do GitHub, vá em **Settings** (Configurações).
2. Na barra lateral esquerda, clique em **Pages**.
3. Em **Build and deployment > Source**, selecione **Deploy from a branch**.
4. Em **Branch**, selecione `main` e a pasta `/ (root)`.
5. Clique em **Save**. Em instantes, o site estará publicado e acessível publicamente com HTTPS.

---

## 🔒 Segurança e Privacidade

- **Proteção de CPFs:** A planilha de banco de dados deve permanecer restrita apenas ao administrador e à conta do Apps Script.
- **Requisições sem Preflight:** As chamadas de API utilizam `Content-Type: text/plain;charset=utf-8` para compatibilidade total com o CORS do Google Apps Script sem bloqueios de preflight.
- **Sessões Temporárias:** Os tokens de sessão são mantidos no `sessionStorage` e validados pelo `CacheService` do Apps Script.

