%title: LINUX
%author: xavki


# LINUX : Device Mapper


<br>

https://en.wikipedia.org/wiki/Device_mapper

DM = Device Mapper

DM = 

	* framework fournit par le kernel linux

	* mapper des blocks devices physique

	* en blocks devices virtuels pour l'utilisateur

	* possibilité de crtyper les disques

	* les fondements de LVM2

Mapper = table de mappage 

	* un device dispoe d'un nom (sda) et par le couple major/minor (256:1)

DMSETUP

* liste des devices

```
dmsetup ls
dmsetup ls --tree #lsblk
```

* afficher la table de mappage

```
dmsetup table
```

* résumé global de device mapper

```
dmsetup info #lvdisplay ou lvs
dmsetup info -c vgubuntu-root
```

* affichage des dépendances (couple major/minor)

```
dmsetup deps
```

* renommer des device

```
dmsetup rename deb1--vg-tmp deb1--vg-temp
```

* suspendre les I/O

```
dmsetup suspend --nolockfs deb1--vg-tmp
dmsetup suspend --noflush deb1--vg-tmp
dmsetup info
```

* réactiver

```
dmsetup resume deb1--vg-tmp
```
