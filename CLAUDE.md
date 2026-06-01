# Clan Olimpo — Site do Clã (NightPT / Priston Tale)

## Visão Geral
Site completo para gerenciamento do clã Olimpo no servidor NightPT de Priston Tale.
Single-page application (SPA) em HTML/CSS/JS puro — **um único arquivo**: `index.html`.

## Estrutura do Projeto
```
clan-olimpo/
├── index.html        ← TODO o site está aqui (HTML + CSS + JS)
├── CLAUDE.md         ← este arquivo (instruções para o Claude Code)
├── CONFIGURACAO.md   ← guia de configuração Firebase e personalização
└── CHANGELOG.md      ← histórico de alterações
```

## Seções do site (páginas SPA)
| ID da página     | Descrição                              |
|-----------------|----------------------------------------|
| `page-home`     | Landing page com logo, stats e link NightPT |
| `page-members`  | Gerenciador de membros (CRUD)          |
| `page-items`    | Lista de itens Boss (tempo real)       |
| `page-server`   | Info + iframe do NightPT               |

## Onde editar cada coisa no index.html

### ⚙ Configurações gerais
Bloco `CONFIG` no topo do `<script>` (linha ~15):
```js
const CONFIG = {
  clanName:    "Olimpo",      // nome do clã
  serverName:  "NightPT",     // nome do servidor
  serverUrl:   "https://nightpt.com/",
  descricao:   "...",         // texto da home
  firebase: { ... }           // credenciais Firebase
}
```

### 🗡 Itens Boss
Array `ITEMS` logo abaixo do CONFIG:
```js
const ITEMS = [
  { id:'tulla', name:'Tulla', icon:'💎' },
  // adicione ou remova itens aqui
]
```

### 🎨 Cores e tema
Variáveis CSS no bloco `:root` (logo no início do `<style>`):
```css
:root {
  --gold:       #c9a227;   /* cor principal dourada */
  --gold-light: #f0c84a;   /* dourado claro */
  --dark:       #08070A;   /* fundo principal */
  --text:       #e8d9a0;   /* texto principal */
  ...
}
```

### 🖼 Logo
A logo está embutida como base64 direto no JS:
```js
const LOGO_SRC = "data:image/jpeg;base64,/9j/...";
```
Para trocar: converta a nova imagem em base64 e substitua o valor.

## Firebase (banco de dados em tempo real)
Preencha o objeto `CONFIG.firebase` com as credenciais do seu projeto.
Sem Firebase, o site funciona localmente (dados ficam apenas na memória da sessão).

## Como adicionar uma nova aba/página
1. Adicione o link na navbar:
```html
<a href="#" onclick="showPage('novaaba',this);return false;">Nova Aba</a>
```
2. Crie o bloco da página:
```html
<div id="page-novaaba" class="page">
  <!-- conteúdo aqui -->
</div>
```

## Como fazer deploy
- **tiiny.host** — arraste o `index.html` → link instantâneo
- **Netlify Drop** — arraste a pasta `clan-olimpo/` → link instantâneo
- **GitHub Pages** — suba o repositório e ative Pages na branch main

## Tecnologias
- HTML5 / CSS3 / Vanilla JS (ES Modules)
- Firebase Realtime Database v10 (via CDN)
- Google Fonts: Cinzel Decorative, Cinzel, Crimson Text
- Zero dependências locais (tudo via CDN)
