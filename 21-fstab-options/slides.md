%title: LINUX
%author: xavki


# LINUX : Mount & Le fichier FSTAB


<br>

Trouver les montages :

		* mount 

		* /etc/fstab

		* /etc/mtab : fstab + commande mount

Les options sont utilisables pour mount ou fstab

------------------------------------------------------------------------------------------

# LINUX : Mount & Le fichier FSTAB

<br>

* montage dans fstab

```
<filesystème> <montage> <typeFS> <options> <dump> <pass>
/dev/sdb   		 /srv/xavki   ext4  defaults  0  0
UUID=xxxxxx    /srv/xavki   ext4  defaults  0  0
#NAS
//192.168.7.12/rep_a_partager   /srv/xavki   ext4  defaults  0  0
#NFS
10.10.0.10:/backups /var/backups  nfs      defaults    0       0
```

------------------------------------------------------------------------------------------

# LINUX : Mount & Le fichier FSTAB

<br>

* liste des UUID

```
sudo blkid
sudo lsblk -fe7
```

------------------------------------------------------------------------------------------

# LINUX : Mount & Le fichier FSTAB

<br>

* quelques options courantes :

		* filesystème : disque, UUID, partition, volume logique, label

		* montage : localisation dans le FSH (Filesystem Hierarchie)

		* type de FS : ext2, ext3, ex4, xfs, btrfs, ntfs, swap...

		* dump : jamais utilisé

		* pass : 0 (rien) / 1 (avant 2) / 2 (ordre de priorité) par fsck
	
		* options : du montage 

				* defaults : rw,exec,auto,suid,dev,nouser,async
				* rw/ro : lecture écriture ou readonly
				* exec/noexec : permet l'exécution ou non de binaires
				* auto/noauto : monté au boot/reboot ou mount -a
				* nofail (important) : permet le boot même sans le device
				* discard : spécifique ssd (activation du trim ~ amélioration durée/perf)
				* sync/async : i/o réalisé en synchrone ou asynchrone
				* suid/nosuid : autorise les actions sur les bits suid/sgid
				* noatime/relatime : mettre à jour ou pas la date accès à l'inode
				* user/nouser : les user ou seul root peuvent monter le FS
				* _netdev : device accessible par réseau (besoin du réseau avant de monter)
				* uid= / gid= : spécification des users si hors linux (équivalence, default root)

------------------------------------------------------------------------------------------

# LINUX : Mount & Le fichier FSTAB

<br>

* je suis à la porte... suppression du volume

```
init=/bin/bash
mount -no remout,rw /
#nano ... ajout nofail
#passwd root
exec /sbin/init
```

------------------------------------------------------------------------------------------

# LINUX : Mount & Le fichier FSTAB

<br>

* le mount bind ou comment monter un rep/fichier dans un autre ?

```
/home/linux/bon-fichier   /mnt/read-only/mauvais-fichier     none       bind      0   0
```

ou

```
sudo mount --bind /srv/xavki test/
```

astuce :

```
findmnt
```

* toutes les options sont utilisables via mount (test et validation avant le fstab)
