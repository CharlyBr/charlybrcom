---
title: Utiliser la date dans le nom de l'access log
date: 2023-02-27
tags:
  - "nginx"
categories:
  - "http"
draft: false
---

A une époque, j'utilisais beaucoup le couple Apache/Cronolog pour classer les fichiers de logs http par vhost et par date.

Par exemple :
```
TransferLog "|/usr/sbin/cronolog /www/logs/%Y/%m/%d/access.log"
ErrorLog "|/usr/sbin/cronolog /www/logs/%Y/%m/%d/errors.log"
```

Utilisant plus souvent Nginx à la place d'Apache, je cherchais une solution pour faire la même chose sur un serveur avec plusieurs vhosts persos.

Il existe des solutions pour Nginx à base de FIFO mais je cherchais quelque chose de plus simple.
Il est possible d'utiliser des variables dans les noms de fichiers et de créer des variables à partir du timestamp de la requête courante.

On peut par exemple extraire l'année, le mois et le jour et les utiliser pour forger le nom du fichier de l'access log.

```
if ($time_iso8601 ~ "^(\d{4})-(\d{2})-(\d{2})") {
    set $year $1;
    set $month $2;
    set $day $3;
}
access_log /var/log/nginx/charlybr.com/$year-$month-access.log main;
```

Il faut noter que Nginx ne va pas créer de répertoires pour vous, j'ai donc ici créé le répertoire du vhost à la main et limité les logs sur le couple `année-mois`.

A noter aussi, qu'il ne faut pas utiliser d'underscore `_` après les noms de variables car ils sont autorisés dans les noms de variables, contrairement aux tirets.

On peut facilement imaginer une cron pour créer quotidiennement / à l'avance, les répertoires nécessaires pour le stockage sous une forme du type :
```
access_log /var/log/nginx/charlybr.com/$year/$month/$day/access.log main;
```
