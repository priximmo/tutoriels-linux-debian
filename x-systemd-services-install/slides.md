%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Les Dépendances


<br>

```
man systemd.service
```

Objectif : comment permettre de l'auto-guerisson de vos services ?

* gérées par le [Unit]

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails

<br>

Deux services hello1 et hello2

```
[Unit]
Description=Hello
[Service]
Type=simple
ExecStart=/usr/bin/sleep 50s
[Install]
WantedBy=multi-user.target
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails

<br>

Différentes propriétés de la section Unit :

	* After

	* Before

	* Wants

	* Requires

	* Requisite

	* BindsTo

	* PartOf

	* Conflicts

```
systemctl list-dependencies test.service --all --reverse
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails


<br>

After : lancé après peu importe l'état (ordre)


<br>

Before : idem mais après

<br>

Wants : devrait être activée avec d'autres unités (non obligatoire)

<br>

Requisite : n'inclus pas de notion d'ordre (même transaction > After) 

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails


<br>

PartOf : dépendance parent au restart et stop

* start de hello1 rien sur hello2

```
systemctl stop hello1 hello2
systemctl status hello1 hello2
systemctl start hello1
```

* stop de hello1 entraine stop de hello2

```
systemctl start hello1 hello2
systemctl status hello1 hello2
systemctl stop hello1
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails


<br>

Requires :

	* démarrage des services listés

	* arrêt sur un des services listés

* démarrage des services listés

```
systemctl stop hello1 hello2
systemctl status hello1 hello2
systemctl start hello1
systemctl status hello1 hello2 # pas de dépendance
systemctl stop hello1
systemctl start hello2 
systemctl status hello1 hello2 # dépendance
```

* arrêt d'un des services listés

```
systemctl start hello1 hello2
systemctl status hello1 hello2
systemctl stop hello1
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails


<br>

BindTo :

	* démarrage des services listés

	* arrêt sur un des services listés

	* mais sur failed du service listé stop

```
systemctl start hello1 hello2
systemctl status hello1 hello2
kill -9 <pid_service_listé>
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails


<br>

Conflicts :

	* si hello1 est activé alors b est inactivé

	* inversement
