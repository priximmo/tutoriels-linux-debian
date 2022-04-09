%title: LINUX
%author: xavki


# LINUX : UMASK & SKEL ??

<br>

* suite des vidéos sur les permissions et l'environnement

* d'où viennent : 
		* fichiers de la HOME
		* ~/.profile
		* ~/.bashrc


---------------------------------------------------------------------

# LINUX : UMASK & SKEL ??


<br>

SKELETON

<br>

* répertoire modèle

* définit dans la configuration de useradd /etc/default/useradd

* /etc/skel par défaut

* attention à bien maintenir les permissions/droits

* uniquement pour les nouveaux utilisateurs

---------------------------------------------------------------------

# LINUX : UMASK & SKEL ??


<br>

UMASK

<br>

* rappel : rwx rwx rwx

		* 4 : r

		* 2 : w

		* 1 : x

		ex: 

			* 7 : rwx

			* 6 : r-w

			* 5 : r-x


---------------------------------------------------------------------

# LINUX : UMASK & SKEL ??

<br>

* les permissions appliquées par défaut :

		* 666 : fichiers

		* 777 : répertoires

* mais pourtant ? à la création les droits sont différents

* définit dans l'environnement

---------------------------------------------------------------------

# LINUX : UMASK & SKEL ??

<br>

* on reprend notre cheminement à partir du login > au bash.rc

		/etc/login.defs
		/etc/profile
		/etc/profile.d/*
		/etc/bash.bashrc
		~/.profile
		~/.bash_profile
		~/.bashrc

<br>

```
umask 002
umask u=#,g=#,o=#
```
