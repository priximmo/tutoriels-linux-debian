%title: LINUX
%author: xavki


# LINUX : I/O - iostat


<br>

* variation d'utilisation en fonction de l'OS

* iowait :
		* pourcentage (10%)
		* x% du CPU est destiné à attendre
		* io = lecture/écriture
		* si multi processeurs/cores = moyenne

* depuis le boot de la machine (tips en fin de vidéo)

* ajout d'un nombre fréquence en secondes

------------------------------------------------------------------------------------------------------------

# LINUX : I/O - iostat


<br>

* -c : seulement les stats CPU

```
iostat -c
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           9,09    0,10    3,47    1,72    0,00   85,62
```

Note : idem top commande

    %user : pourcentage d'utilisation CPU utilisé par le userland (programmes...)
    %nice : pourcentage d'utilisation CPU avec une nice priorité (cf tutos process)
    %system : pourcentage CPU utilisé par le CPU (noyau)
    %iowait : pourcentage CPU en attente d'IO
    %steal : pourcentage CPU en attente d'un autre CPU
    %idle : pourcentage du CPU qui se tourne les pouces !!

------------------------------------------------------------------------------------------------------------


# LINUX : I/O - iostat


<br>

* -h : human readable

* -d : uniquement les statistiques des devices

* -x : statistiques détaillées (xd)

* -p : en spécifiant le device 

* -m : données en mega

* -t : afficher l'heure

------------------------------------------------------------------------------------------------------------


# LINUX : I/O - iostat

* interval

```
iostat 3 2
```

Note : par défaut depuis le démarrage de la machine

------------------------------------------------------------------------------------------------------------


# LINUX : I/O - iostat



    rs : lectures réalisées par seconde
    ws : écritures réalisées par seconde
		tps : transferts par seconde (requêtes d'IO par seconde > agrégation logique)
		%util : pourcentage de temps d'utilisation du disque (100% saturé)

    tm_act : pourcentage du temps pendant lequel le disque est occupé
    kbps : nombre de KB transférés à partir du disque / vers le disque
    msps : moyenne du temps de recherche (si les disques supportent ce
    compteur)
    kB_read (/s) : volume/blocks lus en KB sur le device
    kB_wrtn (/s) : volume/blocks écrits en KB sur le device
    kB_dscd (/s) : volume/blocks rejetés par le device
