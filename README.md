# Notebook SNCF P3

## Introduction

Ce notebook permet de retrouver toutes les ressources concernant la formation DWWM du dispositif UpToDev de la SNCF.

## Informations techniques

Ce site est construit avec [Docusaurus 2](https://docusaurus.io/), un générateur de site statique moderne.

### Plugins

Pour la recherche nous avons utiliser le plugin suivant :
[docusaurus-lunr-search](https://github.com/praveenn77/docusaurus-lunr-search)

### Installation

```
$ npm install
```

### Local Development

```
$ npm start
```

Cette commande démarre un serveur de développement local et ouvre une fenêtre de navigateur. La plupart des modifications sont reflétées en direct sans avoir à redémarrer le serveur.

### Build

```
$ npm run build
```

Cette commande génère du contenu statique dans le répertoire `build` et peut être servi en utilisant n'importe quel service d'hébergement de contenu statique.

### Déploiement

Sans utiliser SSH:

```
$ GIT_USER=<Your GitHub username> yarn deploy
```

Si vous utilisez GitHub pages pour l'hébergement, cette commande est un moyen pratique de construire le site et de le pousser vers la branche `gh-pages`.
