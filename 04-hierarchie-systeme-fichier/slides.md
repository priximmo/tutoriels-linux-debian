%title: LINUX
%author: xavki


# LINUX : Commandes & Hiérarchie du Système de Fichier


<br>

Un standard

* Système de Fichiers = Filesystem

* Filesystem Hierarchy Standard (FHS) : standard Linux (version 3 datant 2015)

* composé de fichiers et de répertoires

* sur linux tout n'est que fichiers

* repose sur le disque (prochaine vidéo) & un format (formater)

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

Commandes pour débuter

* lister les fichiers et les répertoires

```
ls
```

* quelques options intéressantes

```
-a : liste tout y compris les fichiers cachés (commençant par .)
-l : format liste détaillée
-t : classer par date de modification
-r : inverser l'ordre de la date
-h : taille en format lisible pour un humain ;)
-1 : liste simple avec un élément par ligne
```

Note : et bien d'autres encore plus importantes (mais moins utilisées)

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* changer de répertoire

```
cd
```

* utilisation courante

```
/
~
..
.
```

* afficher le répertoire courant

```
pwd
```

* installer la commande tree (optionnel)

```
sudo apt update
sudo apt install tree
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

LES REPERTOIRES

<br>

* la racine ou le root directory

```
/
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* le chargeur d'amorçage (vue dans la vidéo sur le boot)

```
/boot/
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* les binaires de base & réservés aux administrateurs

```
/bin/
/sbin/
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* les périphériques physiques ou virtuelles
		* le stockage (hdd, ssd, cd, usb...)
		* les terminaux (tty - cf vidéos précédentes)
		* /dev/null, /dev/zero ou /dev/random
		* ...

```
/dev/
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* les fichiers de configuration

```
/etc/
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* les home dédiées aux utilisateurs (vrais ou applicatifs)

```
/home/
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* les librairies utilisées par les binaires ou applicatifs

```
/lib/
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* les applis optionnelles (installées manuellement)

```
/opt/
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* la home de l'utilisateur root

```
/root/
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* autres répertoires de binaires non nécessaires au système
		* Unix Système Resources

```
/usr/
/usr/bin/
/usr/lib/
/usr/share/
/usr/src/ > code source du noyau (non compilé)
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* fichiers variables = données
		* logs
		* base de données
		* journaux...

```
/var/
/var/log/
/var/lib/
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* les fichiers temporaires (vidage)

```
/tmp/
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* les pseudos filesystèmes & informations du noyau

```
/proc/
/sys/
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* fichiers de récupérations pour le filesystem

```
lost+found
```

---------------------------------------------------------------------

# LINUX : Commandes & Hiérarchie du Système de Fichier

<br>

* les montage temporaires

```
/mnt/
/media/
```
