# Responsive flexbox & grid

## Partie 1 : Flexbox

### Entraînement

Pour se familiariser avec les différentes propriétés :
[Flexbox Froggy](https://flexboxfroggy.com/#fr)

### TP : à vous !

Le but de l'exercice est de reproduire une célèbre carte à jouer en utilisant les propriétés flexbox. Voici le modèle :

<img src="assets/models/card.jpg" width="300px">

#### Étape 0 : Configuration VSCode

- Créer un fork de ce repository
- Cloner le fork : le dossier `tp/pokemon` sera la racine de votre TP.
- Installer le plugin _Prettier_
  - Dans les options :
    - Cocher "Format on save"
    - Régler "Default formatter" sur "...prettier..."
  - Vérifier le bon fonctionnement sur les fichiers HTML et CSS (à la sauvegarde, le code est-il reformaté ?)
- Installer le plugin _Live Server_
  - Vérifier qu'un fichier HTML peut-être ouvert avec le bouton "Go Live" en bas à droite (auto-refresh du navigateur)

#### Étape 1 : Les fondations (HTML sauce BEM)

- Comprendre la méthodologie BEM : [ici](https://www.alticreation.com/bem-pour-le-css/) (français) ou [là](https://css-tricks.com/bem-101/)
- Déterminer quels sont les blocs constituant la carte (une demi-douzaine, selon le choix de découpage), et leur donner un nom simple
- Écrire le HTML correspondant, sans CSS pour le moment
  - Les images sont dans le dossier `assets/img`

Résultat approximatif à cette étape :

![](assets/models/html.png)

Attention à vérifier la présence de la balise _meta viewport_ pour un bon dimensionnement sur mobile !

```
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

- Solliciter une vérification de ma part, attendre la correction ou continuer si tout se passe bien !
- `git commit` avant de passer à la suite

#### Étape 2 : Styling SCSS

- Afin de pouvoir utiliser SCSS :
  - Dans le dossier de travail, transformer votre projet simple en projet npm avec `npm init`
  - Installer [parcel](https://parceljs.org/) avec `npm install parcel --save-dev`
  - Dans `package.json`, ajouter un script `"serve": "parcel index.html"`
  - Lancer `npm run serve`. Parcel _build_ votre site et l'ouvre dans le navigateur, sur _localhost_.
- Ajouter un fichier `styles.scss` à votre projet et l'importer à partir du HTML. Parcel s'occupera de la transformation en CSS.
- Ajouter un fichier `reset.scss` à votre projet contenant le [reset CSS classique](https://meyerweb.com/eric/tools/css/reset/), sans l'importer dans le HTML.
- Dans le fichier `styles.scss`, utiliser un import SASS pour importer le fichier `reset.scss`.

Dans vos projets, toujours inclure les deux règles CSS suivantes (rappel sur [box-sizing](https://developer.mozilla.org/fr/docs/Web/CSS/box-sizing)) :

```
* {
  box-sizing: border-box;
}

img {
  max-width: 100%;
}
```

Propriétés "interdites" pour cet exercice :

- `width`
- `height`
- `float`
- `position`
- `transform`
- `display` autre que `display: flex`

Votre but est maintenant de reproduire la carte sur un écran de type iPhone5 (320\*568). Il vous appartient de pousser la ressemblance avec l'original au maximum, mais voici un exemple :

![](assets/models/portrait.png)

- En accord avec la convention BEM :
  - Utilisez quasiment exclusivement des sélecteurs de classe
  - Évitez au maximum les imbrications. SASS sera utile, mais surtout pour la suite.
- Solliciter une vérification de ma part, attendre la correction ou continuer si tout se passe bien !
- `git commit` avant de passer à la suite

#### Étape 3 : Mode paysage

On souhaite adapter la carte à un mobile de la même taille en mode paysage (568\*320), autrement dit lorsque la largeur est plus grande que la hauteur.
Pour ce faire, vous pouvez ajouter une mixin SASS en début de fichier :

```
@mixin landscape {
  @media (min-aspect-ratio: 1/1) {
    @content;
  }
}
```

Grâce à cette mixin, vous pouvez écrire :

```
.selector {
  color: red;

  @include landscape {
    color: blue;
  }
}
```

Cela permet d'inclure les variations au plus proche du sélecteur de base, au lieu de tout écrire en fin de fichier, ce qui rend le code plus maintenable / lisible.

Voici le nouvel objectif à atteindre :

![](assets/models/landscape.png)

- Solliciter une vérification de ma part ou attendre la correction
- `git commit` pour finir

#### Étape 4 : Rendu

Rendez votre travail en créant une pull request de votre repository de travail vers ce repository.

## Partie 2 : Grid

Coming soon...

## Ressources

- En cas de besoin : [Exercices HTML/CSS](https://htmlcss.netlify.com/)
- [Méthode BEM](http://getbem.com/introduction/)

### Flexbox

- Reférence : [CSS Tricks Guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- Outil : [Flexulator, calculateur de flexbox](https://www.flexulator.com/)
- Entraînement : [Flexbox Froggy](https://flexboxfroggy.com/#fr)

### Grid

- Reférence : [CSS Tricks Guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- Outil : [Grid generator](https://grid.layoutit.com/)
- Entraînement [Grid Garden](https://cssgridgarden.com/#fr)
- Exemple : [grid-auto-flow: dense](https://codepen.io/imjuangarcia/pen/bzpYyj)
- Le futur [Subgrid](https://dev.to/kenbellows/why-we-need-css-subgrid-53mh)
