%title: LINUX
%author: xavki


# LINUX : Udev - Manager les devices


<br>

* dev : devices (périphériques) > /dev (répertoire dynamique)

* Udev = Userspace /dev (devices)

* track les évènements du kernel

* avec le kernel > 2.6 : avant devfs

* udevd = daemon

<br>

Multiples enjeux :

		* enjeu desktop (plug souris, etc)

		* nom des devices

		* abstraction du péripériques

		* droits sur les périphériques

<br>

man udev

udevadm :

	* monitor : écoute des évènements au niveau du kernel

	* control : modification d'un état

	* trigger : lance un signal

	* test : récupère le résultat de l'exécution




udevadm monitor --udev
udevadm info /dev/nvme0n1
udevadm info -a /dev/nvme0n1

* rules : 

		* /etc/udev/rules.conf : conf générale
		* /etc/udev/rules.d/ : règles perso
		* /lib/udev/rules.d/ : règles générales

* ls /dev/disk
* ls -l /dev/disk/by-id


KERNEL
SUBSYSTEM
DRIVER
NAME
SYMLINK
ATTR{nom_attribut}
PROGRAM

       "=="
           Compare for equality.

       "!="
           Compare for inequality.

       "="
           Assign a value to a key. Keys that represent a list are reset and only this single value is assigned.

       "+="
           Add the value to a key that holds a list of entries.

       "-="
           Remove the value from a key that holds a list of entries.

       ":="
           Assign a value to a key finally; disallow any later changes.


$variable = variables réutilisable/substituables


 oki@doki ~/gitlab.com/linux (master) $ ▶ udevadm 
control       info          monitor       settle        test          test-builtin  trigger  


udevadm monitor --udev

https://www.thegeekdiary.com/how-to-set-custom-device-names-using-udev-in-centos-rhel-7/
