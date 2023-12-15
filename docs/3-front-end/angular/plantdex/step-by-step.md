---
sidebar_position: 1
---

# Step by Step

## Création du projet

```bash title=Terminal
ng new plantdex
```

On choisit d'ajouter Angular Routing et CSS.

## Ajout de Bootstrap

```bash title=Terminal
  npm install bootstrap
```

On ajoute le fichier `bootstrap.min.css` et `bootstrap.bundle.min.js` dans le fichier `angular.json` :

```json title=angular.json
"styles": [
  "node_modules/bootstrap/dist/css/bootstrap.min.css",
  "src/styles.css"
],
"scripts": [
  "node_modules/bootstrap/dist/js/bootstrap.bundle.min.js"
]
```

Cela permettra à Angular d'intégrer les différents fichiers dans notre projet pour pouvoir utiliser les classes de Bootstrap.

:::caution
Il faut redémarrer le serveur pour que les changements soient pris en compte, dès lors que des changements sont fait dans le fichier `angular.json`.
:::

:::info
On pense à faire notre premier commit ! avec le message : `0 - install et config de bootstrap`
:::

## Planning

<div class="container-img-100">
  <img
    src={require('!!url-loader!./assets/plantdex-step-by-step.svg').default}
    alt="Planning complet"
  />
</div>

## Partie 1 : Mise en place de la navbar

<div class="container-img-100">
  <img
    src={require('!!url-loader!./assets/plantdex-step-1.svg').default}
    alt="Planning complet"
  />
</div>

### Création du composant navbar

Afin de rester organisé, on va créer un dossier `components` dans le dossier `app` et on va y créer un composant `navbar` :

```bash title=Terminal
ng g c components/navbar
```

On va ensuite ajouter le composant dans le fichier `app.component.html` :

```html title=app.component.html
<app-navbar></app-navbar>

<router-outlet></router-outlet>
```

### Ajout du template de la navbar

Pour rester concentrer sur l'apprentissage d'Angular, on va utiliser un template de navbar déjà existant. On va utiliser celui de [Bootstrap](https://getbootstrap.com/docs/5.3/components/navbar/#nav).

Directement le template de la navbar dans le fichier `navbar.component.html` :

```html title=navbar.component.html
<nav class="navbar navbar-expand-lg bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">🪴 Plantdex</a>
    <button
      class="navbar-toggler"
      type="button"
      data-bs-toggle="collapse"
      data-bs-target="#navbarNav"
      aria-controls="navbarNav"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">Accueil</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Mes plantes</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Espace Admin</a>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled">A venir...</a>
        </li>
      </ul>
    </div>
  </div>
</nav>
```

:::tip 💻 Exercice
Chercher comment ajouter une ombre à la navbar à l'aide d'une classe de Bootstrap.

**Indice** : aller voir dans la documentation dans la partie `Utilities`.
:::

:::info
On pense à faire notre commit ! avec le message : `1 - barre de navigation`
:::

## Partie 2 : Création des pages

<div class="container-img-100">
  <img
    src={require('!!url-loader!./assets/plantdex-step-2.svg').default}
    alt="Planning complet"
  />
</div>

### Création des composants

On va créer un dossier `pages` dans le dossier `app` et on va y créer les composants suivants :

```bash title=Terminal
ng g c pages/page-home
ng g c pages/page-my-plants
ng g c pages/page-admin
ng g c pages/page-not-found
```

:::info
On pense à faire notre commit ! avec le message : `2 - creation des pages`
:::

## Partie 3 : Mise en place du routing

<div class="container-img-100">
  <img
    src={require('!!url-loader!./assets/plantdex-step-3.svg').default}
    alt="Planning complet"
  />
</div>

### Mise à jour du fichier `app-routing.module.ts`

On va ajouter les routes suivantes :

- `/` : Page d'accueil
- `/my-plants` : Page mes plantes
- `/admin` : Page admin

```ts title=app-routing.module.ts
import { NgModule } from "@angular/core";
import { RouterModule, Routes } from "@angular/router";
import { PageAdminComponent } from "./pages/page-admin/page-admin.component";
import { PageHomeComponent } from "./pages/page-home/page-home.component";
import { PageMyPlantsComponent } from "./pages/page-my-plants/page-my-plants.component";
import { PageNotFoundComponent } from "./pages/page-not-found/page-not-found.component";

const routes: Routes = [
  { path: "", component: PageHomeComponent },
  { path: "my-plants", component: PageMyPlantsComponent },
  { path: "admin", component: PageAdminComponent },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule],
})
export class AppRoutingModule {}
```

Chaque route permettra d'afficher un composant différent en fonction de l'url de l'application à l'endroit de la balise <br/> `<router-outlet></router-outlet>`.

:::info
On pense à faire notre commit ! avec le message : `3 - routing principal`
:::

### Ajout de la page 404

Nous allons ajouter une page 404 qui sera affichée si aucune route n'est trouvée.

Pour pouvoir faire l'exercice, il faut mettre en place une branch à partir de la branche main :

```bash title=Terminal
git checkout -b 404
```

:::tip 💻 Exercice
Ajouter la route pour la page 404.
Il faut rechercher dans la documentation comment faire.
La règle que nous devons mettre en place est une route spécifique qui sera utilisée si aucune autre route n'est trouvée.
:::

Pour la correction on repasse sur la branche main :

```bash title=Terminal
git checkout main
```

<!--
<details>
  <summary>Correction</summary>

```ts title=app-routing.module.ts
import { NgModule } from "@angular/core";
import { RouterModule, Routes } from "@angular/router";
import { PageAdminComponent } from "./pages/page-admin/page-admin.component";
import { PageHomeComponent } from "./pages/page-home/page-home.component";
import { PageMyPlantsComponent } from "./pages/page-my-plants/page-my-plants.component";
import { PageNotFoundComponent } from "./pages/page-not-found/page-not-found.component";

const routes: Routes = [
  { path: "", component: PageHomeComponent },
  { path: "my-plants", component: PageMyPlantsComponent },
  { path: "admin", component: PageAdminComponent },
  { path: "**", component: PageNotFoundComponent },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule],
})
export class AppRoutingModule {}
```

</details> -->

:::info
On pense à faire notre commit ! avec le message : `3.1 - correction route page not found`
:::

### Défi: Implémentation de la page 404

:::tip 💻 Exercice
Créer la page 404 en utilisant le composant `PageNotFoundComponent`.

Pour ton inspiration voici une image de la page 404 de notre application :
tu peux aller chercher sur ce site : https://zenuacademie.com/site-internet/exemples-pages-erreur-404/
:::

## Partie 4 : Afficher des plantes grâce à un service

<div class="container-img-100">
  <img
    src={require('!!url-loader!./assets/plantdex-step-4.svg').default}
    alt="Planning complet"
  />
</div>

### Comment simuler une API ?

Pour simuler une API, on va faire une recherche sur le package `json-server` qui va nous permettre de créer une API à partir d'un fichier JSON.

[📂 Télécharger la fausse base de données](./assets/fausse_BDD_plantdex.zip)

:::tip 💻 Exercice
En groupe de 2, vous allez devoir mettre en place une API à partir du fichier JSON fourni.
**Bien lire la documentation** : https://www.npmjs.com/package/json-server
:::

### Création du modèle

On va créer un modèle `Plant` qui va nous permettre de représenter une plante.

```bash title=Terminal
ng g interface models/plant
```

### Mise à jour du modèle

On va ajouter les propriétés suivantes :

- `id` : number
- `nom` : string
- `soleil` : string
- `arrosage` : number
- `categorie` : string
- `image` : string

```ts title=plant.ts
export interface Plant {
  id: number;
  nom: string;
  soleil: string;
  arrosage: number;
  categorie: string;
  image: string;
}
```

### Création du service

On va créer un service qui va nous permettre de récupérer des plantes. On le met dans un dossier `services`.

```bash title=Terminal
ng g service services/plants
```

### Mise à jour du service

On va ajouter une méthode `getPlants()` qui va nous permettre de récupérer des plantes.

```ts title=plant.service.ts
import { Injectable } from "@angular/core";
export class PlantsService {
  constructor() {}

  getPlants() {}
}
```

Comme on va utiliser une API (même si elle est simuler), on va utiliser le module `HttpClientModule` qui va nous permettre de faire des requêtes HTTP.

```ts title=angular.module.ts
/* . . . */
import { HttpClientModule } from '@angular/common/http';
/* . . . */

@NgModule({
  /* . . . */
  imports: [BrowserModule, AppRoutingModule, HttpClientModule],
  /* . . . */
})

```

On va injecter le service `HttpClient` dans notre service `PlantsService`.

```ts title=plant.service.ts
/* . . . */
import { HttpClient } from "@angular/common/http";
import { Observable } from "rxjs";
/* . . . */

export class PlantsService {
  constructor(private http: HttpClient) {}

  getPlants(): Observable<Plant[]> {
    return this.http.get<Plant[]>("http://localhost:3000/plants");
  }
}
```

Il faut garder en tête que le rôle de notre service est d'assurer la communication avec notre API. Il nous met à disposition une méthode `getPlants()` qui va nous permettre de récupérer des plantes via une requête http.

### Mise à jour du composant `PageHomeComponent`

On va injecter le service `PlantsService` dans le composant `PageHomeComponent`.

```ts title=page-home.component.ts
/* . . . */
import { PlantsService } from "../../services/plants.service";
/* . . . */

export class PageHomeComponent implements OnInit {
  plantsToDisplay: Plant[] = [];

  constructor(private plantsService: PlantsService) {}
  /* . . . */

  ngOnInit(): void {
    this.plantsService.getPlants().subscribe((plants) => {
      this.plantsToDisplay = plants;
      console.log(this.plantsToDisplay);
    });
  }
}
```

On a utilisé la méthode `getPlants()` de notre service `PlantsService` pour récupérer des plantes. On a utilisé la méthode `subscribe()` pour pouvoir récupérer les plantes.

### Mise à jour du template `PageHomeComponent`

On va afficher les plantes dans le template `PageHomeComponent`.

```html title=page-home.component.html
<div class="container">
  <h1 class="title">Plantdex</h1>
  <div class="container-plants">
    <ul>
      <li *ngFor="let plant of plantsToDisplay">{{ plant.nom }}</li>
    </ul>
  </div>
</div>
```

:::info
On pense à faire notre commit ! avec le message : `4 - affichage plant + service`
:::

## Partie 5 : Plant card et communication entre composants

<div class="container-img-100">
  <img
    src={require('!!url-loader!./assets/plantdex-step-5.svg').default}
    alt="Planning complet"
  />
</div>

Dans cette partie, on va créer deux composants :

- un composant `PlantListComponent` qui va nous permettre d'afficher une liste de plantes
- un composant `CardComponent` qui va nous permettre d'afficher une plante

Le composant `CardComponent` sera un composant enfant du composant `PlantListComponent`.

### Création du composant `PlantListComponent`

```bash title=Terminal
ng g c components/plant-list
```

### Mise à jour du composant `PlantListComponent`

```ts title=plant-list.component.ts
import { Component, Input, OnInit } from "@angular/core";
import { Plant } from "../../models/plant";

@Component({
  selector: "app-plant-list",
  templateUrl: "./plant-list.component.html",
  styleUrls: ["./plant-list.component.css"],
})
export class PlantListComponent implements OnInit {
  @Input() plantsRecupDeLaHome!: Plant[];

  constructor() {}

  ngOnInit(): void {}
}
```

### Mise à jour du template `PlantListComponent`

```html title=plant-list.component.html
<div class="container-plants">
  <ul>
    <li *ngFor="let plant of plantsRecupDeLaHome">{{ plant.nom }}</li>
  </ul>
</div>
```

### Mise à jour du composant `PageHomeComponent`

```html title=page-home.component.html
<div class="container">
  <h1 class="title">Plantdex</h1>
  <app-plant-list [plantsRecupDeLaHome]="plantsToDisplay"></app-plant-list>
</div>
```

:::info
Pour le moment nous avons refactorisé notre code, pour que les plantes s'affiche mais via notre composant `PlantListComponent`. On a utilisé la communication entre composants pour passer les plantes de notre composant `PageHomeComponent` à notre composant `PlantListComponent`.
:::

### Création du composant `CardComponent`

On passe sur une seconde phase de reafactoring, on va créer un composant `CardComponent` qui va nous permettre d'afficher une plante d'une manière bien plus interressante qu'avec une simple liste `<ul>`.

```bash title=Terminal
ng g c components/card
```

### Mise à jour du composant `CardComponent`

```ts title=card.component.ts
import { Component, Input, OnInit } from "@angular/core";
import { Plant } from "src/app/models/plant";

@Component({
  selector: "app-card",
  templateUrl: "./card.component.html",
  styleUrls: ["./card.component.css"],
})
export class CardComponent implements OnInit {
  @Input() unePlanteAAfficher!: Plant;

  constructor() {}

  ngOnInit(): void {}
}
```

### Mise à jour du template `CardComponent`

```html title=card.component.html
<div class="card" style="width: 18rem">
  <img
    class="card-img-top"
    src="{{ unePlanteAAfficher.image }}"
    alt="Card image cap"
  />
  <div class="card-body">
    <h5 class="card-title">{{ unePlanteAAfficher.nom }}</h5>
    <p class="card-text">{{ unePlanteAAfficher.categorie }}</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div>
```

### Mise à jour du composant `PlantListComponent`

```html title=plant-list.component.html
<div class="container-plants">
  <div class="row">
    <div class="col-4" *ngFor="let plant of plantsRecupDeLaHome">
      <app-card [unePlanteAAfficher]="plant"></app-card>
    </div>
  </div>
</div>
```

### Mise à jour du style `CardComponent`

```css title=card.component.css
.container-plants {
  display: flex;
  flex-wrap: wrap;
}
```

:::info
On pense à faire notre commit ! avec le message : `5 - plant card + communication parent enfant`
:::

<!-- ## Partie 6 : Mise en place du filtre par catégories

<div class="container-img-100">
  <img
    src={require('!!url-loader!./assets/plantdex-step-6.svg').default}
    alt="Planning complet"
  />
</div>

### Création du composant `SideBarComponent`

```bash title=Terminal
ng g c components/side-bar
```

### Mise à jour du composant `SideBarComponent`

```ts title=side-bar.component.ts
import { Component, EventEmitter, OnInit, Output } from "@angular/core";

@Component({
  selector: "app-side-bar",
  templateUrl: "./side-bar.component.html",
  styleUrls: ["./side-bar.component.css"],
})
export class SideBarComponent implements OnInit {
  @Input() categoriesRecupDeLaHome!: string[];

  constructor() {}

  ngOnInit(): void {}
}
```

### Mise à jour du template `SideBarComponent`

```html title=side-bar.component.html
<div class="custom-side-bar border-end">
  <div class="p-3">
    <span class="fs-5 fw-semibold">Filtres</span>
  </div>
  <hr />
  <div class="px-3">
    <p class="fs-5 fw-semibold">Catégories</p>
    <div class="form-check" *ngFor="let categorie of categoriesRecupDeLaHome">
      <input
        class="form-check-input"
        type="checkbox"
        value="{{ categorie }}"
        id="{{ categorie }}"
      />
      <label class="form-check-label" for="{{ categorie }}">
        {{ categorie }}
      </label>
    </div>
  </div>
</div>
```

Dans un premier on cherche simplement à afficher les catégories de nos plantes, pour cela on va utiliser la directive `*ngFor` pour générer une liste de checkbox.

### Mise à jour du style `SideBarComponent`

```css title=side-bar.component.css
.custom-side-bar {
  height: calc(100vh - 56px);
  width: 17rem;
  position: sticky;
  top: 56px;
}
```

### Mise à jour du composant `PageHomeComponent`

```html title=page-home.component.html
<div id="flexIt">
  <app-side-bar [categoriesRecupDeLaHome]="categories"></app-side-bar>
  <app-plant-list [plantsRecupDeLaHome]="plantsToDisplay"></app-plant-list>
</div>
```

### Mise à jour du composant `SideBarComponent`

Une fois que nos différents composants sont en places il va falloir implémenter la logique pour que le filtre fonctionne. On commence dans notre enfant, `SideBarComponent` et nous allons chercher à constituer un tableau contenant les catégories cochées par l'utilisateur en prenant en compte ces quelques règles :

- Si l'utilisateur coche une catégorie, on l'ajoute au tableau
- Si l'utilisateur décoche une catégorie, on la retire du tableau
- Si l'utilisateur décoche toutes les catégories, on affiche toutes les plantes (donc le tableau contient toutes les catégories)

```ts title=side-bar.component.ts
import { Component, Input } from "@angular/core";

@Component({
  selector: "app-side-bar",
  templateUrl: "./side-bar.component.html",
  styleUrls: ["./side-bar.component.css"],
})
export class SideBarComponent {
  @Input() categoriesRecupDeLaHome!: string[];
  checkedCategorie: string[] = [];

  onCheckCategory(e: Event) {
    const target = e.target as HTMLInputElement;
    console.log("Valeur de la checkbox", target.value);
    console.log("Est elle cochée ? : ", target.checked);

    if (target.checked) {
      if (
        this.checkedCategorie.length === this.categoriesRecupDeLaHome.length
      ) {
        this.checkedCategorie = [];
      }
      this.checkedCategorie.push(target.value);
    } else {
      this.checkedCategorie = this.checkedCategorie.filter(
        (x) => x != target.value
      );
    }

    if (this.checkedCategorie.length === 0) {
      this.checkedCategorie = [...this.categoriesRecupDeLaHome];
    }
    console.log(this.checkedCategorie);
  }
}
```

:::tip 💻 Exercice
Une fois que notre tableau de catégories est prêt, il faut maintenant le transmettre à notre parent `PageHomeComponent` pour qu'il puisse filtrer les plantes à afficher.
A vous de mettre en place le code nécessaire pour que le parent puisse récupérer le tableau de catégories.
:::

Une fois cela fait on va pouvoir mettre en place la logique de filtrage dans notre parent `PageHomeComponent`.

Nous allons devoir nous interresser à la méthode `filter` des `Array` de JavaScript.

Voici un exemple d'utilisation :

```ts
const tableauDeNombres = [1, 2, 3, 4, 5, 6, 7, 8, 9];

const tableauDeNombresPairs = tableauDeNombres.filter((x) => x % 2 === 0);

console.log(tableauDeNombresPairs); // [2, 4, 6, 8]
```

:::tip 💻 Exercice
[Exercice Stackblitz sur les filtres](https://stackblitz.com/edit/angular-ivy-yg4n8q?file=src%2Fapp%2Fpages%2Fpage-home%2Fpage-home.component.ts,src%2Fapp%2Fpages%2Fpage-home%2Fpage-home.component.html)
:::

:::info
On pense à faire notre commit ! avec le message : `6 - filtre par categorie + install underscore.js`
:::

<!--## Partie 7 : Pouvoir rechercher et trier nos plantes

<div class="container-img-100">
  <img
    src={require('!!url-loader!./assets/plantdex-step-7.svg').default}
    alt="Planning complet"
  />
</div>

:::info
On pense à faire notre commit ! avec le message : `7 - barre de recherche + tri`
:::
-->
