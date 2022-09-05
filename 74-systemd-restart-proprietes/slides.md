%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Propriétés de restart


<br>

```
man systemd.service
```

Objectif : comment apprécier le caractère actif du service ?

----------------------------------------------------------------------------------

Restart=always (exit)
Restart=on-failure (exit != 0)

RestartSec=1 (temps d'attente en seconde pour restart)


* défaut si Restart=always

[Unit]
StartLimitBurst=5 (nombre de fois en fail)
StartLimitIntervalSec=10 (5 fois dans l'interval de 10s)

Rq : et si RestartSec=3 > jamais les 5 fois :)

La solution simple qui fonctionne toujours est de définir StartLimitIntervalSec=0. 

RestartSec à au moins 1 seconde, pour éviter de mettre trop de stress

StartLimitAction=reboot > redémarrage du serveur

[Unit]
Description=My App
StartLimitIntervalSec=30
StartLimitBurst=2
FailureAction=reboot

--no-pager

RuntimeMaxSec=180s


```
[Unit]
Description=Your Daemon
After=network-online.goal
Needs=network-online.goal systemd-networkd-wait-online.service

StartLimitIntervalSec=500
StartLimitBurst=5

[Service]
Restart=on-failure
RestartSec=5s
```



[Unit]
Description=My App
StartLimitIntervalSec=30
StartLimitBurst=2
OnFailure=my-app-recovery.service




systemctl reset-failed my-app
