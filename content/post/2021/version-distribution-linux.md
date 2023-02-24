---
title: Quelle est la version courante de la distribution Linux
date: 2021-06-06
categories:
  - "Linux"
draft: true
---

Le fichier `/etc/os-release` permet d'obtenir les informations relatives à la version du système sur lequel vous vous trouvez.

[Ce fichier](https://www.freedesktop.org/software/systemd/man/os-release.html) a été introduit par le fameux `systemd`.

## Exemple de contenu

```
$ cat /etc/os-release
NAME="Ubuntu"
VERSION="20.04.4 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.4 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
```

## Récupérer la version courante en shell

Si vous avez besoin de scripter des actions en fonction de la version courante de l'OS, vous pouvez inclure ce fichier dans votre script et afficher ou utiliser le contenu des variables.

```
$ cat test.sh
#!/bin/bash

. /etc/os-release

echo ${NAME}
echo ${PRETTY_NAME}
```

```
$ bash test.sh
Ubuntu
Ubuntu 20.04.4 LTS
```
