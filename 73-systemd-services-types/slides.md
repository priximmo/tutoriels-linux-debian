%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Types de Services


<br>

```
man systemd.service
```

Objectif : comment apprécier le caractère actif du service ?

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Types de Services

<br>

Types :

	* oneshot : pour lancer une fois (exemple au démarrage), reste en attente

	* exec : lancement d'un simple process vérifié sur le simple execve

	* simple : daemon d'un simple process (classique) - attente de fork (1er)

	* forking : l'ExecStart doit utiliser le syscall fork()

	* dbus : reste actif tant que le bus est utilisé

	* notify

	* idle

	* exec

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Types de Services

<br>

* OneShot

```
[Unit]
Description=My Hello app
[Service]
Type=oneshot
ExecStart=/usr/bin/sleep 10
RemainAfterExit=true
[Install]
WantedBy=multi-user.target
```

Note : attention Remain After Exit (garde le caractère actif)

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Types de Services

<br>

* Exec (attend le syscall execve)

```
[Service]
Type=exec
ExecStart=/usr/bin/sleep infinity
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Types de Services

<br>

* Simple (attend le fork de systemd)

```
[Service]
Type=Simple
ExecStart=/usr/bin/sleep infinity
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Types de Services

<br>

* Idle

```
[Service]
Type=Idle
ExecStart=/usr/bin/sleep infinity
```

Note : évite de lancer le service en même temps
	* attend que d'autres process en cours d'activation
	* lancement au bout de 5s quand même

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Types de Services

<br>

* Forking (attend le syscall fork() )

```
[Service]
Type=forking
ExecStart=/bin/bash -c '/usr/bin/sleep 2s; /usr/bin/sleep 500s &'
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Types de Services

<br>

* Notify

```
[Service]
Type=notify
ExecStart=bash -c '/usr/bin/sleep 20s; systemd-notify --ready; /usr/bin/sleep infinity'
NotifyAccess=all
```

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Types de Services

<br>

* D-Bus

```
[Service]
Type=dbus
BusName=dev.jambor.Test
ExecStart=bash -c 'sleep 2; dbus-test-tool echo --system --name=dev.jambor.Test'
```
