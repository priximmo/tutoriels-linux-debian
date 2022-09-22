%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Gestion de l'environnement


<br>

```
man systemd.service
```

Objectif : Consulter les logs des applicatifs gérés par systemd ?


----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

C'est quoi des logs ??

	* enregistrement des actions réalisées par les applicatifs

	* historique

	* idem pour les programmes dédiés au système

	* permet de débuguer (retrouver la cause et corriger)

	* par défaut les logs sont centralisés dans /var/log/

	* rotation de logs : cycle de compression des logs

	* types : 
			* Application Logs
			* Event Logs
			* Service Logs
			* System Logs

	* format : syslog

```
<date> <user> <service/app[pid]> <message>
```


* /var/log/boot.log : logs de démarrage

* /var/log/cron.log : logs dédiés aux crons

* /var/log/auth.log (secure) : les logs d'authentification/session et l'utilisation du sudo

* /var/log/syslog : tous les messages sauf auth

* /var/log/messages : tous les messages non critiques

* /var/log/kern.log : les logs du kernel

* /var/log/dmesg (dmesg) : les logs relatifs au device driver

* /var/log/mail.log : logs relatifs au serveur de mail

* /var/log/daemon.log : logs des services tournant en arrière plan

StandardOutput=syslog
StandardError=syslog
StandardOutput=append:/var/log/bird_watching.log
StandardError=append:/var/log/bird_watching.log
SyslogIdentifier=bird_watching

Environment=NODE_ENV=production PORT=1494


RequiresMountsFor=

AssertPathExists=/srv/http

PrivateTmp=true


    Use built-in options to sandbox your service instead of chrooting it. Specifically:

    RemoveIPC=true and PrivateTmp=true. These ensure that the lifetime of the IPC objects and temporary files created by the executed process is bound to the runtime of the service. Since /tmp and /var/tmp are usually the only world-writable directories on a system this ensures that the unit cannot leave files around after termination.
    NoNewPrivileges=true and RestrictSUIDSGID=true. These ensure that processes invoked cannot take benefit or create SUID/SGID files or directories.
    ProtectSystem=strict and ProtectHome=read-only prohibits the service from writing to anywhere in your filesystem (exceptions are /dev/ /proc/ and /sys/. In order to allow the service to write to certain directories, they have to be allow-listed using ReadWritePaths=.
    RuntimeDirectory= to assign a runtime directory to the service, which is owned by the service's user, and removed automatically when the system is terminated.
Nice=



