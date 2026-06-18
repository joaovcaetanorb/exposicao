# Guia de Personalização — Uma Pequena Exposição

---

## Passo 1 — Criar o repositório no GitHub e fazer o push

1. Acesse **github.com** e faça login
2. Clique em **New repository** (botão verde no canto superior direito)
3. Dê um nome ao repositório — sugestão: `exposicao`
4. Deixe como **Public** (necessário para o GitHub Pages gratuito)
5. **Não marque** nenhuma opção extra (sem README, sem .gitignore)
6. Clique em **Create repository**
7. O GitHub vai exibir a URL do seu repo, algo como:
   ```
   https://github.com/SEU_USUARIO/exposicao.git
   ```
8. Abra o terminal na pasta `gam` e rode os 3 comandos abaixo:
   ```bash
   git remote add origin https://github.com/SEU_USUARIO/exposicao.git
   git branch -M main
   git push -u origin main
   ```

---

## Passo 2 — Ativar o GitHub Pages (URL grátis e permanente)

1. No repositório → clique em **Settings**
2. No menu lateral esquerdo, clique em **Pages**
3. Em **Source**, selecione **Deploy from a branch**
4. Branch: **main** — Pasta: **/ (root)**
5. Clique em **Save**
6. Aguarde cerca de 1 minuto
7. O site vai estar disponível em:
   ```
   https://SEU_USUARIO.github.io/exposicao/
   ```
   Essa URL **nunca expira** enquanto o repositório existir.

---

## Passo 3 — Gerar o QR Code que não expira

1. Acesse **qr-code-generator.com** ou **qrcode.me**
2. Cole a URL do GitHub Pages
3. Gere o QR Code
4. Baixe como **SVG** (melhor para imprimir sem perder qualidade) ou **PNG**

> O QR code não tem prazo de validade — ele é só uma imagem que aponta para a URL. Enquanto o repositório existir, o QR funciona.

---

## Passo 4 — Personalizar o nome dela (e o seu)

Abra o arquivo `index.html` em qualquer editor de texto (Bloco de Notas, VS Code, etc.) e use **Ctrl + H** para localizar e substituir:

| Encontrar | Substituir por |
|---|---|
| `[Nome dela]` | O nome real dela — ex: `Ana` |
| `[Seu nome]` | Seu nome (aparece na assinatura da carta) |

---

## Passo 5 — Adicionar fotos reais

Primeiro, crie uma pasta chamada `fotos` dentro da pasta `gam` e coloque todas as imagens lá.

### Hero (carrossel — 5 slides)

Cada slide tem uma `<div class="slide-bg">`. Adicione a foto via `style`:

```html
<div class="slide s1 active">
  <div class="slide-bg" style="background-image:url('fotos/foto1.jpg');background-size:cover;background-position:center"></div>
</div>
```

Faça o mesmo para `s2`, `s3`, `s4`, `s5` com fotos diferentes.

---

### Sobre ela — foto principal (retrato grande)

Procure por `<!-- <img src="foto-principal.jpg" alt=""> -->` e substitua:

```html
<div class="about-img-main">
  <img src="fotos/principal.jpg" alt="">
  <span class="about-img-tag">© [Nome dela]</span>
</div>
```

---

### Sobre ela — duas fotos pequenas

Logo abaixo, procure pelos dois `<div class="about-img-sm">` e adicione as imagens:

```html
<div class="about-img-sm"><img src="fotos/pequena1.jpg" alt=""></div>
<div class="about-img-sm"><img src="fotos/pequena2.jpg" alt=""></div>
```

---

### Galeria (8 fotos)

Cada item da galeria tem um `<div class="gal-bg">`. Substitua pelo `<img>`:

```html
<div class="gal-item rv">
  <img src="fotos/galeria1.jpg" alt="" style="position:absolute;inset:0;width:100%;height:100%;object-fit:cover;filter:grayscale(15%)">
  <div class="gal-overlay"></div>
</div>
```

Repita para os 8 itens, trocando o nome do arquivo.

---

## Passo 6 — Editar os traços dela (seção "Sobre ela")

Procure no HTML por `<div class="traits">` e edite os textos:

```html
<div class="trait"><span class="trait-inner">Fotógrafa.</span></div>
<div class="trait"><span class="trait-inner">Estudante de medicina.</span></div>
<div class="trait"><span class="trait-inner">Amante de gatos.</span></div>
<div class="trait"><span class="trait-inner">Colecionadora de momentos.</span></div>
<div class="trait"><span class="trait-inner">Sonhadora de plantão.</span></div>
```

---

## Passo 7 — Editar os cards de admiração

Procure por `<div class="admire-grid">` e edite os textos dentro de cada `<p class="card-text">`:

```html
<p class="card-text">Sua risada que aparece do nada.</p>
<p class="card-text">A forma como você ouve as pessoas.</p>
<p class="card-text">Seu gosto musical absurdo.</p>
```

---

## Passo 8 — Adicionar a playlist do Spotify

1. No Spotify (app ou web) → abra sua playlist
2. Clique em **···** → **Compartilhar** → **Incorporar playlist**
3. Copie o código `<iframe ...>` que aparecer
4. No `index.html`, procure por `<div class="spotify-ph rv">` e **substitua o bloco inteiro** pelo iframe:

```html
<iframe style="border-radius:0"
  src="https://open.spotify.com/embed/playlist/SEU_ID_AQUI"
  width="100%" height="352" frameBorder="0"
  allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
  loading="lazy">
</iframe>
```

---

## Passo 9 — Editar a carta

Procure por `<div class="letter-body">` e edite os parágrafos `<p>` com o que você quiser escrever.

A data aparece na linha `<span class="letter-date">` logo acima.

---

## Passo 10 — Enviar as alterações pro GitHub

Depois de qualquer alteração feita em casa, rode no terminal dentro da pasta `gam`:

```bash
git add .
git commit -m "Adiciona fotos e personaliza conteudo"
git push
```

O site atualiza automaticamente em menos de 1 minuto no GitHub Pages.

---

## Dica final — Testar localmente antes de enviar

Basta abrir o arquivo `index.html` direto no navegador (clique duplo nele).  
Tudo funciona offline, exceto o embed do Spotify (que precisa de internet).
