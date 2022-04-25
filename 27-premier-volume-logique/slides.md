%title: LINUX
%author: xavki


# LINUX : LVM - Premier Volume Logique

<br>

	Disks/Paritions > PV > VG LV > Volumes FS

<br>

Exemple :

	* ajout de 2 disques 1G

	* monter un /srv/xavki de 1,5G

	* monter un /srv/demo de 200M

----------------------------------------------------------------------------

# LINUX : LVM - Premier Volume Logique

<br>

1- création et ajout des disques sur virtualbox

2- partitionnement des disques

3- création des physical volumes (PV)

```
pvcreate /dev/sdb1 /dev/sdc1
pvdisplay
```

----------------------------------------------------------------------------

# LINUX : LVM - Premier Volume Logique

<br>

4- création d'un volume unique vg_data

```
vgcreate vg_data /dev/sdb1 /dev/sdc1
vgdisplay
```

5- création des volumes logiques lv_xavki & lv_demo

```
lvcreate -n lv_xavki -L 1.5G vg_data
lvcreate -n lv_demo -L 200M vg_data
```

----------------------------------------------------------------------------

# LINUX : LVM - Premier Volume Logique

<br>

6- formatons le FS

```
mkfs.ext4 /dev/vg_data/lv_xavki
mkfs.ext4 /dev/vg_data/lv_demo
```

7- montage des volumes

```
mkdir /srv/{xavki,demo}
```

```
/dev/vg_data/lv_xavki  /srv/xavki ext4 nofail 0 0
/dev/vg_data/lv_demo  /srv/demo ext4 nofail 0 0

mount -a
df -h
```
