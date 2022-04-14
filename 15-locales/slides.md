%title: LINUX
%author: xavki


# LINUX : LES LOCALES

<br>

Les spécificités des localisations :

		* format de la date et heures

		* premier jour de la semaine

		* la monnaie

		* le séparateur numérique (milliers)

		...

		=> Les Locales

---------------------------------------------------------------------------------

# LINUX : LES LOCALES


<br>

Comment trouver les locales ?

		* /etc/default/locale

		* commande : localectl

		* commande : locale

		* fr_FR.utf8 = langue.encodage

Les valeurs :

```
localectl list-locales
locale -a
```

---------------------------------------------------------------------------------

# LINUX : LES LOCALES

<br>

Liste des principales locales :

		* LANG : valeur si non défini dans "LC_*"

		* LANGUAGE : définition de valeurs utilisables par défaut
					* classé par ordre séparé de ":"

		* LC_TIME : format des heures et des dates

		* LC_COLLATE : classement lors de tris ou regexp

		* LC_ALL : surcharge toutes les autres locales

		* LC_NUMERIC : format numérique

		* LC_MESSAGES : langues des mots et réponses

		* LC_PAPER : format du papier

		* LC_MONETARY : format monétaire

		* LC_TELEPHONE / LC_ADDRESS / LC_MEASUREMENT / LC_NAME

---------------------------------------------------------------------------------

# LINUX : LES LOCALES

<br>

Détail sur une locale :

```
locale -k LC_TIME
locale -k LC_PAPER
```

<br>

Commandes à retenir :

```
man locale
man localectl
man update-locale
```

---------------------------------------------------------------------------------

# LINUX : LES LOCALES

<br>

Mise à jour :

```
sudo update-locale LC_PAPER=en_US.UTF-8
sudo localectl set-locale LC_PAPER=en_US.UTF-8
```

<br>

Spécifique pour un utilisateur :

```
~/.bashrc
export LC_ALL=en_US.UTF-8
```

---------------------------------------------------------------------------------

# LINUX : LES LOCALES

<br>

Et un peu plus...

* pour la définition du clavier

```
# sur console
sudo loadkeys fr
ou
setxkbmap us
setxkbmap fr
```
