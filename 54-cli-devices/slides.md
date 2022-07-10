%title: LINUX
%author: xavki


# LINUX : CLI Devices


<br>

* récupérer les ID des devices

```
blkid
```

<br>

* lister les blockdevices

```
lsblk
lsblk -f
lsblk -r
lsblk -d -o name,rota
```

------------------------------------------------------------------------

# LINUX : CLI Devices

<br>

* taille, secteurs des disques

```
fdisk -l | grep '^Disk /dev/'
```

------------------------------------------------------------------------

# LINUX : CLI Devices

<br>

* caractéristiques des disques
		* SMART : collecte d'informations sur les disques
		* fonctionne avec un daemon

```
sudo apt-get install smartmontools
sudo smartctl --all  /dev/nvme0n1
sudo smartctl --smart=on  /dev/nvme0n1
sudo smartctl -l error  /dev/nvme0n1
sudo smartctl -l selftest  /dev/nvme0n1
cat /etc/default/smartmontools
```

------------------------------------------------------------------------

# LINUX : CLI Devices

<br>

* informations fournies par udev

```
sudo udevadm info -a -n /dev/nvme0n1
```

<br>

* autres infos

```
sudo lshw -class disk -class storage
sudo lshw -short -C disk
cat /sys/block/nvme0n1/queue/rotational
iostat
dumpe2fs
```

------------------------------------------------------------------------

# LINUX : CLI Devices

<br>

* test

```
ioping -c 10 -s 1M /tmp
```
