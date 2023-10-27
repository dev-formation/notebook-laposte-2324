---
sidebar_position: 3
---

# Git : guide de survie

## Trio gagnant

```sh
git add .
git commit -m "message du commit"
git push
```

## Commandes de base

### Initialiser un repository git **LOCAL**

Si cela n'a pas déjà été fait vous pouvez créer un repository git local en utilisant la commande suivante, dans le terminal, à la racine de votre projet :

**Pas besoin de le faire pour Angular ou si vous avez cloné un repository git.**

```sh
git init
```

### Pour relier un repository git **LOCAL** à un repository git **DISTANT**

1. Créer un repository git **DISTANT** sur GitHub, puis récupérer son url.
2. Puis dans le terminal, à la racine de votre projet, exécuter la commande suivante :

```sh
git remote add origin <url_du_repository_distant>
```

### Pour supprimer le lien entre un repository git **DISTANT** et un repository git **LOCAL**

```sh
git remote remove origin
```

### Pour vérifier si un repo **LOCAL** git est lié à un repo **DISTANT**

```sh
git remote -v
```

### Pour ajouter des fichiers à l'index (staging area)

```sh
git add <nom_du_fichier>
```

### Pour ajouter tous les fichiers à l'index

```sh
git add .
```

### Pour créer un commit

```sh
git commit -m "message du commit"
```

### Pour envoyer les commits sur le repository distant

Pour le premier commit sur une branche :

```sh
git push -u origin <nom_de_la_branche>
```

ex: J'ai une branche main (locale) que je poussé sur la branche distante main :

```sh
git push -u origin main
```

puis ensuite plus besoin de préciser la branche :

```sh
git push
```

### Pour récupérer les commits du repository distant sans les fusionner (récupérer l'historique)

Normalement votre VS Code est configuré pour le faire automatiquement de manière périodique.

```sh
git fetch
```

### Pour récupérer les commits du repository distant et les fusionner avec votre branche locale

```sh
git pull
```

## Branches

### Pour créer une branche

```sh
git branch <nom_de_la_branche>
```

### Pour changer de branche

```sh
git checkout <nom_de_la_branche>
```

### Pour créer une branche et changer de branche

```sh
git checkout -b <nom_de_la_branche>
```

## Fusionner des branches

### Pour fusionner une branche dans la branche courante

```sh
git merge <nom_de_la_branche>
```

ex : pour fusionner la branche `feature/ma-nouvelle-fonctionnalite` dans la branche `main` :

```sh
git checkout main
git merge feature/ma-nouvelle-fonctionnalite
```

<div class="container-img-auto">
  <img
    src={require('./assets/explication-git-dark.png').default}
    alt="Les produits sont ajoutés à la liste"
  />
  <figcaption>Les produits sont ajoutés à la liste</figcaption>
</div>
