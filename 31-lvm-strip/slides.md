%title: LINUX
%author: xavki


# LINUX : LVM - LV strippé

<br>

	Disk > Partitions > PV > VG > LV > Volume FS

<br>

Intérêts ?

		* RAID 0

		* agrégation de disque en répartissant l'écriture/lecture

		* performance (cumul iops)

--------------------------------------------------------------------------------------------------

# LINUX : LVM - LV strippé

<br>

* création des PV (physical volumes) - ex 2 partitions

```
pvcreate /dev/sd[b-c]1
```

--------------------------------------------------------------------------------------------------

# LINUX : LVM - LV strippé

<br>

* création du volume group

```
vgcreate -v vg_data /dev/sd[b-c]1
```

--------------------------------------------------------------------------------------------------

# LINUX : LVM - LV strippé

<br>

* création du LV strippé 

```
lvcreate -L 1G -n lv_strip -i 2 -I 4k /dev/vg_data
lvdisplay -m /dev/vg_data/lv_strip
lvs -o +devices
dmsetup table
```

--------------------------------------------------------------------------------------------------

# LINUX : LVM - LV strippé

<br>

* puis montage

```
mkfs.ext4 /dev/vg_data/lv_strip
mount -t ext4 /dev/vg_data/lv_strip /srv/xavki
```

<br>

* test

```
dd if=/dev/zero of=/srv/xavki/test.txt bs=1G count=1 oflag=direct
```
