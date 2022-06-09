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

* -c : seulement les stats CPU

```
iostat -c
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           9,09    0,10    3,47    1,72    0,00   85,62
```

Note : idem top commande


    %user, is CPU utilization for the user,
    %nice, is the CPU utilization for apps with nice priority,
    %system, is the CPU being utilized by the system,
    %iowait, is the time percentage during which CPU was idle but there was an outstanding i/o request,
    %steal, percentage of time CPU was waiting as the hypervisor was working on another CPU,
    %idle, is the percentage of time system was idle with no outstanding request.

* -d : uniquement les statistiques des devices

* -x : statistiques détaillées (xd)

* -p : en spécifiant le device 

https://www.sqlpac.com/fr/documents/unix-iostat-performances-disques.html

Statistiques disques

    rps : lectures par seconde
    wps : écritures par seconde
    util : pourcentage d’utilisation des disques

Statistiques tty 	

    tin : nombre de caractères lus à partir des terminaux
    tout : nombre de caractères écrits vers les terminaux

Statistiques CPU 	

    user : pourcentage du temps d’utilisation de la CPU par des process
    utilisateurs (applications)
    sys : pourcentage du temps d’utilisation de la CPU par le système (mode
    système)
    idle : pourcentage du temps où la ou les CPU sont inactives (état idle) et le
    système n’a pas de requêtes E/S disques
    iowait : pourcentage du temps où la ou les CPU sont inactives (état idle) et
    le système a au moins une requête E/S disques. Cette valeur est grandement
    augmentée si plusieurs CPU sont inactives en même temps, ce qui est un
    phénomène inhabituel

Statistiques disques 	

    tm_act : pourcentage du temps pendant lequel le disque est occupé
    kbps : nombre de KB transférés à partir du disque / vers le disque
    tps : nombre de transferts par seconde sur le disque
    msps : moyenne du temps de recherche (si les disques supportent ce
    compteur)
    kb_read : nombre de KB lus sur le disque
    kb_wrtn : nombre de KB écrits sur le disque
