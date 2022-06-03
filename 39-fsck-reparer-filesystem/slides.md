%title: LINUX
%author: xavki


# LINUX : FSCK - Réparer/Vérifier le Filesystem


<br>

* vérifier un device

```
fsck /dev/<device>
```

<br>

* forcer la vérification (même si pas nécessaire)

```
fsck -f /dev/<device>
```

-----------------------------------------------------------------

# LINUX : FSCK - Réparer/Vérifier le Filesystem

<br>

* vérifier les secteurs défectueux

```
fsck -f -c /dev/<device>
```

Note : si correction vous aurez une demande de confirmation
-N : si juste check

-----------------------------------------------------------------

# LINUX : FSCK - Réparer/Vérifier le Filesystem

<br>

* pour checker tous les devices du fstab (sauf la racine)

```
fsck -AR -y
```

-----------------------------------------------------------------

# LINUX : FSCK - Réparer/Vérifier le Filesystem

<br>

* comment faire un fsck sur la racine sur ancienne machine

```
touch /forcefsck
reboot
ls /
```

<br>

* sur une nouvelle machine via la cmdline (lancement kernel)

```
fsck.mode=force fsck.repair=yes
/etc/default/grub
update-grub
```

-----------------------------------------------------------------

# LINUX : FSCK - Réparer/Vérifier le Filesystem

<br>

* fréquence de vérification

tune2fs -c 50 -i 2w /dev/hda1
