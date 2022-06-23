%title: LINUX
%author: xavki


# LINUX : Device Mapper


<br>

https://en.wikipedia.org/wiki/Device_mapper

DM = Device Mapper

<br>

DM = 

	* framework fourni par le kernel linux

	* mapper des blocks devices physique

	* en blocks devices virtuels pour l'utilisateur

	* possibilité de crtyper les disques

	* les fondements de LVM2

Mapper = table de mappage 

	* un device dispoe d'un nom (sda) et par le couple major/minor (256:1)

------------------------------------------------------------------------------------------

# LINUX : Device Mapper


<br>

DMSETUP

<br>

* liste des devices

```
dmsetup ls
dmsetup ls --tree #lsblk
```

<br>

* afficher la table de mappage

```
dmsetup table
```

<br>

* résumé global de device mapper

```
dmsetup info #lvdisplay ou lvs
dmsetup info -c vgubuntu-root
```

------------------------------------------------------------------------------------------

# LINUX : Device Mapper


<br>

* affichage des dépendances (couple major/minor)

```
dmsetup deps
```

<br>

* renommer des device

```
dmsetup rename deb1--vg-tmp deb1--vg-temp
```

------------------------------------------------------------------------------------------

# LINUX : Device Mapper


<br>

* suspendre les I/O

```
dmsetup suspend --nolockfs deb1--vg-tmp
dmsetup suspend --noflush deb1--vg-tmp
dmsetup info
```

<br>

* réactiver

```
dmsetup resume deb1--vg-tmp
```

<br>

* création

```
echo "0 1024 linear /dev/sdb1 0" | dmsetup create toto
```

https://docs.kernel.org/admin-guide/device-mapper/index.html
