%title: LINUX
%author: xavki


# LINUX : Les LOGS


<br>


Objectif : Consulter les logs des applicatifs gérés par systemd ?


----------------------------------------------------------------------------------

# LINUX : Les LOGS

<br>

C'est quoi des logs ??

<br>

	* enregistrement des actions réalisées par les applicatifs

<br>

	* historique

<br>

	* idem pour les programmes dédiés au système

<br>

	* permet de débuguer (retrouver la cause et corriger)

<br>

	* par défaut les logs sont centralisés dans /var/log/

----------------------------------------------------------------------------------

# LINUX : Les LOGS

<br>

	* rotation de logs : cycle de compression des logs

```
syslog
syslog.1
syslog.2.gz
syslog.3.gz
```

----------------------------------------------------------------------------------

# LINUX : Les LOGS


<br>

	* types : 
			* Application Logs
			* Event Logs
			* Service Logs
			* System Logs

<br>

	* format : syslog

```
<timestamp> <user> <service/app[pid]> <message>
```

----------------------------------------------------------------------------------

# LINUX : Les LOGS

<br>

* /var/log/boot.log : logs de démarrage

<br>

* /var/log/cron.log : logs dédiés aux crons

<br>

* /var/log/auth.log (secure) : les logs d'authentification/session et l'utilisation du sudo

<br>

* /var/log/syslog : tous les messages sauf auth

----------------------------------------------------------------------------------

# LINUX : Les LOGS

<br>

* /var/log/messages : tous les messages non critiques

<br>

* /var/log/kern.log : les logs du kernel

<br>

* /var/log/dmesg (dmesg) : les logs relatifs au device driver

<br>

* /var/log/mail.log : logs relatifs au serveur de mail

<br>

* /var/log/daemon.log : logs des services tournant en arrière plan

Note : https://fr.wikipedia.org/wiki/Syslog
