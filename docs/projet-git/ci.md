# Configuration de l'Intégration Continue (CI) avec GitHub Actions

## Prérequis

- Un dépôt GitHub
- Accès à GitHub Actions

## Création du Workflow CI

Créez un fichier `deploy.yml` dans `.github/workflows` :

```yaml
name: Deploy Docusaurus site

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Use Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '18'

      - name: Install dependencies
        run:  npm install

      - name: Build
        run: npm run build

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./build
```

1. Bien pensez à mettre la branche correcte dans settings > pages.

2. Bien pensez à mettre les droits read/write sur le dépôt GitHub pour les secrets dans settings > actions > general.
