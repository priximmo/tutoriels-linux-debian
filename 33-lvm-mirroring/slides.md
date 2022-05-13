%title: LINUX
%author: xavki


# LINUX : LVM - Comment mirrorer/copier un volume ?

<br>

Physical Extents = blocks LVM (taille > nombre)

	* petits LV = petits extents

	* gros LV = gros extents

	* default 4M (2M > 128M)

	* vgcreate -s (spécifier la taille des extents)

----------------------------------------------------------------------------------------------------

# LINUX : LVM - Comment mirrorer/copier un volume ?

<br>

* commençons à partir de 2 partitions

```
pvcreate /dev/sdb1 /dev/sdc1
vgcreate vg_data /dev/sdb1 /dev/sdc1
```

----------------------------------------------------------------------------------------------------

# LINUX : LVM - Comment mirrorer/copier un volume ?

<br>

* puis créons un LV mirroré

```
lvcreate -L 200M -n lv_xavki -m1 /dev/vg_data
lvs -o +devices -a
```

Rq : -m nombre de copie

----------------------------------------------------------------------------------------------------

# LINUX : LVM - Comment mirrorer/copier un volume ?

<br>

* n'oublions pas le formatage de notre FS

```
mkfs.ext4 /dev/vg_data/lv_xavki
mount -t ext4 /dev/vg_data/lv_xavki /srv/xavki
touch /srv/xavki/demo1.txt
```

----------------------------------------------------------------------------------------------------

# LINUX : LVM - Comment mirrorer/copier un volume ?

<br>

* test : remplacement d'un PV

attention : si uniquement des LV mirrorés

```
lvconvert --replace /dev/sdb1 /dev/vg_data/lv_xavki /dev/sdd1
lvdisplay
lvs
```

----------------------------------------------------------------------------------------------------

# LINUX : LVM - Comment mirrorer/copier un volume ?

<br>

* réparation du LV mirroré (sync extents)

```
lvconvert --repair /dev/vg_data/lv_xavki
lvs -a -o +devices
```

----------------------------------------------------------------------------------------------------

# LINUX : LVM - Comment mirrorer/copier un volume ?

<br>

* comment passer d'un LV mirroré à un LV simple ?

```
lvconvert -m 0 /dev/vg_data/lv_xavki /dev/sdd1
lvs -a -o +devices
```

----------------------------------------------------------------------------------------------------

# LINUX : LVM - Comment mirrorer/copier un volume ?

<br>

* inversement, comment mirroré un LV simple ?

```
lvconvert -m 1 /dev/vg_data/lv_xavki /dev/sdc1
```

----------------------------------------------------------------------------------------------------

# LINUX : LVM - Comment mirrorer/copier un volume ?

<br>

* comment ajouter un PV pour ajouter un mirroring ?

```
vgextend vg_data /dev/sdd1
lvconvert -m 2 /dev/vg_data/lv_xavki /dev/sdd1
```
