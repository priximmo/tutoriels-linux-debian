%title: LINUX
%author: xavki


# LINUX : Inodes & caractéristiques d'un fichier

<br>

* vidéo précédente => différents types de fichiers

* commande stat

<br>

* options :

		-f : filesytème du fichier

		-L : suivre les liens symboliques (symlink)

<br>

* stat sortie (output)

```
  File: toto.txt
  Size: 5         	Blocks: 8          IO Block: 4096   regular file
Device: fd01h/64769d	Inode: 8165659     Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/     oki)   Gid: ( 1000/     oki)
Access: 2022-04-15 07:42:40.323132281 +0200
Modify: 2022-04-15 07:42:40.323132281 +0200
Change: 2022-04-15 07:42:40.323132281 +0200
 Birth: -
```

------------------------------------------------------------------------

# LINUX : Inodes & caractéristiques d'un fichier

<br>

INFORMATIONS

		* File : le nom du fichier (où la représentation du symlink)
		* Size : taille en bytes
		* Block : nombre de blocks alloués
		* IO Block : taille de chaque block
		* type de fichier
		* Device : le numéro de device
		* Inode : numéro d'inode
		* Links : nombre de hard links
		* Access : permissions symbol et octal
		* UID / GID
		* Access : dernière date d'accès
		* Modify : date de la dernière modification du contenu
		* Change : date de changement du contenu et des attributs
		* Birth : non utilisé sous linux


------------------------------------------------------------------------

# LINUX : Inodes & caractéristiques d'un fichier

<br>

NOTION DE BLOCK


<br>

		* un filesystème est découpé en morceaux = blocks

		* chaque block device dispose d'une taille de blocks

<br>

```
lsblk
```

<br>

		* plusieurs niveaux de blocks
				* disk block size (disque) ~ 512
				* data block size (filesystème) ~ 4096 (4k)

```
	Block Disk > Block FileSystem > Fichiers... ou blocks applicatifs
```

<br>

		* si un block FS à une taille de 4096 bytes et un fichier 8 bytes
				* => utilisation de 4096 bytes

------------------------------------------------------------------------

# LINUX : Inodes & caractéristiques d'un fichier

<br>

* nombre de blocks par device

```
cat /proc/partitions
cat /sys/block/nvme0n1/queue/physical_block_size 
cat /sys/block/nvme0n1/queue/logical_block_size 
```

------------------------------------------------------------------------

# LINUX : Inodes & caractéristiques d'un fichier

<br>

ou

```
sudo fdisk -l /dev/nvme0n1
Disk /dev/nvme0n1: 476,96 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: LENSE30512GMSP34MEAT3TA                 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
```

------------------------------------------------------------------------

# LINUX : Inodes & caractéristiques d'un fichier

<br>

* choix de la taille des blocks

		* petits fichiers = block size plus petits (mais perte lié aux méta-données)

		* gros fichiers = large block (mais si petits fichiers = perte)

		* trop de blocks = dépasser la limite gérable par le system

* les inodes sont des pointeurs vers les data blocks
		* inodes = noeuds d'index

------------------------------------------------------------------------

# LINUX : Inodes & caractéristiques d'un fichier

<br>

NOTION INODES

		* pointeurs vers les data blocks

		* diposent de metadatas :
				* device du fichier
				* le numéro d'inode (unique dur sur un filesystem)
				* type de fichier et mode
				* GID/UID
				* nombre de hard links

		* taille du fichier

		* nombre de blocks

		* atime : dernier accès

		* mtime : date de modification du contenu

		* ctime : date de changement du contenu et des attributs

------------------------------------------------------------------------

# LINUX : Inodes & caractéristiques d'un fichier

<br>

PROCESS DE LECTURE D'UN FICHIER

<br>

	1 - lire l'inode

<br>

	2 - trouver l'inode dans la table des inodes

<br>

	3 - lire les informations de l'inode

<br>

	4 - récupération de la localisation des blocks
				* block début/fin ou début/taille

<br>

	5 - lecture des datas blocks
