# Déploiement du Site sur GitHub Pages

## Configuration de GitHub Pages

1. Accédez aux paramètres de votre dépôt sur GitHub.
2. Sous l'onglet "Pages", configurez la source de build et de déploiement.

## Déploiement Automatique avec GitHub Actions

Assurez-vous d'avoir les droits read/write sur le dépôt GitHub pour les secrets dans settings > actions > general si vous avez une erreur 403.
Assurez-vous que le fichier `deploy.yml` inclut les étapes de déploiement :

```yaml
- name: Deploy to GitHub Pages
  uses: peaceiris/actions-gh-pages@v3
  with:
    github_token: ${{ secrets.GITHUB_TOKEN }}
    publish_dir: ./build
```
