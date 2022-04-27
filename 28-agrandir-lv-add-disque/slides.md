%title: LINUX
%author: xavki


# LINUX : LVM - Etendre un volume logique & ajout de disque

<br>

	Disks/Partitions > PV > VG > LV > Volumes FS

<br>

* Remplissons un volume

```
df -h
fallocate -l 1500M /srv/xavki
df -h
```

------------------------------------------------------------------------------------

# LINUX : LVM - Etendre un volume logique & ajout de disque

<br>

* vérifions si il reste l'espace allouable au niveau du VG

```
vgs
vgdisplay vg_data
lvextend -L +300M /dev/vg_data/lv_xavki
df -h
```

<br>

* redimensionnons le filesystem (ext4)

```
resize2fs /dev/vg_data/lv_xavki
df -h
```

------------------------------------------------------------------------------------

# LINUX : LVM - Etendre un volume logique & ajout de disque

<br>

* et si on remplit de nouveau ??

```
fallocate -l 1500M /srv/xavki
```

<br>

* ajoutons un nouveau disque

```
pvcreate /dev/sdd1
vgextend vg_data /dev/sdd1
vgs
vgdisplay vg_data
lvextend -l +50%FREE /dev/vg_data/lv_xavki
lvextend -l +100%FREE /dev/vg_data/lv_demo
resize2fs /dev/vg_data/lv_xavki
resize2fs /dev/vg_data/lv_demo
```
