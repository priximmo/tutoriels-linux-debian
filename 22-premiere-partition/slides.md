%title: LINUX
%author: xavki


# LINUX : Première PARTITION


<br>

Partitions :

		* devices

		* découpage d'un disque en sous éléments

		* isolation et espace dédié (différents FS, OS, montages...)

		* peut être redimensionnée (attenion quand même)

-----------------------------------------------------------------------------------

# LINUX : Première PARTITION


<br>

Procédure simplifiée :

<br>

	1 - ajouter un disque

<br>

	2 - rechercher le disk : fdisk -l

<br>

	3 - Lancer fdisk sur /dev/<disk>

<br>

	4 - n pour créer une partition

-----------------------------------------------------------------------------------

# LINUX : Première PARTITION


<br>
4 primaire + étendues

primaire = partitions dans le MBR du disque (découverte au boot)

étendue = fractionnement d'une partition primaire (conteneur)

<br>

	5 - p pour une partition primaire

<br>

	6 - t pour définir le type (linux = 83)

<br>

	7 - w enregistrer

<br>

	8 - cat /proc/partition partx /dev/<partition>

<br>

	9 - install xfsprogs

	10 - mkfs.xfs /dev/<partition>

	11 - création dir & montage
