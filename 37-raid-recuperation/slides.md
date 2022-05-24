%title: LINUX
%author: xavki


# LINUX : RAID 1 - Test recovery


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
mdadm --manage /dev/md0 --replace /dev/sdc1 --with /dev/sdd1
mdadm --grow /dev/md0 --raid-devices 3 --add /dev/sdc1
```

-------------------------------------------------------------------

# LINUX : RAID 1 - Test recovery

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

# LINUX : RAID 1 - Test recovery

<br>

* ajouter un spare 

```
mdadm --manage /dev/md0 --add /dev/sdd1
mdadm --add-spare /dev/md0 /dev/sde1
mdadm -D /dev/md0 --scan >> /etc/mdadm/mdadm.conf
update-initramfs -u
```

<br>

* test suppression du disque

```
sfdisk -d /dev/sda | sfdisk /dev/sdb
```

<br>

* recovery

```
mdadm --stop /dev/md0
mdadm --assemble /dev/md0
```

-------------------------------------------------------------------

# LINUX : RAID 1 - Test recovery

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

<br>

* forcer un rebuild

```
mdadm --assemble --run --force --update=resync /dev/md0 /dev/sdb1 /dev/sdc1
```
