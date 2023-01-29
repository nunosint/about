---
layout: post
title: Où sont stocké les ISO sur Proxmox
description: no description
tags: []
---

Bonjour !   
Vous souhaitez accéder au ISO stocker sur votre PROXMOX ?

Facile, prenez un café et allons-si !

```Niveau : 🟢🟢⚪⚪⚪```

# 1 - Ouvrir un gestionnaire FTP / SFTP

Afin de faciliter l'accès au ISO sur notre machine, il est plus intéressant d'y voir plus clair via un client de fichier graphique.


Je recommande :  
* [WinSCP](https://winscp.net/) (windows seulement, simple et rapide, open source)  
* [Filezilla](https://filezilla-project.org/) (compatible avec MacOS et Linux, mais l'interface est moins intuitive, open source)

# 2 - Se connecter à notre serveur

Pour se connecter à sont serveur via notre gestionnaire, nous avons besoins :


* De son IP (exemple : 192.168.1.2)
* Du nom d'utilisateur, dans notre cas "root"
* Du mot de passe root de votre PVE


Pensez à accepter les connexions en root sur votre PVE. [Aide](https://cloriou.fr/2016/12/05/debian-autoriser-acces-root-via-ssh/)

Lancer votre gestionnaire et connectez-vous :

[![Exemple](https://cdn.discordapp.com/attachments/562313609774891008/1046566651996418130/index.jpg)]()

/!\ verifier que le protocole est bien definie sur ```SFTP```

# 3 - Se rendre dans le répertoire en question

Le répertoire où sont stocker les ISO sur proxmox est :


> /var/lib/vz/template/iso

# 4 - Fin du café

Et voilà ! Vous avez toute vos ISO déposer depuis votre panel.  
Vous pouvez bien évidement déposé vos ISO depuis votre gestionnaire et il seront lisible dans votre panel.

_Ce tuto peux être obselète à tout moment, je le mettrait à jour si il le faut._

_Source : [virtualizationhowto.com](https://www.virtualizationhowto.com/2022/09/proxmox-create-iso-storage-location-disk-space-error/)_
