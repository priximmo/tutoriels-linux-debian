%title: LINUX
%author: xavki


# LINUX : PROCESS


<br>

Boot d'une machine :


	0. Bouton marche

	1. CPU lance BIOS (Basic Input/Output System) via le ROM

```
efibootmgr -v
```

	2. BIOS - POST (Power On Self Test) : check hardware

	3. BIOS/UEFI : 
			* Secure Boot

	4. Boot device :
			* CD, network (PXE > DHCP > PXE > TFTP)...

	5. BootLoader (GRUB - Grand Unified Boot loader)
			* sélection du noyau

```
ls /boot/grub/
cat /etc/default/grub
ls /etc/grub.d/
#GRUB_BACKGROUND
sudo update-grub
```

```
#ligne vmlinuz
init=/bin/bash
mount -n -o remount,rw /
```

	6. Décompression (vmlinuz) et chargement en RAM du kernel
			* VM : prise en charge de la mémoire virtuelle
			* Z : compresssion

```
ls /boot/
cat /usr/src/linux-headers-$(uname -r)/scripts/extract-vmlinux
```

	7. Lancement du Kernel
			* initramfs (ancien initrd) : système de fichier racine 

	8. Drivers System

	9. Filesystem

	10. Init historique (Premier Process) > systemd
			* nom du serveur
			* timezone
			* check disque (fsck)
			* montage des filesystems
			* suppression des vieux fichiers de /tmp
			* configuration des interface réseau
			* configuration de packet filter
			* démarrage de démonds et éléments réseau

	9. Run level
		
