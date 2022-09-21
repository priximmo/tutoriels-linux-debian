%title: LINUX
%author: xavki


# LINUX : SYSTEMD - les Exec & user/group


<br>

```
man systemd.service
```

Objectif : 

* gérées par le [System]

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - les Exec

<br>

ExecStart

<br>

ExecStop

<br>

ExecReload

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - les Exec

<br>

ExecStartPre

<br>

ExecStartPost

<br>

ExecStopPost


----------------------------------------------------------------------------------

# LINUX : SYSTEMD - les Exec


<br>

* Exemple :

```
#/etc/systemd/system/test.service
[Unit]
Description=Test Systemd Service
[Service]
ExecStartPre=/usr/bin/echo -e "\033[0;33m Pre start \033[0m"
ExecStart=/usr/bin/sleep 20;/usr/bin/echo -e "\033[0;33m Pre start \033[0m"
ExecStartPost=/usr/bin/echo -e "\033[0;33m Post start \033[0m"
ExecStop=/usr/bin/pkill -f sleep
ExecStopPost=/usr/bin/echo -e "\033[0;33m Post stop \033[0m"
ExecReload=/usr/bin/echo -e "\033[0;33m Reload \033[0m"
[Install]
WantedBy=multi-user.target
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - les Exec


<br>

* si exit normal du programme

```
RemainAfterExit=true
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - les Exec

<br>

* préciser le user et le group

```
User=oki
Group=oki
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - les Exec

<br>

* action sur le MAINPID

```
ExecStop=/usr/bin/kill -TERM $MAINPID
ExecReload=/bin/kill -HUP $MAINPID
```

Note : si forking utilisation de PIDFile=

