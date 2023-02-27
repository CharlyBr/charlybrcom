---
title: About
date: 1980-07-19T14:30:00.000Z
authorbox: false
sidebar: false
draft: false
menu: main
---

Ce site est construit avec [Hugo](https://gohugo.io/) et le thème
[PaperMod](https://github.com/adityatelange/hugo-PaperMod/).

## Installation du thème

* Voir https://github.com/adityatelange/hugo-PaperMod/wiki/Installation

### Installation en tant que submodule git 

```
$ git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

* mise à jour du thème

```
$ git submodule update --remote --merge
```


## Utilisation de Hugo en local

```
$ hugo -D server
[...]
Web Server is available at //localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

## Rendu des fichiers statiques du site

```
$ hugo
Start building sites …
hugo v0.110.0+extended darwin/amd64 BuildDate=unknown

                   | EN
-------------------+-----
  Pages            | 42
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  0
  Processed images |  0
  Aliases          | 16
  Sitemaps         |  1
  Cleaned          |  0

Total in 102 ms
```

Votre site est disponible dans le répertoire `public/`.
