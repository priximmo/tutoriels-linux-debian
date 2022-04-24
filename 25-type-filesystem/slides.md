%title: LINUX
%author: xavki


# LINUX : EXT4 vs XFS vs BTRFS vs ZFS

<br>

	Disque > block> système d'exploitation > filesystème

<br>

	Journalisation : enregistrement des modifications (datas/metadatas)
					* utile en cas de crash	

<br>

	Delayed allocation : les données sont stockées dans un buffer/tampon
					* avant d'être écrites sur les data blocks
					* permet de temporiser pour réduire la fragmentation...

--------------------------------------------------------------

# LINUX : EXT4 vs XFS vs BTRFS vs ZFS

<br>

EXT4

<br>

	* Exemple :

		Disque = Boot Block + Block Group + .... + Block Group

<br>

		Block Group = x blocks

<br>

		Block Group = 
				* Super Block (1) : infos du filesystème (nb blocks...)
				* Group Descriptor(x) : localisation des bitmap et table inodes
				* Data Block Bitmap (1) : carte de blocks dédiés aux blocks
				* Inode Bitmap (1) : carte des blocks dédiés aux inodes
				* Inode Table (n) : metadatas et données des fichiers
				* Data Block (n) : données

<br>

		Ex : Directory > Inode > X data blocks

--------------------------------------------------------------

# LINUX : EXT4 vs XFS vs BTRFS vs ZFS


<br>

	* https://ext4.wiki.kernel.org/index.php/Main_Page

	* 4ème version des filesystem étendus

	* à partir du kernel 2.6.19

	* taille maximum d'un fichier 16TB

	* taille maxi du filesystem 1EB

	* nombre maximum de sous répertoire 64000

	* compatibilité de ext3 avec ext4

--------------------------------------------------------------

# LINUX : EXT4 vs XFS vs BTRFS vs ZFS

<br>

	* défragmentation à chaud (sans démonter le disque) e4defrag

	* multi-block allocation = amélioration lecture/écriture

	* retarde allocation des blocks (avant de flusher sur disk)  
		* basée sur les extents
		* allocation plus rapide pour les fichiers
		* autres FS : allocation immédiate (même si la donnée va en cache)

	* journal checksum : éviter la corruption de fichier
		(si activation réduction de la performance)

	* vitesse de fsck améliorée

	* timestamp en nanoseconde

	* désactivation de la journalisation possible

--------------------------------------------------------------

# LINUX : EXT4 vs XFS vs BTRFS vs ZFS

<br>

XFS

<br>

	* adapté aux gros volumes de données et gros fichiers/répertoires

	* default sur les os RedHat

	* haute performance de lecture et d'écriture

	* allocation groupe ~ block groupes : mais plus gros que BG

	* allocation groupe fonctionnement similaire à un filesystème
			* permet la paraléllisation et la scalabilité

	* journalisation des metadatas : amélioration de la consistence

--------------------------------------------------------------

# LINUX : EXT4 vs XFS vs BTRFS vs ZFS

<br>

	* défragmentation à chaud

	* redimensionnement à chaud

	* direct I/O : bypass le cache du kernel dédié aux fichiers 
			* moins de CPU

	* delayed allocation amélioration des performances : 
		* quand la donnée est arrivée sur disque
		* réduction de la fragmentation

	* quota et journalisation (en cas de crash)

	* extension des attibuts par fichier

	* taille maximum du filesystem 8EB

--------------------------------------------------------------

# LINUX : EXT4 vs XFS vs BTRFS vs ZFS

<br>

BTRFS

	* https://btrfs.readthedocs.io/en/latest/

	* maximum filesystem 16EB

	* maximum fichier 16EB

	* adapté pour les nombreux petits fichiers

	* allocation dynamique des inodes

	* permet de réaliser du RAID strippé, mirroré ou les deux

	* compression, lecture et écriture des snapshots (incrémental)

--------------------------------------------------------------

# LINUX : EXT4 vs XFS vs BTRFS vs ZFS

<br>

	* COW : copy on write 

	* future de ext4

	* disques > storage pool > volumes (partitions) > filesystems

	* réalisation de snapshots

	* compression (zlib)

	* compatible SSD (trim...)

	* défragmentation à chaud

--------------------------------------------------------------

# LINUX : EXT4 vs XFS vs BTRFS vs ZFS

<br>

ZFS

	* maximum filesystem 1ZB

	* volume manager + filesystem

	* maximum fichier 16 EM

	* multiple disques = pool de stockage > filesystems

	* ajout facile de disques poru être pris en compte par le pool

	* cow : copy on write (on n'écrase jamais la donnée)

	* snapshots du filesystem

	* RAID-Z : amélioration de l'intégrité de la data


