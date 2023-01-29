---
layout: post
title: Installer Apache2 et l'utiliser pour du multisite & multiport
description: no description
tags: []
---

Bonjour !   
Vous voulez héberger plusieurs sites sur Apache2 avec différent port ?

Avec plusieurs commandes tout ce fait facilement, prenez un café et allons-si !

```Niveau : 🟢🟢⚪⚪⚪```

# 1 - Se connecter à sa machine pour installer apache2

Pour se connecter à sa machine on va utiliser le protocole ```SSH```.
Ouvrez votre terminal :

Sur Windows : Win+R -> CMD
Sur Linux : Ctrl+Alt+T
Sur MacOS : Allez dans Applications puis Utilities (utilitaires) et ouvrez Terminal

Vérifié si le protocole SSH est bien installez sur votre machine en inscrivant "SSH" dans le terminal.
Si tout est bon, un message devrais apparaitre, tant que la commande retourne un message qui semble bon, on peux continuer.
Si ce n'est pas la cas, allez sur google chercher comment l'activer.

Continuons, après avoir tapez SSH inscrivez l'utilisateur de votre serveur, généralement "root". Après root nous meterrons un "@" suivie de l'adresse ip du serveur.
[![Exemple](https://cdn.discordapp.com/attachments/562313609774891008/1069378200909651968/Capture_decran_20230129_230617.png)]()

Après vous être connecter à votre machine, mettez là à jour via c'est commande :

```apt-get update && apt-get upgrade -y ```

Puis redémarrer la via ```reboot```.

Après vous être reconnecter on va installez Apache2. Pour ce faire tapez :

```apt install apache2```

Pour vérifiez que Apache2 est bien installer on tape : 

```systemctl status apache2```

Parfait ! Vous pouvez désormais accéder à la page par défaut de Apache via l'adresse IP de votre serveur sur votre navigateur internet.

# 2 - Configurer apache2 et importer les sites

À présent nous allons configurer apache2. Pour ce faire nous allons utiliser les répertoires :

* /var/www/html
* /etc/apache2

Pour commencer nous allons supprimer les fichiers par défaut de apache2. Pour le faire plus rapidement, nous pouvons utiliser un gestionnaire FTP / SFTP, je vous redirige vers mon tuto "Où sont stocké les ISO sur Proxmox" pour vous connectez à votre machine.

Nous allons dans ```/var/www/html``` et supprimer le document html par défaut.
Vous pouvez crées les dossiers de vos sites directement, je les nomerais "WebX" (X=1->Premier site, X=2-> Deuxième site,...). Je vous invite à importer vos documents de vos sites dans chacun des dossiers.

Nous retournons ensuite dans notre terminal pour configurer apache2.

















# X - Tout fonctionne !

À présent vous pouvez configurer plusieurs sites comme bon vous semble sans à avoir à crée plusieurs machines virtuelles pour chaque sites.

_Ce tuto peux être obselète à tout moment, je le mettrait à jour si il le faut._

_Source : [youtube.com](https://www.youtube.com/watch?v=6hG477N6jI8)_
_Source : [youtube.com](https://www.youtube.com/watch?v=Vn5PWMKq-wg)_

