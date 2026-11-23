# Joséphine Aubé — site photo

Site statique Hugo, déployé sur Cloudflare Pages (<https://josephine-dht.pages.dev>).

## Structure

- `content/series/<slug>/` — 1 dossier = 1 publication (photos `01.jpg`… + `index.md`)
- `static/thumbs/<slug>/` — vignettes WebP 760 px générées hors ligne (le build Hugo ne retouche aucune image)
- `layouts/series/single.html` — page publication (galerie maçonnée + lightbox)
- `layouts/series/list.html` — archive groupée par année
- `layouts/partials/logo.html` — médaillon SVG (anneau + lettrage en arc + `static/logo-mark.webp`)
- `assets/css/main.css` — tout le style (papier crème, Fraunces + IBM Plex Mono)

## Ajouter une publication

```bash
hugo new series/ma-publication/index.md   # crée le dossier + frontmatter
# → déposer les JPG à côté de index.md (01.jpg, 02.jpg…)
# → générer les vignettes : static/thumbs/ma-publication/01.webp…
# → mettre à jour `photos: N` dans le frontmatter, passer draft: false
git add content static && git commit -m "nouvelle publication" && git push
```

Cloudflare Pages rebuild et publie automatiquement après le push.

## Commandes

```bash
hugo server              # prévisualiser en local (http://localhost:1313)
hugo --minify            # build statique → public/
```

Binaire Hugo : v0.170.1 extended (`%LOCALAPPDATA%/hermes/bin/hugo.exe`).

## Config Cloudflare Pages

- Projet `josephine`, dépôt `josephineaube/JOJO`
- Build command : `hugo --minify` — Output directory : `public`
- Variable d'environnement de **premier niveau** : `HUGO_VERSION=0.170.1`

## Conventions de contenu

- `number` (01…43) et `weight` = ordre chronologique (1 = la plus ancienne)
- `lieu`, `appareil`, `pellicule`, `photos` alimentent les métadonnées affichées sous chaque titre
- `tags` = hashtags d'origine, affichés en pastilles sur la page publication
