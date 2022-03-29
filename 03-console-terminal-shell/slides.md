%title: LINUX
%author: xavki


# LINUX : Terminal vs Console vs Shell


<br>

TERMINAL

<br>

* historiquement cela ressemblait à des machines à écrire

<br>

* multiuser & échange input/output avec le système

<br>

* c'est un device qui va utiliser un processus pour communiquer

<br>

* connection avec identification (user/password, clef sécurisée...)

<br>

* permet :
		* afficher des lignes
		* gestion des retour à la ligne
				* CR : cariage return
				* LF : line feed
		* envoi d'instruction au process

-------------------------------------------------------------------------------------------

# LINUX : Terminal vs Console vs Shell


<br>

* tty = terminal  > teletypewriter

<br>

* exemple sur ubuntu ctrl + alt + <num terminal>

<br>

* avoir les caractéristiques de son terminal

```
who
stty -a
echo "toto" > /dev/tty1
```

<br>

* reél terminal vs virtual terminal (émulateur)
		* réel = premier terminal > console
		* terminal virtuel = application (fait office de terminal)
				* augmentation des possibilités (clones...)

<br>

* input > 0  / output > 1
	* référence aux file descriptor (fd > stdin/stdout)

-------------------------------------------------------------------------------------------

# LINUX : Terminal vs Console vs Shell


CONSOLE

<br>

* accès physique au terminal primaire

<br>

* connexion avec des outils spécifiques en datacenter

<br>

* pas besoin d'accès réseau
		* dernier recours si perte de connexion réseau totale)
		* connexion standard
		* ou connexion via les outils construteurs (idrac Dell / ilo HP)
			* intervention distante

-------------------------------------------------------------------------------------------

# LINUX : Terminal vs Console vs Shell


SHELL

<br>

* shell vs kernel

<br>

* interpréteur de commande via le terminal
		* mode de communication

<br>

* différents type de shell
		* bourne shell (/bin/sh)
		* bash (bourne again shell) (/bin/bash)
		* z-shell (zsh)
		* ...

<br>

* permet des fonctions avancées
		* pipe : communication inter-processus

<br>

* prompt vs command

```
prompt : command (options) (arguments)
```
