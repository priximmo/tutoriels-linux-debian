%title: LINUX
%author: xavki


# LINUX : ENVIRONNEMENT

<br>

* tuto précédent : utilisateurs & permissions

		* /home/<user>

		* personnalisation par utilisateur (réel ou system)

	=> Environnement & Scripts de démarrage

	=> bien sûr tout cela s'enclenche à la connexion = login

----------------------------------------------------------------------

# LINUX : ENVIRONNEMENT


<br>

* la commande login 

		* man login (files...)

		* configuration /etc/login.defs (man !!)

		* deux types de interactive (remote ou su) / non interactive (script distant)

		* shell login vs non login (sh après auth)

		* ex : non login et non interactive = script lancé dans la CLI

----------------------------------------------------------------------

# LINUX : ENVIRONNEMENT

<br>

* après lancement de login :

		* scripts (autocompletion etc)

		* source de certaines variables (variables d'environnement)

<br>

* l'environnement :

		* commande env (man !!) : -i / ajout variable

		* commande export (help !!)

----------------------------------------------------------------------

# LINUX : ENVIRONNEMENT

<br>

* cheminement des fichiers définissant l'environnement 
		* pour un interactive login ;)

		1- /etc/profile
		2- /etc/profile.d/*
		3- ~/profile ou ~/.bash_profile
		4- ~/.bashrc (exception)
		...
		x- ~/.bash_logout
