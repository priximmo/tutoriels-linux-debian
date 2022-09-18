%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Gestion de l'environnement


<br>

```
man systemd.service
```

Objectif : Comment changer le répertoire de travail, variables d'env ?

* gérées par le [System]

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

* WorkingDirectory

```
echo "Test WorkingDirectory" > /tmp/xavki.txt
```

```
[Service]
Type=simple
WorkingDirectory=/tmp/
ExecStart=/usr/bin/cat xavki.txt
```

Note : ne fonctionne pour le chemin (path) vers le script

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

* les permissions sur les répertoires :

```
[Service]
Type=simple
ExecStart=/usr/bin/ls /home/oki
InaccessibleDirectories=/home
```
ReadWriteDirectories=
ReadOnlyDirectories=

Note : ajouter "-" pour éviter une erreur si non existant

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

* protection de la home (true/false/read-only)

ProtectHome > /home/ ou /run/user/ non accesible

* ProtectSystem (true/false/full) :

ProtectSystem > /usr/ en read-only
		* si full, /etc/ aussi 




----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

* le répertoire temporaire privé (True/False)


```
[Service]
Type=simple
ExecStart=/bin/bash -c "echo toto > /tmp/xavki.txt"
PrivateTmp=True
```

Note :
	* pour la sécurité, suppression /tmp/ & /var/tmp/ du process
	* idem pour les networks & pour les devices

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

*  répertoire dédié au process (clean au stop)

```
[Service]
Type=simple
ExecStart=/usr/bin/sleep infinity
RuntimeDirectory=xavki
```

RuntimeDirectoryMode : pour spécifier le mode (permissions sur le répertoire)


----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

* définir des variables d'environnement

Environment=NODE_ENV=production PORT=1494

```
[Service]
Environment=ENV=production APP=myapp
Type=simple
ExecStart=/bin/bash -c "/usr/bin/echo $ENV; /usr/bin/echo $APP"
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Gestion de l'environnement

<br>

* par fichier

EnvironmentFile=/etc/myapp/environment

```
[Service]
EnvironmentFile=/etc/myapp/environment
Type=simple
ExecStart=/bin/bash -c "/usr/bin/echo $ENV; /usr/bin/echo $APP"
```
