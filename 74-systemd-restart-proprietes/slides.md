%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Propriétés de Restarts & Fails


<br>

```
man systemd.service
```

Objectif : comment permettre de l'auto-guerisson de vos services ?

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails

<br>

Deux endroits pour ajouter des propriétés :

	* le [Unit]

	* le [Service]

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails

[Service]

<br>

* le simple restart peu importe l'exit

```
Restart=always (exit)
```

* le simple restart sur un fail (exi diff de 0)

```
Restart=on-failure (exit != 0)
```

Note: mais nécessité de prise en compte du comportement du programmea

Restart=on-abnormal
no
----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails

[Service]

<br>

* temps d'attente entre les restarts (valeur par défaut)

```
RestartSec=1
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails

[Unit]

<br>

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





