%title: LINUX
%author: xavki


# LINUX : BOOT vers l'init (premier process)


<br>

0. Bouton Marche (électrique ou assimilé cf VM)

<br>

1. CPU lance le BIOS (Basic Input or Output System)
		* via le Bootsrap Processor (vs application processor)
		* se rend au BIOS entrypoint (BIOS code POST)
		* stocké dans la mémoire non volatile ROM (Read Only Memory)
		* stocké sur la carte mère (mémoire flash sur OS moderne - upgrade)
		* read only = non volatile (mémoire non perdue si arrêt électrique)
		* configuration du BIOS stockées dans le CMOS de la carte mère
				* mémoire volatile
				* batterie du CMOS (Complementary metal-oxide-semiconductor)

-------------------------------------------------------------------------------------

# LINUX : BOOT vers l'init (premier process)


<br>

2. BIOS - POST (Power On Self Test) : vérification du hardware

<br>

3. BIOS - Boot device : on lance quoi ?
		* CD, network (PXE > DHCP > PXE > TFTP)...

4. BIOS - Master Boot Record (MBR 512B) = premier secteur d'amorçage
		* table des partitions
 
-------------------------------------------------------------------------------------

# LINUX : BOOT vers l'init (premier process)

<br>

5. BootLoader (GRUB - Grand Unified Boot loader)
			* sélection du noyau

```
ls /boot/grub/
cat /boot/grub/grub.cfg
cat /etc/default/grub
ls /etc/grub.d/
#GRUB_BACKGROUND
sudo update-grub
```

Rq : GRUB_CMDLINE_LINUX_DEFAULT  | man bootparam

-------------------------------------------------------------------------------------

# LINUX : BOOT vers l'init (premier process)

<br>

6. GRUB - Décompression (vmlinuz) et chargement en RAM du kernel + initramfs
			* VM : prise en charge de la mémoire virtuelle
			* Z : compresssion

```
ls /boot/
cat /usr/src/linux-headers-$(uname -r)/scripts/extract-vmlinux
```

-------------------------------------------------------------------------------------

# LINUX : BOOT vers l'init (premier process)

<br>

7. Lancement du Kernel
			* activation de la mémoire
			* initialisation de page/table mémoire
			* détection du CPU
			* initialisation de la prise en compte des hardwares

<br>

8. initialisation des Filesystem

<br>

9. initramfs/initrd > montage du root FS > objectif l'init (systemd)
		* PID 1 = init
		* PID 0 = scheduler


-------------------------------------------------------------------------------------

# LINUX : BOOT vers l'init (premier process)

<br>

10. Exécution de systemd /usr/bin/systemd
		=> lancement de /usr/lib/systemd/system/*

<br>

11. Init historique (Premier Process) > systemd
			* /lib/systemd/systemd
			* nom du serveur
			* timezone
			* check disque (fsck)
			* montage des filesystems
			* suppression des vieux fichiers de /tmp
			* configuration des interface réseau
			* configuration de packet filter
			* démarrage de démonds et éléments réseau

-------------------------------------------------------------------------------------

# LINUX : BOOT vers l'init (premier process)

<br>

12. Run level
		0 - arrêt
		1 -	simple utilisateur (single)
		2 - multi-utilisateurs sans réseau
		3 - multi-utilisateurs avec réseau
		5 - mode graphique
		6 - redémarrage

```
runlevel
```	
		
