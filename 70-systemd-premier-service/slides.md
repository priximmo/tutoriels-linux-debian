%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Premier Service


<br>

Qu'est-ce qu'un service systemd ?

	* un type d'unité systemd

	* un programme (processus... ou plusieurs)

	* un daemon (tourne en tâche de fond)

	* l'unité pour manager les daemons (start/stop/boot...)

---------------------------------------------------------------------------

# LINUX : SYSTEMD - Premier Service

<br>

Localisation des fichiers de configuration des services

    * /etc/systemd/system : configuration locale
    * /run/systemd/system : configuration du runtime
    * /lib/systemd/system : configuration "packagée"
    * /usr/lib/systemd/system/

---------------------------------------------------------------------------

# LINUX : SYSTEMD - Premier Service

<br>

Constitution d'une configuration de service

```
[Unit]
Description=My app
[Service]
Type=simple
ExecStart=/usr/bin/sleep infinity
[Install]
WantedBy=multi-user.target
```

---------------------------------------------------------------------------

# LINUX : SYSTEMD - Premier Service

<br>

Description : quelques mots sur l'unité en question (multi unités)

Service : type d'unité (informe sur le type de comportement attendu)

ExecStart : le process lancé et ses options et arguments

Wanted-By : niveau de runlevel (utile pour démarrer le programme auto)

Rq: toute édition d'un fichier de conf systemd nécessite

```
systemctl daemon-reload
```

---------------------------------------------------------------------------

# LINUX : SYSTEMD - Premier Service

<br>

* les commandes systemctl de base : lister

```
systemctl
systemctl list-units
systemctl list-units --type service
```

---------------------------------------------------------------------------

# LINUX : SYSTEMD - Premier Service

<br>

* arrêter ou démarrer un service

```
systemctl start hello
systemctl status hello
systemctl stop hello
systemctl restart hello
```

---------------------------------------------------------------------------

# LINUX : SYSTEMD - Premier Service

<br>

D'autres :

* reload : demande aux daemons de recharger leur configuration (si possible)
* try-restart : essaie de redémarrer une unité déjà démarré (pas si stopped)
* reload-or-try-restart : essaie de reload sinon restart

```
ExecReload=/usr/bin/bash -c '/usr/bin/touch /tmp/xavki-$$(date +%%Y%%m%%d%%H%%M%%S)'
```

---------------------------------------------------------------------------

# LINUX : SYSTEMD - Premier Service

<br>

* activer le démarrage au boot de la machine

```
systemctl enable hello
systemctl disable hello
```

---------------------------------------------------------------------------

# LINUX : SYSTEMD - Premier Service

<br>

* vérifier le status (vérification via le code retour)

```
systemctl is-active hello
systemctl is-failed hello
```
