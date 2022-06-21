%title: LINUX
%author: xavki


# LINUX : Udev - Manager les devices


<br>

* dev : devices (périphériques) > /dev (répertoire dynamique)

* Udev = Userspace /dev (devices)

* track les évènements du kernel

* avec le kernel > 2.6 : avant devfs

* udevd = daemon

-------------------------------------------------------------------------------

# LINUX : Udev - Manager les devices

<br>

Multiples enjeux :

		* enjeu desktop (plug souris, etc)

		* nom des devices

		* abstraction du péripériques

		* droits sur les périphériques

-------------------------------------------------------------------------------

# LINUX : Udev - Manager les devices

<br>

* rules : 

		* /etc/udev/rules.conf : conf générale
		* /etc/udev/rules.d/ : règles perso
		* /lib/udev/rules.d/ : règles générales

<br>

* ls /dev/disk
* ls -l /dev/disk/by-id

-------------------------------------------------------------------------------

# LINUX : Udev - Manager les devices

<br>

man udev

<br>

udevadm :

	* monitor : écoute des évènements au niveau du kernel

	* control : modification d'un état

	* trigger : lance un signal

	* test : récupère le résultat de l'exécution

-------------------------------------------------------------------------------

# LINUX : Udev - Manager les devices


<br>

* exemples : 

```
udevadm monitor --udev
udevadm info /dev/nvme0n1
udevadm info -a /dev/nvme0n1
udevadm test /sys/block/sdb
```
