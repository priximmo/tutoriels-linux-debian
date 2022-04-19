%title: LINUX
%author: xavki


# LINUX : DD 

<br>

COPIE :

		* devices

		* partitions ou volume logique

		* disque ou zones de disque

		* local ou distant (combinaison avec ssh)

-------------------------------------

# LINUX : DD 

<br>

* copie de disk à disk

```
dd if=/dev/sdb of=/dev/sdc
dd if=/dev/sdb of=/dev/sdc status=progress
```

-------------------------------------

# LINUX : DD 

<br>

* copie en format image (copie sur cd ou usb)

```
dd if=/dev/sdb of=myimage.img
```

-------------------------------------

# LINUX : DD 

<br>

* restauration

```
dd if=myimage.img of=/dev/sdc
```

-------------------------------------

# LINUX : DD 

<br>

* nettoyer

```
dd if=/dev/zero of=/dev/sdc
dd if=/dev/random of=/dev/sdc
```
