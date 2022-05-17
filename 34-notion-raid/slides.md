%title: LINUX
%author: xavki


# LINUX : Les RAID

<br>

RAID : Redundant Array of Independent Disks

1978 : les origines du RAID 5 (IBM) et mention du RAID 1

1987 : technologie RAID (Berkeley)


------------------------------------------------------------------------------

# LINUX : Les RAID

<br>

Intérêts ?

	* suite à des coûts de stockage très bas

	* problématique de performances

	* redondance des données (si perte de disque ou erreurs)

<br>

Prérequis : 

	* avoir plusieurs disques

	* le nombre dépend du choix de RAID

------------------------------------------------------------------------------

# LINUX : Les RAID

<br>

Type de contrôles :

	* logiciel

			* moins coûteuse

			* administration système

			* compatibilité

			* moins proche du matériel (erreurs...)

			* consommation de ressources systèmes

------------------------------------------------------------------------------

# LINUX : Les RAID

<br>

	* matériel semi-matériel : 
			routines en dehors de l'OS
			pas indépendant

			* éviter la dépendance au système d'exploitation

			* idéal pour des fichiers externes à celui-ci

			* consommaion de ressources (système non dédié)

			* difficultés de changement de carte-mère

------------------------------------------------------------------------------

# LINUX : Les RAID

<br>

	* matériel :
			processeur, mémoire, batterie dédiés

			* détection de problèmes matériels

			* préservation des ressources

			* opérations en arrière plan (check, diag...)

			* pas de compatibilité entre les controleurs

			* le coût

			* haute dispo nécessaire 

------------------------------------------------------------------------------

# LINUX : Les RAID

<br>

RAID 0

	A1	A2
	B2	B1
	C1	C2

	* disques entrelacés 

	* strippé (cf vidéo LVM strippé)

	* 2 disques requis

	* amélioration sensible des performances

	* taille est égale au plus petit des disques (même capacité)

	* risque de perte x2 (perte 1 disque = perte totale)

------------------------------------------------------------------------------

# LINUX : Les RAID

<br>

RAID 1

	A1	A1
	B1	B1
	C1	C1

	* mirroré (duplication)

	* 2 disques requis

	* résistance à la panne (erreurs ou perte totale)

	* pas de perte du service

	* performances variables en lectue (amélioration si multithread)

	* réduction de perf en écriture (légère)

	* capacité = plsu petit des disques

	* risque divisé par 2

	* augmentation du coût

------------------------------------------------------------------------------

# LINUX : Les RAID

<br>

RAID 10

		
	A1	A1	|	A2	A2
	B2	B2	|	B1	B1

	* 4 disques requis

	* cumul de 2 RAID 0 sous un RAID 1

	* 2 mirrorés x 2 disques strippés
	
	* cumul des atouts des RAID 0 & 1 (perf et redondance)

------------------------------------------------------------------------------

# LINUX : Les RAID

<br>

RAID 5

	A1	A2	P
	B1	P		B2
	P		C1	C2

	* 3 disques (n blocs de données & 1 parité par disque)

	* mirroré et strippé mais avec des informations de parités
			* algo de parité

	* performance de lecture

	* écriture réduite

	* sur failure pas de perte de l'Array mais reconstruction

	* perte de données si perte de 2 disques

------------------------------------------------------------------------------

# LINUX : Les RAID

<br>

RAID 6

	* idem RAID 5 mais 2 disques de parité
