%title: LINUX
%author: xavki


# LINUX : Montage d'un disque sans partitionnement


<br>

* généralement on utilise à minima du partitionnement

<br>

* peut être pratique (migration de serveur...)

<br>

* inconvénients :

		* pas d'isolation (si le disque est plein perte VM)

		* exemple : base de données, risque sécu sur /tmp, logs...

		* partition : cas d'utilisation pour les dual boot (windows/linux...)

-------------------------------------------------------------------------------

# LINUX : Montage d'un disque sans partitionnement


<br>

SUR VIRTUALBOX

<br>

1. création du disque

2. ajout du disque

<br>

3. lister les disques

```
sudo fdisk -l
```

<br>

4. formater le disque

```
sudo mkfs.ext4 /dev/sdb
```

-------------------------------------------------------------------------------

# LINUX : Montage d'un disque sans partitionnement

<br>

5. le monter temporairement

```
sudo mkdir /srv/xavki
sudo mount -t ext4 /dev/sdb /srv/xavki
df
```


-------------------------------------------------------------------------------

# LINUX : Montage d'un disque sans partitionnement


<br>

DF

	* disk free

	* information sur l'utilisation des filesystems

	* la consommation des inodes

	* les montages actifs sur le système

	* page Wikipédia : https://fr.wikipedia.org/wiki/Df\_(Unix)

-------------------------------------------------------------------------------

# LINUX : Montage d'un disque sans partitionnement


<br>

	* colonnes :

		* Filesystem : devices des filesystems

		* 1k-block : taille en block de 1Kb

		* Used : taille utilisée

		* Available : taille disponible

		* Use% : utilisation en pourcentage

		* Mounted on : où le device est monté sur FHS

-------------------------------------------------------------------------------

# LINUX : Montage d'un disque sans partitionnement


<br>

	* options

		* -a : affiche tous les montages

		* -h : format de taille humain

		* -i : consommation en inodes

		* --total : dernière ligne (tail -1)

		* -T : type de filesystem

		* -t <ext4> : un type de filesystem

		* -x <tmpfs> : exclure un type de filesystem

-------------------------------------------------------------------------------

# LINUX : Montage d'un disque sans partitionnement

<br>

6. si persistence

```
cat /etc/fstab
/dev/sdb  /srv/xavki  ext4  defaults  0 0
```

-------------------------------------------------------------------------------

# LINUX : Montage d'un disque sans partitionnement

<br>

6. si démontage

```
sudo umount /dev/sdb
ou
sudo umount /srv/xavki
```

<br>

7. retirer le disque de la VM

<br>

8. l'ajouter à une autre VM

<br>

9. le monter sur l'autre VM

```
sudo mkdir /tmp/xavki
sudo mount -t ext4 /dev/sdb /tmp/xavki
```

10. informations sur le filesystem

```
sudo dumpe2fs -h /dev/sdb
```

