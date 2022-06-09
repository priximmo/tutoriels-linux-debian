%title: LINUX
%author: xavki


# LINUX : CLI Devices


<br>

blkid
lsblk
sudo smartctl --all  /dev/nvme0n1
sudo lshw -class disk -class storage
sudo lshw -short -C disk
fdisk -l | grep '^Disk /dev/'
sudo udevadm info -a -n /dev/nvme0n1
cat /sys/block/nvme0n1/queue/rotational
lsblk -d -o name,rota
sudo smartctl -a /dev/sda | grep 'Rotation Rate'
ioping
iostat
dumpe2fs
fsck
