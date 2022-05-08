%title: LINUX
%author: xavki


# LINUX : LVM - Remplacer un disque

<br>

* avant :

	/dev/sdb1 > pv > vg > lv > volume fs

<br>

* après

	/dev/sdc1 > pv > vg > lv > volume fs


Exemple : remplacement d'un disque

--------------------------------------------------------------------------------------------------

# LINUX : LVM - Remplacer un disque

<br>

0. Ajout d'un disque

<br>

1. création de la partition (optionnelle)

<br>

2. création du PV du nouveau disque

--------------------------------------------------------------------------------------------------

# LINUX : LVM - Remplacer un disque

<br>

3. ajout du nouveau PV au VG existant

```
pvextend vg_data /dev/sdc1
```

<br>

4. démonter le volume

```
umount /srv/xavki
# si possible faire un backup
```

--------------------------------------------------------------------------------------------------

# LINUX : LVM - Remplacer un disque

<br>

5. déplacement des extends de l'ancien PV vers les autres PV (nouveau)

```
pvmove /dev/sdb1
pvmove /dev/sdb1 /dev/sdc1
```

<br>

6. retirer l'ancien PV du VG

```
vgreduce vg_data /dev/sdb1
```

<br>

7. remonter

```
mount -t ext4 /dev/vg_data/lv_xavki /srv/xavki
```
