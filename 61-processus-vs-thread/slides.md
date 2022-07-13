%title: LINUX
%author: xavki


# LINUX : Un PROCESS c'est quoi ??


<br>

* process = processus (tasks)

<br>

* un process = c'est une instance d'un programme (plus ou moins gros/important

<br>

* c'est un exécutable (permissions)

<br>

* stocké sur la machine (sauf exceptions...)

<br>

* lancer un programme = créer un nouveau processus

<br>

* lancé par un utilisateur (système ou réel)

<br>

* PID = identifiant unique du processus

<br>

* Linux = multitask OS (multiple process en même temps)

https://tldp.org/LDP/tlk/kernel/processes.html

-----------------------------------------------------------------------------------------------------------

# LINUX : Un PROCESS c'est quoi ??


<br>

* process = processus (tasks)

<br>

* lister les processus : commande ps

```
ps 
echo $$
ps aux
ps auxwww
```

Note : notre bash/shell est un process

-----------------------------------------------------------------------------------------------------------

# LINUX : Un PROCESS c'est quoi ??

<br>

* process / hardware = CPU & Memoire & stockage (lui-même)

Caractéristiques :

<br>

		* un identifiant le PID

<br>

		* adresse en mémoire

<br>

		* un statut : running, stopped, waiting, zombie

<br>

		* un propriétaire (owner qui a lancé le process) - UID

<br>

		* des ressources : cpu/ram

<br>

		* des fichiers utilisés

		* des sockets réseaux (fichiers dédiés à la communication) & des ports

		* des signaux

		* peut attendre :  cpu / io disque / réseau...

-----------------------------------------------------------------------------------------------------------

# LINUX : Un PROCESS c'est quoi ??

<br>

PID : 

		* identifiant unique dans le kernel

		* numéro incrémenté par ordre de création

		* isolation entre les processus (sécurité)

-----------------------------------------------------------------------------------------------------------

# LINUX : Un PROCESS c'est quoi ??

<br>

PID 1 = Init

		* le père de tous les process (règle Unix)

```
ps aux | head -n2
```
		* émane de systemD (management des services, montages... sous forme d'unités)

```
man init
```

<br>

		* c'est donc la première et la dernière task du système (commande init 0 - arrêt / init 6 - reboot)

		* issue de la phase de boot (cf vidéo précédente)

		* création de processus par fork 

```
man 2 fork
```

<br>

		* reaping = s'occupe des processus orphelins (perte des parents)

-----------------------------------------------------------------------------------------------------------

# LINUX : Un PROCESS c'est quoi ??


<br>

Un peu d'histoire : https://linuxfr.org/news/systemd-l-init-martyrise-l-init-bafoue-mais-l-init-libere
