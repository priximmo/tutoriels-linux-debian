%title: LINUX
%author: xavki


# LINUX : RAID 1


<br>

Raid logiciel > commande mdadm

<br>

```
sudo apt install mdadm
```

<br>

```
sudo systemctl status mdmonitor
sudo systemctl start mdmonitor
```

--------------------------------------------------------------------------

# LINUX : RAID 1

<br>

* pour un RAID 1

```
sudo mdadm --create --verbose /dev/md0 --level 1 --raid-devices 2 /dev/sdb1 /dev/sdc1
```

<br>

```
cat /proc/mdstat
mdadm --detail /dev/md0
```

--------------------------------------------------------------------------

# LINUX : RAID 1

<br>

* vitesse de synchronisation

```
sysctl -a | grep raid
```

Note : KibiBytes > 1024 Bytes

<br>

* changer la valeur

```
echo 50000 > /proc/sys/dev/raid/speed_limit_min
```

ou

```
sysctl -w dev.raid.speed_limit_min=50000
```

--------------------------------------------------------------------------

# LINUX : RAID 1

<br>

* de manière permanente

```
# /etc/sysctl.conf
dev.raid.speed_limit_min = 50000
```

--------------------------------------------------------------------------

# LINUX : RAID 1

<br>

* pour sauvegarder la configuration de la grappe RAID

```
mdadm --detail --scan --verbose >> /etc/mdadm/mdadm.conf
update-initramfs -u
```

Note : important pour garder le numéro du device


--------------------------------------------------------------------------

# LINUX : RAID 1

<br>

* utilisation

```
mkfs.ext4 /dev/md0
#/etc/fstab
```

