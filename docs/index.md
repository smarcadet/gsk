Documentation
===============================================================================

Ce dépôt contient les maquettes sous forme d’intégration statique ainsi que la documentation et les outils nécessaires à la conception frontend du projet.

Ce dépôt est basé sur le [Garden Starter Kit](https://github.com/cleverage/garden-starter-kit).

Chaque outil du GSK dispose d’une documentation dédiée sur la façon de
l’utiliser dans notre contexte. Cette documentation est rédigée au [format
Markdown](https://daringfireball.net/projects/markdown/syntax) et est disponible dans le répertoire `.gsk/docs` de ce dépôt.


Prérequis
-------------------------------------------------------------------------------

Ce projet nécessite que votre environnement dispose de tous les outils suivants installés au niveau global sur votre machine :

* [Git](http://git-scm.com/)
* [NodeJS](http://nodejs.org/)

Afin de pouvoir utiliser facilement les commandes fournies par npm (notamment _gulp_), installées
dans votre répertoire projet (dans le dossier `node_modules`), plusieurs méthodes existent.

### Solution 1 : ajout au PATH

La plus simple est d'ajouter le répertoire `./node_modules/.bin` a votre `PATH`, mais suivant votre environnement, vous aurez peut-être besoin de le faire pour chaque projet.

Pour Mac/Linux, rajouter la ligne suivante dans votre fichier `~/.profile`
(Mac), `~/.bash_rc` (Linux) ou tout autre fichier de configuration
correspondant à votre shell, pour que le changement soit effectif à chaque
lancement de votre terminal.

```sh
export PATH="./node_modules/.bin:$PATH"
```

Vous pourrez alors lancer directement depuis votre terminal les commandes :

```
$ gulp live
```

### Solution 2 : méthode dédiée

Une autre solution valable d’un projet à l’autre est de définir une fonction dédiée dans votre _profile_ de terminal qui ira à chaque fois lancer les commandes inhérentes au projet en cours.

Pour Mac/Linux, rajouter la fonction suivante dans votre fichier `~/.profile`
(Mac), `~/.bash_rc` (Linux) ou tout autre fichier de configuration
correspondant à votre shell, pour que le changement soit effectif à chaque
lancement de votre terminal.

```
function npm-do {
	(PATH=$(npm bin):$PATH; eval $@;)
}
```

Vous pourrez alors lancer les commandes voulues par le biais de cette méthode :

```
$ npm-do gulp live
```


Innitialisez votre environement
-------------------------------------------------------------------------------

### Clôner ce dépôt avec Git

Clôner ce dépôt avec Git :

```bash
$ cd ~
$ git clone git@git.clever-age.net:tv5monde/afrique.git
```

### Installation des dépendances du projet
Lors du démarrage de votre projet et à chaque fois que le dépôt est rapatrié en
local, exécutez les commandes suivantes :

```bash
$ npm install
```


Organisation des fichiers
-------------------------------------------------------------------------------

Le projet utilise la structure de fichiers suivante.

Les sources sur lesquelles nous travaillons sont toutes dans le répertoire
`src`. _Normalement, seuls les fichiers présents dans ce répertoire devraient
être modifiés après l’initialisation du projet._

* `/src`
* `/src/css` : l’ensemble des fichiers qui produiront du CSS.
* `/src/js` : l’ensemble des sources JavaScript du projet
* `/src/assets` : l’ensemble des fichiers qui doivent être utilisés par le projet en l’état.
* `/src/assets/img` : l’ensemble des images d’interface du projet
* `/src/assets/svg` : l’ensemble des svg d’interface qui seront regroupées en sprites dès que possible.
* `/src/assets/fonts` : l’ensemble des fontes utilisées par le projet
* `/src/html` : l’ensemble des gabarits qui produiront du HTML
* `/src/data` : les fichiers JSON de données à injecter dans les gabarits HTML ou autres
* `/src/docs` : l’ensemble de la documentation statique du projet au format Markdown

À chaque fois que le projet est « construit », le résultat est disponible dans
les répertoires suivant :

* `/build`
* `/build/doc` : toute la documentation du projet au format HTML


Tâches
-------------------------------------------------------------------------------

Le projet hérite des tâches Gulp normalisées du _Garder Starter Kit_ dispose d'un certain nombre de tâches.

**connect** : Demarre le serveur intégré

```bash
$ gulp connect
```

> **ATTENTION :** _Même si tous les chemins sont résolus de manière relative, il
  est vivement conseillé de préférer cette méthode à tout autre serveur local
  que vous pourriez utiliser. De cette manière, vous verrez toujours votre site
  « à la racine ». Sauf si le port est déjà occupé, votre site répondra sur l’URL : [http://localhost:8000](http://localhost:8000)_

**live** : Permet de démarrer un serveur statique pour les pages HTML et d’avoir un _watch_ sur les fichiers du projet en même temps.

```bash
$ gulp live

# Pour ne pas être embêté par les tests,
# vous pouvez lancer le live en mode relax
# (Mais c’est mal et vous le savez)
$ gulp live --relax

# Pour des raisons de performance,
# le watcher ne génère pas par défaut la documentation
# Mais vous pouvez activer cette fonctionalité :
$ gulp live --doc
```

**build** : Contruit la version statique du projet (compile les fichiers Sass, assemble les fichiers HTML, etc.)

```bash
$ gulp build

# Pour créer un build optimisé pour la prod
# (Fichiers minifiés, pas de doc, etc.)
$ gulp build --optimize
```

**css** : construit les feuilles de styles

```bash
$ gulp css
```

**html** : construit les pages HTML statiques

```bash
$ gulp html
```

**js** : construit les fichiers JS

```bash
$ gulp js
```

**assets** : déplace et optimise les ressources statiques du projet

```bash
$ gulp assets
```

**doc** : génère la documentation du projet

```bash
$ gulp doc
```

**test** : exécute tous les tests du projet

```bash
$ gulp test
```

**sftp-deploy** : déploie le dossier build sur le serveur de preview. Sur le serveur distant, le nom du dossier créé contiendra le numéro de version renseigné dans le fichier `package.json`.

```bash
$ gulp sftp-deploy
```


Outils utilisés
-------------------------------------------------------------------------------
Les outils listés ici doivent êtres utilisés obligatoirement lorsqu’on démarre un nouveau projet d’intégration. Ils garantissent un _workflow_ de travail optimal.

* [Gulp](http://gulpjs.com/)
* [Linter](linter.md)

Les outils listés ci-après sont à utiliser et à configurer pour votre projet.
Ils sont tous utilisables tels quels, mais le _starter kit_ est suffisamment flexible pour s’adapter à vos besoins. Le choix d'utilisation de ces outils se fait via le fichier `.gsk/config.json`, voir les instructions de configuration ci-après :

### CSS
* [Sass](css/sass.md) [Recommandé]
* [Sass/Compass](css/compass.md)

### HTML
* [Twig](html/twig.md) [Recommandé]

### JavaScript
* [Webpack + NPM](js/webpack.md)

### Documentation
* [Documentation statique](docs/index.md)
* [KSS](kss.md)

### Autres outils
* [Nproxy](nproxy.md) pour servir vos fichiers locaux à la place de fichiers distants (debug)
* [Browsersync](browsersync.md) pour rendre le browser-testing plus facile
* [Import](import.md) pour copier simplement des fichiers dans le build (exemple : assets de dépendances)
