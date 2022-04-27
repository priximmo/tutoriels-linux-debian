%title: LINUX
%author: xavki


# LINUX : LVM - Réduire un volume logique

<br>

	Disks/Partitions > PV > VG > LV > Volumes FS

<br>

```
lvs
lvdisplay
```

<br>

* démonter le volume en question

```
umount /srv/demo
```

-----------------------------------------------------------------------------------

# LINUX : LVM - Réduire un volume logique

<br>

* réaliser un fsck

```
e2fsck -f /dev/vg_data/lv_demo
```

<br>

* réduire le filesystème à la taille souhaitée

```
resize2fs /dev/vg_data/lv_demo 100M
```

-----------------------------------------------------------------------------------

# LINUX : LVM - Réduire un volume logique

<br>

* réduire le LV et resize

```
lvreduce -L 100M /dev/vg_data/lv_demo
resize2fs /dev/vg_data/lv_demo
mount /srv/demo
vgs
```
