%title: LINUX
%author: xavki


# LINUX : RAID 0 - 5 - 10


<br>


RAID 0

```
mdadm --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/sdb /dev/sdc
lsblk
mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
update-initramfs -u
mkfs.ext4 /dev/md0
mount /dev/md0 /srv/xavki
#echo '/dev/md0 /mnt/md0 ext4 defaults,nofail,discard 0 0' | sudo tee -a /etc/fstab
df -h

dd if=/dev/zero of=/dev/sda bs=1M count=1024
mdadm --zero-superblock /dev/sdb1
mdadm --remove /dev/md0
cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf.bak

sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda /dev/sdb /dev/sdc


sudo mdadm --create --verbose /dev/md0 --level=6 --raid-devices=4 /dev/sda /dev/sdb /dev/sdc /dev/sdd


sudo mdadm --create --verbose /dev/md0 --level=10 --raid-devices=4 /dev/sda /dev/sdb /dev/sdc /dev/sdd
