%title: LINUX
%author: xavki


# LINUX : CLI Devices


<br>

* récupérer les ID des devices

```
blkid
```

* lister les blockdevices

```
lsblk
lsblk -f
lsblk -r
lsblk -d -o name,rota
```

* taille, secteurs des disques

```
fdisk -l | grep '^Disk /dev/'
```

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

* informations fournies par udev

```
sudo udevadm info -a -n /dev/nvme0n1
```

* autres infos

```
sudo lshw -class disk -class storage
sudo lshw -short -C disk
cat /sys/block/nvme0n1/queue/rotational
iostat
dumpe2fs

* test

```
ioping -c 10 -s 1M /tmp
```
