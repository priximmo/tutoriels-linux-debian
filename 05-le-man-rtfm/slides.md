%title: LINUX
%author: xavki


# LINUX : LE MAN & RTFM

<br>

* la documentation formelle sur linux, ses commandes

* disponible sur le terminal ou en ligne

* différentes langues disponibles

* utilisable via la commande

```
man
man man
h
```

--------------------------------------------------------------------------

# LINUX : LE MAN & RTFM

<br>

* Structure d'une page de man

	* nom : commande ou autre
  
	* copyright

	* résumé (synopsys)

	* description

	* options

	* Notes

	* Exemples

	* Auteurs de la commande

	* ...

```
man man-pages
```

--------------------------------------------------------------------------

# LINUX : LE MAN & RTFM

<br>
```
man -L fr man
```

* découpé en section

```
    Programmes exécutables ou commandes de l'interpréteur de commandes (shell) 
    Appels système (Fonctions fournies par le noyau)
    Appels de bibliothèque (fonctions fournies par des bibliothèques)
    Fichiers spéciaux (situés généralement dans /dev)
    Formats des fichiers et conventions
    Jeux ;
    Divers (y compris les macropaquets et les conventions)
    Commandes de gestion du système (admin)
    Interface du noyau Linux.
```

--------------------------------------------------------------------------

# LINUX : LE MAN & RTFM

<br>

* chaque section dispose d'une intro

```
man 1 intro
```

* comment chercher ?

```
man -k <recherche>
man -k swapoff
apropos <recherche>
man -K <recherche> 
```

--------------------------------------------------------------------------

# LINUX : LE MAN & RTFM

<br>

* recherche dans une page

```
\<mot>
```

```
n # next
N # previous
G # bas de page
g # haut de page
```
