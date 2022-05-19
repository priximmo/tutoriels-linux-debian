%title: LINUX
%author: xavki


# LINUX : RAID 1 - Ajout, Suppression de disques, Manips


<br>

* ajouter un disque pour jouer :)

<br>

* sortir un disque de la grappe raid (array)

```
mdadm --manage /dev/md0 --fail /dev/sdc1
mdadm --manage /dev/md0 --remove /dev/sdc1
```

* remettre

```
mdadm --manage /dev/md0 --re-add /dev/sdc1
mdadm --manage /dev/md0 --add /dev/sdc1
```

* si nécessaire

```
mdadm --stop /dev/md0
mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
```

-------------------------------------------------------------------

# LINUX : RAID 1 - Ajout / Suppression de disques


<br>

* ajouter le nouveau disque

```
mdadm --manage /dev/md0 --add /dev/sdd1
mdadm -D /dev/md0
cat /proc/mdstat
```

<br>

* si remplacement direct

```
mdadm --manage /dev/md0 --replace /dev/sdc1 --with /dev/sdd1
```

-------------------------------------------------------------------

# LINUX : RAID 1 - Ajout / Suppression de disques

<br>

* augmenter le nombre de disques mirrorés

```
mdadm --grow /dev/md0 --raid-devices 3 --add /dev/sdc1
mdadm -D /dev/md0
```

Attention : en raid 1 pas d'extension de volume de la grappe
	ex : si raid 0 > extension du volume > resize2fs

-------------------------------------------------------------------

# LINUX : RAID 1 - Ajout / Suppression de disques

<br>

* stopper un array Raid

```
mdadm --stop /dev/md0
mdadm --stop --scan
```

<br>

* redémarrer un array

```
mdadm --assemble /dev/md0
mdadm --assemble --scan
```

-------------------------------------------------------------------

# LINUX : RAID 1 - Ajout / Suppression de disques

<br>

* passer en read-only

```
umount /dev/md0
mdadm --manage /dev/md0 --readonly
mount /dev/md0
```

<br>

* repasser en lecture/écriture

```
mdadm --manage /dev/md0 --readwrite
```
