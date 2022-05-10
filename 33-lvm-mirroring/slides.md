%title: LINUX
%author: xavki


# LINUX : LVM - Comment mirrorer/copier un volume ?

<br>


2 partitions

pvcreate /dev/sdb1 /dev/sdc1

vg vg_data /dev/sdb1 /dev/sdc1

Physical Extents = blocks LVM (taille > nombre)

	* petits LV = petits extents

	* gros LV = gros extents

	* default 4M (2M > 128M)

	* vgcreate -s (spécifier la taille des extents)

lvcreate -L 200M -n lv_xavki -m1 /dev/vg_data

(-m : nombre de copie)

lvs : indique l'état de la synchronisation
	(-o +devices -a)

mkfs.ext4 /dev/vg_data/lv_xavki

mount -t ext4 /dev/vg_data/lv_xavki /srv/xavki

touch /srv/xavki/demo1.txt

* test : suppression d'un PV

attention : si uniquement des LV mirrorés

pvremove /dev/sdb1
lvdisplay
lvs

vgreduce --removemissing vg_data --force

* remettre la partition manquante

pvcreate /dev/sdb1

vgextend vg_data /dev/sdb1

* réparation du LV mirroré (sync extents)

lvconvert --repair /dev/vg_data/lv_xavki
lvs -a -o +devices

* comment passer d'un LV mirroré à un LV simple

lvconvert -m 0 /dev/vg_data/lv_xavki /dev/sdb1
lvs -a -o +devices

* comment mirroré un LV simple ?

lvconvert -m 1 /dev/vg_data/lv_xavki /dev/sdb1

* ajouter un PV pour ajouter un mirroring ?

vgextend vg_data /dev/sdd1
lvconvert -m 2 /dev/vg_data/lv_xavki /dev/sdd1


