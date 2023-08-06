---
layout: post
title: Comment accéder à sa machine en SSH sans user/password
description: no description
tags: []
---

Bonjour !   
Vous souhaitez vous connecter facilement en SSH sans taper à chaque fois votre nom d'utilisateur et votre mot de passe  ?

Facile, prenez un café et allons-si !

```Niveau : 🟢🟢⚪⚪⚪```<br>
```OS expliquer : Windows 11 / debian```

# 1 - Vérifier si SSH est installer sur votre ordinateur

Pour pouvoir accéder à votre serveur via le protocole SSH, il faut avoir SSH Client sur votre ordinateur.

Vérifiez si vous avez SSH sur votre ordinateur dans un terminal avec la commande > "SSH"
Si SSH est installé vous devriez avoir une réponse > "usage: ssh...", sinon, il faudra l'installer :

Allez dans : 
* Paramètre Windows - Applications - Fonctionnalités facultatives
* Cliquer sur "Affichier les fonctionnalités"
* Rechercher "SSH"
* Installer "Client OpenSSH" (et pas "Serveur OpenSSH")

Dans le cas où vous n'arrivez pas à installer SSH de cette manière, installer le logiciel putty.

* [putty](https://www.putty.org/) (simple et rapide, open source)

Parfait, tout est fonctionnel à présent.

*ps: je considère que vous avez déjà le protocole SSH sur le serveur auquel vous voulez vous connecter. Si ce n'est pas le cas, je vous redirige vers ce tuto explicatif sous debian : [tuto](http://labrat.fr/article/installer-et-configurer-openssh-sur-debian.html)*

# 2 - Configurer une clés privée et public sur votre ordinateur

Maintenant que vous avez SSH sur votre ordinateur, rendez-vous dans le répertoire associer.

* Ouvrez votre explorateur Windows, 
* Allez dans le dossier utilisateur
* Votre nom d'utilisateur
* Puis .ssh

Si vous n'avez pas le dossier .ssh afficher, il suffit d'en créer un.

* Clique droit, créez un dossier, nommez le .ssh (dois-je vraiment l'expliquer ?)

Rentrez dans ce dossier puis créez un fichier config sans extension.

Ouvrez un terminal dans le même dossier (tapez cmd dans le vide où il y a marqué "Ce PC > Disque Local ..")

**Vérifiez dans votre terminal que vous êtes bien dans le dossier .ssh !**

Tapez la commande "ssh-keygen", elle répondra :

* Generating public/private rsa key pair.
* Enter file in which to save the key (C:\Users\ *votre nom d'utilisateur* /.ssh/id_rsa):
  
Écrivez le nom de votre serveur ou le service auquel vous vous connectez (proxmox, Omv, ...) suivi d'un "_rsa".
On vous demandera une "passphrase", pas besoin d'en mettre honnêtement, faite deux fois entré.

*ps: pour avoir accès aux extensions de fichier (png, .mp4, .mp3, etc..), allez dans "Afficher", puis "Afficher", et cliquer sur Extensions de noms de fichiers*

# 3 - Configurer le fichier config

Une fois que vous avez généré votre clé privée et public, vous devenez la rentrée dans le fichier de configuration SSH.
Ouvrez le fichier "config" créé précédemment avec votre éditeur de texte.
Rentrez cette configuration et modifiez les éléments selon votre cas, sans les guillemets ;

Host "nom de votre serveur/service"
	Hostname "ip de votre serveur"
	IdentityFile ~/.ssh/"nom de votre serveur/service"_rsa
	User "utilisateur que vous utilisez pour vous connectez en SSH"

# 4 - Appliquer votre clé public dans votre serveur 

Maintenant que vous avez configuré votre ordinateur pour l'authentification sans nom d'utilisateur et mot de passe, il faut l'appliquer sur votre serveur.

Pour ce faire connectez vous sur votre serveur.
Allez dans le répertoire de votre utilisateur via la commande "cd ~/".
Essayer "cd .ssh", si ça ne fonctionne pas c'est qu'il faut créer un dossier .ssh.
Tapez "mkdir .ssh", puis, refaites "cd .ssh".

Une fois dans le dossier faite la commande "nano authorized_keys".

Dans ce fichier tapez l'entièreté de votre fichier.pub dans le répertoire.SSH de votre ordinateur.

Pour ce faire ouvrez le avec votre éditeur de texte, copier via "CTRL + A" et "CTRL + C", puis retournez dans votre nano, clique droit et/ou collez.

Une fois cela fait réactualiser le service SSH sur votre serveur via la commande "systemctl restart sshd.service"

# 5 - Fin du café

Et voilà ! Vous pouvez vous connecter via SSH sur votre serveur sans taper de nom d'utilisateur ni de mot de passe.
Notez que c'est purement local et seul votre ordinateur aura accès de cette manière à votre serveur.
Pour appliquer cette méthode partout, refaites le tuto sur chaque ordinateur que vous avez besoin. N'oubliez pas de remplir le fichier "authorized_keys" des nouvelles clées par un retour à la ligne.

_Ce tuto peux être obselète à tout moment, je le mettrait à jour si il le faut._

_Source : [youtube.com/@GuiPoM](https://youtu.be/9XTYshvg8FE)_
