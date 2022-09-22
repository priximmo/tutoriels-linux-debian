%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Logs & Journalctl


<br>

```
man systemd.service
```

Objectif : Consulter les logs des applicatifs gérés par systemd ?


----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Logs & Journalctl

<br>

* journalctl : consulter vos logs via une commande

```
journalctl
```

<br>

* pour une unité

```
journalctl -u hello2
```

<br>

* l'équivalent de tail

```
tail -f /var/log/syslog
journalctl -fu hello
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Logs & Journalctl

<br>

* par applicatif

```
journalctl /usr/bin/sleep
```

<br>

* par log level

```
journalctl -p err
```

<br>

* cumuler

```
journalctl /usr/bin/sleep -u hello1
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Logs & Journalctl

<br>

* par date

```
journalctl --since "2022-01-01 01:00:00" --until "2022-09-21 18:13:00"
```

<br>

* mode courant

```
journalctl --since yesterday
journalctl --since "1 hour ago"
```

<br>

* sortie json

```
journalctl -u hello2 -o json
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Logs & Journalctl

<br>

* logs level

0 	Emergency 	emerg 		: système non utilisable
1 	Alert 	alert 				: correction à apporter immédiatement
2 	Critical 	crit 				: conditions critiques (hardware)
3 	Error 	err 					: erreur
4 	Warning 	warning 		: précvention
5 	Notice 	notice 				: pas de problème mais à noter 
6 	Informational 	info 	: information
7 	Debug 	debug 				: maximum d'information

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Logs & Journalctl

<br>

* utilisation de syslog (défaut)

```
StandardOutput=syslog
StandardError=syslog
```

<br>

* spécifier une autre destination

```
StandardOutput=append:/var/log/xavki.log
StandardError=append:/var/log/xavki_err.log
```

inherit, null, tty, journal, kmsg
journal+console, kmsg+console
file:path, append:path, truncate:path, socket, fd:name

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Logs & Journalctl

<br>

* définir un identifiant spécifique

```
SyslogIdentifier=xavki
```

<br>

* ajouter des champs

```
LogExtraFields
```

<br>

* limiter le nombre de messages par intervales

```
LogRateLimitIntervalSec
LogRateLimitBurst
```
