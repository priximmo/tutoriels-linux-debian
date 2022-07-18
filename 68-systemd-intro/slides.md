%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Introduction


<br>

* SystemD = System Daemon

<br>

* Grosse application avec plein de services

<br>

* annecdote : remplacement de SystemV  > System D = System 500 (chiffre romain)

* Pour l'histoire :

https://linuxfr.org/news/systemd-l-init-martyrise-l-init-bafoue-mais-l-init-libere

-------------------------------------------------------------------------------

# LINUX : SYSTEMD - Introduction

<br>

* beaucoup de discussions :

		* accélérer le boot final (desktop)

		* anti principe KISS (Keep It Simple and Stupid

		* non respect de règles fondamentales linux (conf hors etc ...)

		* scripts shell tranformés en déclaration

		* projet mené d'une main de fer

		* résistance de certaines distributions

		* ...

-------------------------------------------------------------------------------

# LINUX : SYSTEMD - Introduction

<br>

Perso = peu importe il faut faire comme c'est :)

... mais il y a encore des reliquats : /etc/init.d/ ou commande service...

<br>

Informations :

```
man systemd
man systemd.service
...
```

https://www.freedesktop.org/wiki/Software/systemd/
https://lea-linux.org/documentations/Systemd

-------------------------------------------------------------------------------

# LINUX : SYSTEMD - Introduction

<br>

* pid1 = init > systemd

```
ps aux
ls -la /sbin/init 
ps -q 1
```

-------------------------------------------------------------------------------

# LINUX : SYSTEMD - Introduction

<br>

* Management de différents daemons :

		* logind
		* systemd
		* journald
		* networkd
		* resolvd
		* ...

* Ordonne et Parallélise le démarrage (gain de temps)

-------------------------------------------------------------------------------

# LINUX : SYSTEMD - Introduction

<br>

* Leur configuration se découpe par unités :

```
systemctl -t help
systemctl list-units
```

-------------------------------------------------------------------------------

# LINUX : SYSTEMD - Introduction

<br>

		* service : process
		* socket : socket réseau de communication & IPC
		* target : regroupement de plusieurs unités (association au runlevel & ordonnancement)
		* mount : les montages en complément de fstab
		* automount : comme autofs (montage à la demande)
		* timer : équivalent des crons
		* device : pour la gestion des devices
		* scope : gestion de groupes au sein de systemd
		* slice : gestion des cgroups
		* snapshot : sauvegarde de l'état des services (systemd)
		* swap : montage de la swap (cf vidéo mémoire plus tard)
		* session
		* path

-------------------------------------------------------------------------------

# LINUX : SYSTEMD - Introduction

<br>

* Suite de d'utilitaires/programmes

		* systemctl
		* journalctl
		* sysctl
		* resolvectl
		* hostnamectl
		* ...

-------------------------------------------------------------------------------

# LINUX : SYSTEMD - Introduction

<br>

```
systemctl list-units -t service
man systemd.service
```

-------------------------------------------------------------------------------

# LINUX : SYSTEMD - Introduction

<br>

```
systemctl get-default
systemctl list-dependencies
systemd-analyze blame
```

-------------------------------------------------------------------------------

# LINUX : SYSTEMD - Introduction

<br>

Les principaux répertoires de configurations :

à éviter de modifier :
	* /usr/lib/systemd/system/
	* /lib/systemd/system/

à modifier et compléter :
	* /etc/systemd/system/
	* /run/systemd/system/

Format de nombreux fichiers en .ini
