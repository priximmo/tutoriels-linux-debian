%title: LINUX
%author: xavki


# LINUX : Commande PS


<br>

* ps = process state

```
man ps
```

* pid, uid, priorité, cpu, mémoire, statuts, cmdline...

* le petit copain de la commande TOP

------------------------------------------------------------------

# LINUX : Commande PS

<br>

* attention : le tiret joue un rôle

```
ps a
ps -a
``` 

Note : a = tous les process

------------------------------------------------------------------

# LINUX : Commande PS

<br>

* exemples

```
ps a # tous les utilisateurs hors root
ps au # ajout d'information user
ps aux # tous les process sans exception
ps faux # sous forme d'arbre
ps fauxww # cmdline complète sans limite
ps raux # seulement les process running
```

------------------------------------------------------------------

# LINUX : Commande PS

<br>

* colonnes

		* USER : propriétaire du process (pas du programme ;) )
		* PID : Process id
		* %CPU : pourcentage d'utilisation du cpu par ce process (temps)
		* %MEM : pourcentage de la mémoire utilisé par ce process
		* VSZ : Virtual Memory Size (allouée mais pas forcément utilisée physique ou non)
		* RSS : Resident Set Size (utilisée et physique)
		* STAT : status du process (R / S / D / T / Z)
		* TIME : temps cumulé de CPU utilisé
		* CMD : la ligne de commande (programme)
		* TTY : terminal associé (si tel est le cas)
	
------------------------------------------------------------------

# LINUX : Commande PS

<br>

* trier par une colonne

```
ps aux --sort=+%mem
```

<br>

* PPID, horodatage

```
ps -ef
```

<br>

* pour les threads

```
ps -eLf
```

Note :
		* LWP : ID du thread
		* NLWP : Nb de thread

------------------------------------------------------------------

# LINUX : Commande PS

<br>

* TOP10 des process pour le CPU

```
ps -eo pcpu,args | sort -rn  | head
```

<br>

* récupérer la commande d'un process

```
ps -q 11729 -o cmd | tail -n1
ps -p 1 11729
```

------------------------------------------------------------------

# LINUX : Commande PS

<br>

* complément

```
ps -C vim
pgrep vim
pidof vim
pstree
```
