%title: LINUX
%author: xavki


# LINUX : Les RAID


RAID : Redundant Array of Independent Disks

1978 : les origines du RAID 5 (IBM) et mention du RAID 1

1987 : technologie RAID (Berkeley)


Intérêts ?

	* suite à des coûts de stockage très bas

	* problématique de performances

	* redondance des données (si perte de disque ou erreurs)


Prérequis : 

	* avoir plusieurs disques

	* le nombre dépend du choix de RAID

Type de contrôles :

	* logiciel

			* moins coûteuse

			* administration système

			* compatibilité

			* moins proche du matériel (erreurs...)

			* consommation de ressources systèmes

	* matériel


<br>

RAID 0

	* strippé (cf vidéo LVM strippé)

	* 2 disques requis

	* amélioration sensible des performances

<br>

RAID 1

	* mirroré (duplication)

	* 2 disques requis

	* résistance à la panne (erreurs ou perte totale)

	* pas de perte du service

	* performances variables en lectue (amélioration si multithread)

	* réduction de perf en écriture (légère)

<br>

RAID 10

	* 4 disques requis

	* cumul de 2 RAID 0 sous un RAID 1

	* 2 mirrorés x 2 disques strippés
	
	* cumul des atouts des RAID 0 & 1 (perf et redondance)

<br>

RAID 5

	* 3 disques (2 datas & 1 parité)

	* mirroré et strippé mais avec des informations de parités
			* algo de parité

	* performance de lecture

	* écriture réduite

	* sur failure pas de perte de l'Array mais reconstruction

	* perte de données si perte de 2 disques

RAID 6

	* idem RAID 5 mais 2 disques de parité
