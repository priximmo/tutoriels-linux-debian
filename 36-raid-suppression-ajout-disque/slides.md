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

<br>

* remettre

```
mdadm --manage /dev/md0 --re-add /dev/sdc1
mdadm --manage /dev/md0 --add /dev/sdc1
```

<br>

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
mdadm --manage /dev/md0 --add /dev/sde1
mdadm --manage /dev/md0 --replace /dev/sdc1 --with /dev/sde1
```

<br>

* étendre

```
mdadm --grow /dev/md0 --raid-devices 4 --add /dev/sde1
```

