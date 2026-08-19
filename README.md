# Portfólio — Gustavo Vecchiatti Aguiar

Site estático em HTML/CSS/JS puro, pronto para o **GitHub Pages** (sem custo de hospedagem).

## O que tem aqui

- `index.html` — o site inteiro (HTML + CSS + JS no mesmo arquivo, para simplificar)
- `assets/images/` — coloque suas fotos aqui
- `assets/video/` — coloque seus vídeos aqui
- `assets/models/` — se quiser exportar algo do Blender para a web (ex: `.glb`), coloque aqui

## Recursos já implementados

- Efeito **parallax** no hero (palavras flutuando em profundidades diferentes ao rolar)
- **Animações de entrada** (reveal on scroll) em todas as seções
- **"Timeline scrubber"** fixo no topo — uma barra de progresso de rolagem no estilo linha do tempo de edição de vídeo, com timecode animado (referência direta ao seu trabalho como editor/motion designer)
- Seletor de idioma **PT / EN** (clique em "PT" ou "EN" no topo direito) — todo o texto do site troca dinamicamente
- Seção "Áreas de Atuação" com **marquee** (letreiro rolante) de palavras-chave, bom para impacto visual e para SEO
- Totalmente **responsivo** (celular, tablet, desktop)
- Respeita `prefers-reduced-motion` (acessibilidade)

## Como adicionar suas imagens/vídeos

Neste momento os blocos de projeto (`.thumb`) e o retrato (`.portrait`) são placeholders com gradiente.
Para trocar por imagens reais, edite o CSS de cada elemento, por exemplo:

```css
.project:nth-child(1) .thumb{
  background:url('assets/images/sintegra-3d-01.jpg') center/cover;
}
#about .portrait{
  background:url('assets/images/portrait.jpg') center/cover;
}
```

Para vídeo de fundo em algum projeto, substitua a `div.thumb` por:
```html
<video class="thumb" src="assets/video/projeto.mp4" autoplay muted loop playsinline></video>
```

## Como publicar no GitHub Pages (passo a passo)

1. Crie um repositório novo no GitHub, por exemplo `gustavo-portfolio` (pode ser público, é grátis).
2. No seu computador, dentro desta pasta, rode:
   ```bash
   git init
   git add .
   git commit -m "primeiro deploy do portfólio"
   git branch -M main
   git remote add origin https://github.com/SEU-USUARIO/gustavo-portfolio.git
   git push -u origin main
   ```
3. No GitHub, vá em **Settings → Pages**.
4. Em "Source", selecione a branch `main` e a pasta `/ (root)`.
5. Salve. Em alguns minutos o site estará em:
   `https://SEU-USUARIO.github.io/gustavo-portfolio/`

## Se comprar um domínio próprio depois

1. Compre o domínio (Registro.br, Namecheap, Google Domains, etc.).
2. No repositório, crie um arquivo chamado `CNAME` (sem extensão) na raiz, contendo apenas o domínio, ex:
   ```
   gustavovecchiatti.com
   ```
3. No painel do seu provedor de domínio, aponte um registro **CNAME** para `SEU-USUARIO.github.io`.
4. Em **Settings → Pages** no GitHub, adicione o domínio customizado no campo indicado — o GitHub cuida do HTTPS automaticamente.

## Próximos passos sugeridos

- Trocar todos os placeholders de imagem/vídeo pelo seu material real
- Ajustar os textos de "Sobre" se quiser um tom diferente
- Adicionar um favicon (ícone na aba do navegador)
- Opcional: registrar o site no Google Search Console para indexação mais rápida
