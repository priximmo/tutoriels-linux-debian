%title: LINUX
%author: xavki


# LINUX : Disques & Partionnements

<br>

* disques physiques :

		* disque dur mécannique (plateau)

		* ssd (Solid State Drive)

	Disques > ??? > Filesystem

	Partitionnement > Formatage > Montage

* pourquoi faire ?

		* créer une isolation la composante système et d'autres
				* permettre d'accéder à la machine

		* séparer les données, les programmes
				* cf tuto sur la hiérarchie du système de fichier

		* séparer les données utilisateurs des programmes

		* limiter les risques de corruptions (volumes à fort I/O)

		= dédier un espace pour chaque volume (répertoires racines)

		=> découper le(s) disque(s) en sous disques (logique) 

* Quel découpage choisir ?

		/tmp : compte tenu de la facilité d'accès et des risques de le remplir

		/home : isoler les usages des utilisateurs (moins précotionneux)

		/var : les données à forte variation (notamment en volume)

		/ : pour récupérer tous les autres répertoires

		(/boot) : dédié au noyau et à l'amorçage

		swap : particulier pour la mémoire
	
