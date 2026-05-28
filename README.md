# Modes ALTTPRFR

## Installation (pour dev)

- Installer NodeJS (version 22 recommandée, 24 ne fonctionne pas de mémoire)
- Cloner ce repo et ouvrir le dossier dans un invite de commandes
- Exécuter `npm ci` pour installer le module Astro (qui gère l'affichage des templates)

## Lancer l'environnement de dev

- Ouvrir le dossier de ce repo dans un invite de commandes
- Exécuter `npm run dev`, attendre que la ligne avec `ready` apparraisse (peut
être long)
- Se connecter à <http://localhost:4321> pour vérifier que le site s'affiche bien

## Données

Les données sont réparties dans différents fichiers, tous dans le dossier `src/data`:

### Niveaux d'accord

- Fichier : `agreements.json`
- Structure : une liste avec différents niveaux d'accord (e.g. "Dispo pour
toutes les phases", "Dispo seulement si les deux joueureuses sont d'accord", ...)
- Pour en ajouter / enlever, il faudra aussi modifier le fichier
`src/components/CategoryContent.astro`, en haut du fichier la ligne avec
`numberOfAgreements`.

### Générateurs

- Fichier : `generators.json`
- Structure : une liste de générateurs avec un indicateur et un nom

### Catégories

- Fichier : `categories.json`
- Structure : une liste de catégories avec un indicateur (une "slug") et un nom

### Modes

- Fichier : pour chaque catégorie, un fichier (e.g. `opn.json`, `std.json`, ...)
- Structure : il faut autant de liste que de niveaux d'accord (e.g. 0,
1, 2), même s'il n'y a pas de mode dans le niveau d'accord ! (Voir par exemple
`std.json`)
- Pour en ajouter / enlever, il faudra aussi modifier le fichier
`src/pages/index.astro`, en haut du fichier il faut rajouter un import pour le
fichier de données de la catégorie (e.g.
`import openData from "../data/opn.json";`) avec un nom spécifique, ainsi que
modifier `modesData` pour faire correspondre à la slug de la catégorie les
données importées (prendre exemple sur `"OPN"`).

## Nom de domaine

- [Source](https://docs.astro.build/en/guides/deploy/github/)
- Modifier le fichier `astro.config.mjs`, mettre la bonne URL au niveau du
paramètre site
- Créer un fichier `CNAME` dans le dossier `public`, y écrire le nom de domaine
  (e.g. `alttprfr.com`)

## Mettre à jour

Il y a une automatisation Github Pages mise en place, il suffit de faire un
commit une fois les modifications terminées et de push sur le repo.
