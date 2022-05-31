%title: LINUX
%author: xavki


# LINUX : I/O


<br>

* I/O = Input/Output

* Disk IO

* Input = écriture

* Output = lecture

-----------------------------------------------------------------------

# LINUX : I/O

<br>

* data transfert

<br>

* unités : 
		* MB/s,KB/s
		* opérations par seconde

<br>

* point important de performance :
		* base de données
		* traitement de tâches généralement

-----------------------------------------------------------------------

# LINUX : I/O

<br>

Représentation :

	USER > Kernel > Mémoire <-> Disks

<br>

	Mémoire <-> Disks
		* Buffer = écriture
		* Cache  = lecture

<br>

Impacts importants :

		* lenteurs applications

		* traitement des tâches

		* saturation des CPU 

		* saturation de la RAM


Indicateur principal :

		* iowait (mesure du temps d'attente CPU)

		* attente de lecture/écriture IO

		* wa (top...) , %iowait (iostat), wait...

		* processus status = D (tâche non interruptible)

	
-----------------------------------------------------------------------

# LINUX : I/O

<br>

* Facteurs :

		* noatime (fstab) : pas de timestamp (atime)
			https://opensource.com/article/20/6/linux-noatime

		* développement applicatif (APM est ton ami)

		* garder tout à jour :) (système, applicatif, firmwares...)

		* type de disk (HDD / SSD)

		* type de connectique pour SSD (SAT/NVMe)

		* nombre de disque dans une grappe RAID

		* RAID Level ( 0 = strip, x2, x4... )

		* type random/sequential

		* IOPS

		* taux de lecture et d'écriture

		* taille des blocs (différents niveaux)

<br>


* stockage = HDD / SSD / NAS (NET)

<br>

Les Mesures : 

* IOPS => lecture/écriture par seconde (en nombre)

* KB/s (MB/s) => un débit (quantité par seconde)

<br>

FIO > benchmark

<br>

Quelques calcules :

	* si j'ai un disk capable d'écrire 155 MB/s avec des blocs 4K

		> 155 * 1024 / 4k = 39680 IOPS

	* inversement mon disque a pour capacité 40k IOPS et blocs 4k

		> 40000 * 4k / 1024 = 156,25 MB/s
