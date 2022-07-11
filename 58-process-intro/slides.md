%title: LINUX
%author: xavki


# LINUX : Un PROCESS c'est quoi ??


<br>

* process = processus (tasks)

* un process = c'est une instance d'un programme (plus ou moins gros/important

* c'est un exécutable (permissions)

* stocké sur la machine (sauf exceptions...)

* lancer un programme = créer un nouveau processus

* lancé par un utilisateur (système ou réel)

* PID = identifiant unique du processus

* Linux = multitask OS (multiple process en même temps)

https://tldp.org/LDP/tlk/kernel/processes.html

<br>

* lister les processus : commande ps

```
ps 
echo $$
ps aux
ps auxwww
```

Note : notre bash/shell est un process

<br>

* process / hardware = CPU & Memoire & stockage (lui-même)

Caractéristiques :

		* un identifiant le PID

		* adresse en mémoire

		* un statut : running, stopped, waiting, zombie

		* des ressources : cpu/ram

		* des fichiers utilisés

		* des sockets réseaux (fichiers dédiés à la communication) & des ports

		* un propriétaire (owner qui a lancé el process) - UID

		* des signaux

		* peut attendre :  cpu/ io disque / réseau...

PID : 

		* identifiant unique dans le kernel

		* numéro incrémenté par ordre de création

		* isolation entre les processus (sécurité)

PID 1 = Init

		* le père de tous les process (règle Unix)

		* émane de systemD

```
man init
```

		* c'est donc la première et la dernière task du système (commande init 0 - arrêt / init 6 - reboot)

		* issue de la phase de boot (cf vidéo précédente)

		* création de processus par fork

```
man 2 fork
```

		* reaping = s'occupe des processus orphelins (perte des parents)

```
ps aux | head -n2
```

Un peu d'histoire : https://linuxfr.org/news/systemd-l-init-martyrise-l-init-bafoue-mais-l-init-libere
