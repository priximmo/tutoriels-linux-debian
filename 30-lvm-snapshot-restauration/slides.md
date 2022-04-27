%title: LINUX
%author: xavki


# LINUX : LVM - Créer et restaurer un Snapshot

<br>

	Disk > Partitions > PV > VG > LV > Volume FS

<br>

* créer un snapshot de LV 

```
touch /srv/xavki/demo1.txt
lvcreate -L 1G -s -n snap_lv_data /dev/vg_data/lv_xavki
sudo lvdisplay
# lvs
touch /srv/xavki/demo2.txt
```

Note : attention au volume libre du VG

--------------------------------------------------------------------------

# LINUX : LVM - Créer et restaurer un Snapshot

<br>

* on peut vérifier

```
sudo mount /dev/vg_data/snap_lv_data /mnt/snap_check
ls /mnt/snap_check
sudo umount /mnt/snap_check
```

<br>

* vérifier la taille utilisée 

```
sudo lvs /dev/vg_data/snap_lv_data
```

--------------------------------------------------------------------------

# LINUX : LVM - Créer et restaurer un Snapshot

<br>

* attention ne pas atteindre les 100% sinon plus de snap

* étendre un snapshot manuellement

```
lvextend -L +100M /dev/vg_data/snap_lv_data
```

--------------------------------------------------------------------------

# LINUX : LVM - Créer et restaurer un Snapshot

<br>

* activer l'extension automatique des snapshots

```
vim /etc/lvm/lvm.conf
snapshot_autoextend_threshold = 100
# Setting this to 100 disables automatic extension
snapshot_autoextend_percent = 20
```

--------------------------------------------------------------------------

# LINUX : LVM - Créer et restaurer un Snapshot

<br>

* restauration du snapshot

```
lvconvert --merge /dev/vg_data/snap_lv_data
ls /srv/xavki/
# parfois  lvchange -an et lvchange -ay
```
