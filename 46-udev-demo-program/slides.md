%title: LINUX
%author: xavki


# LINUX : Udev - Démo - Créer un device custom


<br>

SCSI = Small Computer System Interface

Protocole dédié aux interfaces de stockage (disques)

C'est une connexion : carte dédiée / bus (identification)

<br>

Les Keywords (cumulatif séprateur ","):

	* ACTION : sur quel action du device agir 
		add / remove / change

	* DEVPATH

	* KERNEL : nom de l'évènement du device (généralement device)

	* NAME : pour le nom des interfaces réseaux

	* PROGRAM : sélectionner sur une commande

	* RUN : lance de commande

----------------------------------------------------------------------------------------------

# LINUX : Udev - Démo - Créer un device custom

<br>

Recherche dans le devpath (les éléments des parents)

	* KERNELS : recherche dans le devpath

	* SUBSYSTEMS : recherche dans le devpath le nom d'un sous système

	* DRIVERS : recherche le driver du device dans le subpath

----------------------------------------------------------------------------------------------

# LINUX : Udev - Démo - Créer un device custom

<br>

Utilisation des attributs

	* ATTR{<attribut>} : recherche dans les attributs du device

	* ATTRS{<attributs>} : idem dans les parents

	* ENV{<propriété>) : utilisation de la propriété du device

----------------------------------------------------------------------------------------------

# LINUX : Udev - Démo - Créer un device custom

<br>

```
udevadm monitor --udev
udevadm info -a /dev/nvme0n1
udevadm info -a /dev/nvme0n1 -q property
udevadm info -a /dev/nvme0n1 -q all
udevadm info -a /dev/nvme0n1 -q all --help
```

----------------------------------------------------------------------------------------------

# LINUX : Udev - Démo - Créer un device custom

<br>

Les opérateurs:

	* "==" : égal à

	* "!=" : différent de

	* "="  : affecte/définit des valeurs

	* "+=" : ajoute des éléments à une variable déjà définie

	* "-=" : retire la valeur de la variable

	* ":=" : définit une valeur en dernière position et empêhce tout changement

----------------------------------------------------------------------------------------------

# LINUX : Udev - Démo - Créer un device custom

<br>

Petit exemple : récupérer l'identifiant scsi pour repérer un disque et lui affecter un device

* récupération de l'id scsi

```
/usr/lib/udev/scsi_id -g -u /dev/sdb
```

* notre règle

```
KERNEL=="sd*",
ENV{DEVTYPE}=="disk",
PROGRAM=="/usr/lib/udev/scsi_id -g -u -d $devnode",
RESULT=="xxx",
RUN+="/bin/sh -c 'mknod /dev/xavki b $major $minor; chown xavki:xavki/dev/xavki; chmod 660 /dev/xavki'"
```

* pour tester la règle

```
udevadm trigger --typ devices --action change
```
