# ⛪ Ministério ELIM — Cadastro de Jovens

Formulário de cadastro para o Ministério de Jovens ELIM, com design dark mode, identidade visual moderna e integração automática com planilha Google Sheets.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-222?style=flat&logo=github&logoColor=white)

---

## ✨ Funcionalidades

- **Cadastro completo** — Nome, aniversário, foto de perfil, e-mail e celular
- **Upload de foto** — Envio automático para [imgbb](https://imgbb.com) com preview circular
- **Google Sheets** — Dados salvos direto na planilha via Google Apps Script
- **Máscara de celular** — Formatação automática `(XX) XXXXX-XXXX`
- **Validação** — Todos os campos são validados antes do envio
- **Feedback visual** — Loading spinner, toast de sucesso/erro
- **Responsivo** — Funciona perfeitamente em mobile e desktop
- **Zero dependências** — Arquivo único `index.html`, sem frameworks

## 🎨 Design

| Elemento | Detalhe |
|---|---|
| Fundo | Preto `#080810` com glow radial roxo |
| Cor de destaque | Roxo elétrico `#7c3aed` / `#a855f7` |
| Títulos | Bebas Neue (Google Fonts) |
| Corpo | Outfit (Google Fonts) |
| Animações | fadeUp escalonado nos elementos |
| Botão | Gradiente roxo com hover scale |

## 🚀 Como usar

### 1. Clone o repositório

```bash
git clone https://github.com/gabrielfernandessc/form.git
```

### 2. Configure as chaves

No arquivo `index.html`, edite as variáveis no topo do `<script>`:

```javascript
const IMGBB_API_KEY     = "SUA_KEY_AQUI";
const GOOGLE_SCRIPT_URL = "SUA_URL_AQUI";
```

### 3. Configure o Google Sheets

1. Crie uma planilha no [Google Sheets](https://sheets.google.com)
2. Vá em **Extensões → Apps Script**
3. Cole o código abaixo e salve:

```javascript
function doPost(e) {
  const data = JSON.parse(e.postData.contents);
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  sheet.appendRow([
    new Date(),
    data.nome,
    data.aniversario,
    data.foto,
    data.email,
    data.celular
  ]);
  return ContentService.createTextOutput("OK");
}
```

4. Clique em **Implantar → Nova implantação → App da Web**
5. Configure: **Executar como: Eu** | **Acesso: Qualquer pessoa**
6. Copie a URL gerada e cole na variável `GOOGLE_SCRIPT_URL`

### 4. Hospede no GitHub Pages

1. Vá em **Settings → Pages**
2. Em Source, selecione a branch `main`
3. O site estará em: `https://gabrielfernandessc.github.io/form/`

## 📁 Estrutura

```
form/
└── index.html   ← Tudo aqui: HTML + CSS + JS
```

## 📄 Licença

Uso livre para o Ministério ELIM.
