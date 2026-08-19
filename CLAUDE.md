# CLAUDE.md

Este arquivo dá contexto ao Claude Code sobre este projeto. Leia antes de fazer qualquer alteração.

## O que é este projeto

Site de portfólio pessoal (uma página só, scroll único) de **Gustavo Vecchiatti Aguiar** — designer gráfico, motion designer e artista 3D atuando no setor de saúde (Sintegra Surgical Sciences). Destino final: **GitHub Pages**, sem build step, sem framework, sem custo de hospedagem.

## Stack

- HTML + CSS + JS **puros**, tudo em um único arquivo: `index.html`.
- Sem bundler, sem npm, sem dependências além de fontes do Google Fonts via CDN (`<link>` no `<head>`).
- Não introduzir React, Vue, Tailwind, build tools, etc. a menos que o usuário peça explicitamente — o objetivo é continuar simples e 100% compatível com GitHub Pages estático.

## Estrutura de arquivos

```
index.html          → site inteiro (HTML + <style> + <script> inline)
README.md            → instruções de deploy no GitHub Pages / domínio próprio
CLAUDE.md            → este arquivo
assets/images/       → fotos (hoje só tem LEIA-ME.txt de placeholder)
assets/video/        → vídeos (hoje só tem LEIA-ME.txt de placeholder)
assets/models/       → exports .glb do Blender, se algum dia for usado 3D interativo na web
```

## Sistema de design (tokens, em `:root` no `<style>`)

- `--paper` (#faf9f6) fundo principal, quase branco — direção minimalista clean pedida pelo usuário
- `--ink` (#121212) texto principal
- `--accent` (#ff3b30) vermelho "REC" — usado com moderação, é a cor de assinatura do site (referência a gravação/edição de vídeo)
- `--accent-2` (#1e40ff) cobalto, uso esporádico
- Tipografia: `Space Grotesk` (display/títulos), `Newsreader` itálica (storytelling na seção Sobre), `IBM Plex Mono` (labels, timecodes, eyebrows)
- **Não trocar a paleta por tons terrosos/creme (#F4F1EA + terracota) nem por dark mode com verde ácido** — são os defaults genéricos de design gerado por IA que foram deliberadamente evitados aqui.

## Elemento de assinatura (não remover sem discutir com o usuário)

O **"timeline scrubber"** fixo no topo (`#scrubber`) é o elemento central do conceito: uma barra de progresso de scroll estilizada como linha do tempo de edição de vídeo, com timecode falso (`00:00:00:00`) que avança conforme o usuário rola a página, e um ponto vermelho pulsante "REC". Isso é intencional — reforça a identidade de motion designer/videomaker do usuário. Manter esse motivo consistente em qualquer nova seção.

## Sistema de i18n (PT/EN)

- Objeto `i18n` no `<script>`, com chaves `pt` e `en`.
- Elementos de texto usam `data-i18n="chave.aninhada"` e são preenchidos via `el.innerHTML = i18n[lang][key]`.
- Função `setLang(lang)` troca todo o texto da página e persiste a escolha em `localStorage`.
- **Ao adicionar qualquer novo texto ao site, sempre adicionar a chave correspondente nos dois idiomas** (`pt` e `en`) dentro do objeto `i18n`, nunca deixar texto hardcoded sem passar pelo sistema de tradução.

## Placeholders de mídia — IMPORTANTE

Todos os blocos `.thumb` (cards de projeto) e `.portrait` (foto do Sobre) são atualmente gradientes CSS de placeholder. O usuário ainda vai adicionar fotos/vídeos reais. Ao trabalhar no projeto:

- Não inventar/gerar imagens fake para substituir os placeholders sem que o usuário forneça o arquivo.
- Se o usuário anexar imagens, colocá-las em `assets/images/` (ou `assets/video/` para vídeo) e trocar o CSS correspondente, seguindo o padrão já documentado no `README.md`.

## Convenções de código

- CSS organizado em blocos comentados por seção (`/* === HERO === */` etc.) — manter esse padrão ao adicionar CSS novo.
- Motion/animação: usar `IntersectionObserver` para reveals on-scroll (já existe um `io` configurado) em vez de bibliotecas externas.
- **Não usar `prefers-reduced-motion`** para desativar animações — decisão explícita do usuário (2026-08-19): o site deve sempre animar (REC pulsante, faixa de skills etc.), mesmo para quem tem "reduzir animações" ativado no sistema.
- Mobile-first: sempre testar/ajustar breakpoints em `max-width: 720px–900px`.

## Tarefas pendentes conhecidas (backlog)

- [ ] Substituir todos os placeholders de imagem/vídeo pelo material real do usuário
- [ ] Adicionar favicon
- [ ] Revisar/ajustar copy do "Sobre" se o usuário pedir um tom diferente
- [ ] Opcional: 3D interativo (ex: Three.js + export `.glb` do Blender) na seção de skills, se o usuário quiser elevar ainda mais o "impacto" do site

## O que NÃO fazer sem confirmar com o usuário

- Não trocar a stack para um framework (Next.js, React, etc.)
- Não remover o seletor de idioma ou o timeline scrubber
- Não adicionar dependências pagas ou que exijam hospedagem além do GitHub Pages
