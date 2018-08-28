
KSS
===============================================================================

[KSS](http://warpspire.com/kss/) est une convention de documentation pour les feuilles de styles. Elle permet de structurer les commentaires afin de générer
un guide complet des styles du projet.

Il existe plusieurs outils capable de lire les commentaires pour générer un guide des styles. Nous utilisons ici [kss-node](http://kss-node.github.io/kss-node/).


Générez un guide des styles
===============================================================================

Les commentaire doivent être mis dans les partials css sous cette forme :

/// Exemple de commentaire
//
// Si vous commentez votre code en utilisant la syntaxe
// [KSS](https://github.com/kss-node/kss/blob/spec/SPEC.md),
// le Starter Kit generera un guide des styles dans la
// documentation a chaque build du projet.
//
// Styleguide Introduction

/// Une palette de couleur
//
// Si vous voulez documenter des couleurs, vous pouvez
// le faire de cette manière grace au block Colors.
//
// Colors:
// denim          : #1e5bc6
// flamingo       : #f15145
// alert          : #f33121 - red for error
// $color-black   : #000    - real black
//
// Styleguide Introduction.Couleur

/// Font d’icon Fontello
//
// De la même façon que pour les fonts grâce au block
// Icons vous pouvez documenter les icons de la font.
//
// Implique que la font d’icon se nomme fontello
// Sinon il faut changer celle-ci dans doc.scss
//
// Icons:
// left    : ←
// up      : ↑
// right   : →
// down    : ↓
// comment : 💬 - bulle
//
// Styleguide Introduction.Icons

/// Exemple UI
//
// Markup: ../html/partials/_exemple.twig
//
// Styleguide Introduction.UI

/// SVG
//
// Markup:
// <svg style="height:120px;width:120px;fill:#000">
//   <use xlink:href="#symbol-fish"/>
// </svg>
//
// Styleguide Introduction.Svg


Configuration
-------------------------------------------------------------------------------

Toute la configuration pour la génération du guide des styles est centralisée dans le fichier `kss.json`.

```javascript
{
  // Le dossier comportant les sources à analyser
  // (le chemin est relatif à l'emplacement du fichier kss.json)
  "source": "./src/sass",

  // La page d'accueil statique du guide des style au format Markdown
  // (le chemin est relatif à l'emplacement des sources à analyser)
  "homepage": "styleguide.md",

  // L'emplacement ou le guide des style sera généré
  // (le chemin est relatif à l'emplacement du fichier kss.json)
  "destination": "./build/docs/styleguide",

  // L'emplacement du gabarit KSS personalisé à utiliser
  // (le chemin est relatif à l'emplacement du fichier kss.json)
  "template": "./.gsk/kss",

  // Les divers fichiers CSS à inclure dans le template
  // (leur chemin est l'URL relative des fichiers et dépend donc de la
  //  configuration du serveur HTTP utilisé pour afficher la documentation)
  "css": [
    "../../css/doc.css",
    "../../css/styles.css"
  ]
}
```
