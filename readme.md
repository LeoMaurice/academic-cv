# CV académique

Template de site académique créé avec [Hugo](https://gohugo.io/) et le thème [PaperMod](https://github.com/adityatelange/hugo-PaperMod) créé par [Aditya Telange](https://github.com/adityatelange).

Il permet de créer rapidement un site personnel comprenant :

- une page de CV ou de biographie ;
- une page consacrée aux publications ;
- des articles ou billets de blog ;
- plusieurs langues ;
- des tags, catégories et séries ;
- une recherche dans le contenu du site ;
- un déploiement possible avec GitHub Pages.

## Utiliser ce dépôt comme template

Le dépôt peut servir de base à plusieurs sites personnels.

Vous pouvez :

- utiliser la fonctionnalité **Use this template** de GitHub ;
- cloner le dépôt et créer un nouveau dépôt ;

Il faut simplement penser à activer GitHub Pages, en précisant le déployement par GitHub Actions. Le workflow est déjà présent dans le repos.

## Structure du contenu

Le contenu du site se trouve dans le dossier `content/`.

```text
content/
├── bio.md
├── bio.en.md
├── papers.md
├── papers.en.md
└── posts/
    ├── firstpost.md
    ├── firstpost.en.md
    └── postseries/
        ├── _index.md
        ├── _index.en.md
        ├── postseries-debut.md
        ├── postseries-debut.en.md
        ├── postseries-fin.md
        └── postseries-fin.en.md
```

Les fichiers sans suffixe correspondent à la langue principale du site, ici le français :

```text
bio.md
papers.md
posts/firstpost.md
```

Les fichiers dont le nom se termine par `.en.md` correspondent à la version anglaise :

```text
bio.en.md
papers.en.md
posts/firstpost.en.md
```

Si une page n’existe que dans une langue, il suffit de créer un seul fichier :

```text
content/page-uniquement-francaise.md
```

## Configurer les langues

Les langues sont définies dans `hugo.yaml` :

```yaml
defaultContentLanguage: fr

languages:
  fr:
    languageName: Français
    languageCode: fr-fr
    weight: 1

  en:
    languageName: English
    languageCode: en-us
    weight: 2
```

La langue principale utilise les fichiers sans suffixe. Les autres langues utilisent leur code dans le nom du fichier.

## Modifier la page de CV

La page de CV ou de biographie se trouve dans :

```text
content/bio.md
content/bio.en.md
```

## Ajouter des publications

Les publications sont regroupées dans :

```text
content/papers.md
content/papers.en.md
```

## Ajouter des articles

Les articles sont placés dans le dossier :

```text
content/posts/
```

Pour créer un article :

```bash
hugo new posts/firstpost.md
```

Pour créer la version anglaise du même article, ajoutez :

```text
content/posts/firstpost.en.md
```

Un article avec :

```yaml
draft: true
```

est visible uniquement pendant le développement local :

```bash
hugo server -D
```

Pour le publier, utilisez :

```yaml
draft: false
```

ou supprimez la ligne `draft`.

### Séries d’articles

Les articles peuvent être regroupés dans un sous-dossier :

```text
content/posts/postseries/
```

Le fichier `_index.md` définit la page de la série :

```text
content/posts/postseries/_index.md
content/posts/postseries/_index.en.md
```

Les articles appartenant à cette série peuvent ensuite être placés dans le même dossier.

## Tags, catégories et séries

Le site utilise trois taxonomies :

- `tags` : mots-clés précis décrivant le contenu ;
- `categories` : grandes catégories thématiques ;
- `series` : groupe d’articles ou de pages liés entre eux.

Exemple :

```yaml
tags:
  - méthodes
  - recherche
  - université

categories:
  - académique

series:
  - publications
```

Utilisez de préférence des noms cohérents et des minuscules pour éviter de créer plusieurs termes presque identiques, par exemple `recherche` et `Recherche`.

## Recherche

La recherche est une fonctionnalité de PaperMod. 

La page correspondante est `search.md` (`search.en.md`) en anglais. Il faut préciser `layout: search`, le reste est modifiable

Exemple de configuration :

```yml
---
title: "Recherche"
placeholder: Chercher dans mes posts
layout: "search"
---
```

## Configuration principale

La configuration du site est contenu dans `hugo.yaml`.

Les autres options de PaperMod sont disponibles dans la [documentation du thème](https://github.com/adityatelange/hugo-PaperMod/wiki/).

## Images, PDF et fichiers statiques

Les fichiers qui doivent être accessibles directement sur le site sont placés dans `static/`.

Par exemple :

```text
static/files/cv.pdf
static/images/photo.jpg
```

seront accessibles avec :

```text
/files/cv.pdf
/images/photo.jpg
```

Le dossier `public/` est généré par Hugo. Il ne doit pas être modifié manuellement.

## Personnaliser le template

Pour créer votre propre site :

1. modifiez le titre et les paramètres dans `hugo.yaml` ;
2. remplacez les fichiers d’exemple dans `content/` ;
3. ajoutez les versions anglaises avec le suffixe `.en.md` ;
4. ajoutez vos publications et vos articles dans `content/`, voir dans une série de postes dédiées dans `content/publications/` ;
5. ajoutez vos fichiers PDF et vos images dans `static/` ;
6. testez le site avec `hugo server` ;
7. construisez le site avec `hugo --minify`.

Le dossier `public/` ne doit pas être édité directement : son contenu est recréé automatiquement lors de chaque compilation.

Il faut utiliser `hugo --server` pour afficher une version locale de test de votre site.

Pour les détails concernant Hugo, consultez la [documentation officielle de Hugo](https://gohugo.io/documentation/).

## Déploiement

Ce template peut être déployé avec GitHub Pages et GitHub Actions.

Pour un dépôt de projet, le `baseURL` doit inclure le nom du dépôt :

```yaml
baseURL: "https://utilisateur.github.io/nom-du-depot/"
```

Attention, si vous utilisez un dépît avec le même nom que votre compte GitHub, cela devient :

```yaml
baseURL: "https://utilisateur.github.io/"
```

Pour le déploiement avec GitHub Pages, consultez la [documentation GitHub Pages](https://docs.github.com/en/pages).

## Licence

Le code et la structure propres à ce template sont distribués sous licence MIT.

Ce projet utilise le thème [PaperMod](https://github.com/adityatelange/hugo-PaperMod), lui-même distribué sous licence MIT. Sa licence est disponible dans `themes/PaperMod/LICENSE`.

Les contenus personnels — notamment le CV, les publications, les textes, les images et les fichiers PDF — restent protégés par le droit d’auteur de leurs auteurs, sauf mention contraire.
