%title: LINUX
%author: xavki


# LINUX : LVM - Introduction

<br>

LVM : Logical Volume Manager

```
man 8 LVM
```

<br>

Intérêts LVM : 

		* partitionnement limité sur la gestion des secteurs

		* partitionnement risqué

		* partiionnement difficile si plusieurs disques (cumul)

		* LVM apporte un moyen snapshot (hormis certains FS)

		* LVM apport un moyen de stripper ( parallélisation des écritures)

		* LVM ne résoud pas la haute dispo des disques (niveau Raid)

-------------------------------------------------------------------------------------------

# LINUX : LVM - Introduction

<br>

SANS

	Disk > partitions > filesystem

<br> 

AVEC

	Disk > Physical Volumes > Volume Groups > Logical Volumes > FS

ou

	Disk > partitions > PV > VG > LV > FS

<br>

ATTENTION :
	Type de partition à passer de Linux (83) en Linux LVM (8e)


-------------------------------------------------------------------------------------------

# LINUX : LVM - Introduction

<br>

PHYSICAL VOLUME (PV)

	* représentation d'un disque physique, d'une partition, d'un volume RAID, baie SAN

	* une sort de déclaration des disk utilisable

Principales commandes :

	* pvcreate: création d'un PV
	* pvdisplay ou pvs : afficher la liste des PV
	* pvremove : supprimer un PV
	* pvresize : redimensionner un PV
	* pvscan : lister les disques pour les PV

-------------------------------------------------------------------------------------------

# LINUX : LVM - Introduction

<br>

VOLUME GROUPE (VG)

	* couche logique contenant à minima 1 PV

	* permet d'agréger les PV 

	* utilisable via les volumes logiques (découpage...)

Principales commandes :

	* vgcreate : créer un volume groupe
	* vgdisplay ou vgs : lister les VG
	* vgremove : supprimer un VG
	* vgreduce : pour réduire la taille des VG
	* vgrename : pour changer le nom d'un VG
	* vgconvert : changer les metadatas
	* vgextend : ajouter un PV à un VG existant
	* vgsplit : couper en 2 un VG
	* vgmerge : regrouper 2 VG en un
	* vgscan : lister les disques d'un LV

------------------------------------------------------------------------------------------

# LINUX : LVM - Introduction

<br>

LOGICAL VOLUME (LV)

	* un à plusieurs LV par VG

	* un LV est utilisable pour un filesystem (volume)

	* fonctionnalités avancées : stripping, taille de blocs, snapshots...

Principales commandes :

	* lvcreate: créer un volume logique (snapshot, stripping...)
	* lvdisplay ou lvs : afficher les information d'un ou des LV
	* lvremove : supprimer un LV
	* lvextend : agrandir un LV
	* lvconvert : pour restaurer un snapshot ou convertir
	* lvresize : redimensionner un LV
	* lvreduce : pour réduire la taille d'un LV
	* lvscan : scanner tous les disques d'un LV
	
