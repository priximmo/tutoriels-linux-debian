%title: LINUX
%author: xavki


# LINUX : Udev - Démo - Créer un nouveau SymLink


<br>

udevadm :

	* monitor : écoute des évènements au niveau du kernel

	* control : modification d'un état

	* trigger : lance un signal

	* test : récupère le résultat de l'exécution

----------------------------------------------------------------------------------------------

# LINUX : Udev - Démo - Créer un nouveau SymLink

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

# LINUX : Udev - Démo - Créer un nouveau SymLink

<br>

Recherche dans le devpath (les éléments des parents)

	* KERNELS : recherche dans le devpath

	* SUBSYSTEMS : recherche dans le devpath le nom d'un sous système

	* DRIVERS : recherche le driver du device dans le subpath

----------------------------------------------------------------------------------------------

# LINUX : Udev - Démo - Créer un nouveau SymLink

<br>

Utilisation des attributs

	* ATTR{<attribut>} : recherche dans les attributs du device

	* ATTRS{<attributs>} : idem dans les parents

	* ENV{<propriété>) : utilisation de la propriété du device

----------------------------------------------------------------------------------------------

# LINUX : Udev - Démo - Créer un nouveau SymLink

<br>

```
udevadm monitor --udev
udevadm info -a /dev/nvme0n1
udevadm info -a /dev/nvme0n1 -q property
udevadm info -a /dev/nvme0n1 -q all
udevadm info -a /dev/nvme0n1 -q all --help
```

----------------------------------------------------------------------------------------------

# LINUX : Udev - Démo - Créer un nouveau SymLink

<br>

Les opérateurs:

	* "==" : égal à

	* "!=" : différent de

	* "="  : affecte/définit des valeurs

	* "+=" : ajoute des éléments à une variable déjà définie

	* "-=" : retire la valeur de la variable

	* ":=" : définit une valeur en dernière position et empêhce tout changement

----------------------------------------------------------------------------------------------

# LINUX : Udev - Démo - Créer un nouveau SymLink

<br>

Petit exemple : création d'un nouve device pointant vers /dev/sdb

* notre règle

```
KERNEL=="sd*", ENV{ID_SERIAL}=="xxxxx", SYMLINK+="sdx", RUN+="/bin/sh -c '${date +%Y%m%d} - echo SDX created' > /tmp/xavki.log"
```

* pour tester la règle

```
udevadm trigger --typ devices --action change
```
