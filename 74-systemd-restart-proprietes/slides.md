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

```
[Unit]
Description=My app Hello
[Service]
ExecStart=/usr/bin/sleep 10s
[Install]
WantedBy=multi-user.target
```


----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails

[Service]

<br>

* le simple restart peu importe l'exit (exemple : sleep)

```
Restart=always (exit)
```

* le simple restart sur un fail (exi diff de 0)

```
Restart=on-failure (exit != 0)
```

Note: mais nécessité de prise en compte du comportement du programmea

Restart=on-abnormal

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


[Service]

<br>

* limiter la durée d'un service (mais restart potentiel)

```
[Service]
RuntimeMaxSec=180s
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails


[Unit]

<br>

* défaut si Restart=always

```
[Unit]
StartLimitBurst=5 (nombre de fois en fail)
StartLimitIntervalSec=10 (5 fois dans l'interval de 10s)
```

Rq : et si RestartSec=3 > jamais les 5 fois :)

La solution simple qui fonctionne toujours est de définir StartLimitIntervalSec=0. 

RestartSec à au moins 5 secondes, pour éviter de mettre trop de stress

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails

[Unit]

<br>

* pour limiter le nombre de restart (2)

```
[Unit]
Description=My app Hello
StartLimitBurst=2
StartLimitIntervalSec=300
[Service]
ExecStart=/usr/bin/sleep 10s
Restart=always
RestartSec=5s
[Install]
WantedBy=multi-user.target
```


----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails


[Unit]

<br>

* pour cadencer les restart sans les limiter du tout

```
[Unit]
Description=My app Hello
StartLimitBurst=2
StartLimitIntervalSec=300
[Service]
ExecStart=/usr/bin/sleep 10s
Restart=always
RestartSec=5s
[Install]
WantedBy=multi-user.target
```


----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails


[Unit]

<br>

* redémarrer le serveur en cas de fail :

```
[Unit]
Description=My App
StartLimitIntervalSec=30
StartLimitBurst=2
FailureAction=reboot
```

SuccessAction=
StartLimitAction=reboot > reboot si startlimitaction activé (burst/interval)
OnFailure=my-app-recovery.service

