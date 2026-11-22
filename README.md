# Dans l'œil de Jo — site photo

Site statique Hugo, déployable sur Cloudflare Pages.

## Ajouter une série (le geste habituel)

```bash
hugo new series/ma-nouvelle-serie/index.md   # crée le dossier + frontmatter
# → déposer les JPG à côté de index.md (nommés 01.jpg, 02.jpg…)
# → remplir le frontmatter (title, number, cover, description), passer draft: false
git add content && git commit -m "nouvelle série" && git push
```

Cloudflare Pages rebuild et publie tout seul après le push.

## Commandes

```bash
hugo server -D          # prévisualiser en local (http://localhost:1313)
hugo --minify           # build statique → dossier public/
```

Binaire Hugo utilisé : v0.170.1 extended (nécessaire pour le traitement d'images/webp).

## Config Cloudflare Pages

- Build command : `hugo --minify`
- Output directory : `public`
- Variable d'environnement : `HUGO_VERSION=0.170.1`

## Structure

- `content/series/<nom>/` — 1 dossier = 1 série (photos + index.md)
- `layouts/series/single.html` — mise en page d'une série (galerie + lightbox)
- `layouts/index.html` — accueil (grille des séries)
- `assets/css/main.css` — tout le style (papier crème, Fraunces + IBM Plex Mono)

## TODO

- [ ] Remplacer les previews 640 px par les originaux (export Instagram)
- [ ] Connecter le remote GitHub `josephineaube` + Pages
- [ ] Domaine perso éventuel
