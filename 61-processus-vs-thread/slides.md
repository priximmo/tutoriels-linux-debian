%title: LINUX
%author: xavki


# LINUX : Process vs Fork vs Thread


<br>

Linux : OS multitâches et préemptif
		* démarrer
		* stopper
		* reprendre

Rôle du scheduler

<br>

1 core : pas de parallélisation

On parle de "simultanéité apparente"

Du coup, le scheduler intègre une priorisation

<br>

démarrer/stopper/reprendre = context switching (commutation de contexte)
		* l'enjeu est de fixer l'état du process suspendu
		* pour pouvoir le reprendre où il en était


----------------------------------------------------------------------------------

# LINUX : Process vs Fork vs Thread


<br>

Processus/Fork :


```
     ┌──────────────────┐
     │                  │
     │    Pile (Stack)  │ Variables locales & retours de Fonctions
     │                  │
     ├──────────────────┤
     │                  │
     │   Bibliothèques  │	Lib partagées
     │                  │
     ├──────────────────┤
     │                  │
     │   Tas (Heap)     │	Variables non ordonnées/vrac
     │                  │
     ├──────────────────┤
     │                  │
     │  Données (Datas) │	Variables globales
     │                  │
     ├──────────────────┤
     │                  │
     │   Code (Text)    │	Code à exécuter
     │                  │
     └──────────────────┘
```

----------------------------------------------------------------------------------

# LINUX : Process vs Fork vs Thread


<br>

		* fonction fork() et wait()
<br>

		* processus fils
<br>

		* PID différents entre père et fils
<br>

		* copie similaire au process parent (même variables et code par ex)
<br>

		* valeurs différenciées via l'utilisation du PID
<br>

		* par exemple au fork() COPIE des files descriptors
<br>

		* mais différenciation après
<br>

		* communication entre processus (plus coûteux)


----------------------------------------------------------------------------------

# LINUX : Process vs Fork vs Thread


<br>

Thread :

```
     ┌──────────────────┐
     │    Pile1         │
     │    Pile2         │ Variables locales & retours de Fonctions
     │    Pile3         │
     ├──────────────────┤
     │                  │
     │   Bibliothèques  │ Lib partagées
     │                  │
     ├──────────────────┤
     │                  │
     │   Tas (Heap)     │ Variables temporaires/vrac
     │                  │
     ├──────────────────┤
     │                  │
     │  Données (Datas) │ Variables globales
     │                  │
     ├──────────────────┤
     │                  │
     │   Code (Text)    │ Code à exécuter
     │                  │
     └──────────────────┘
```

----------------------------------------------------------------------------------

# LINUX : Process vs Fork vs Thread


<br>

		* en apparence similaire à un processus
<br>

		* même mémoire
<br>

		* identification : Thread Group ID (PID)  et Thread ID 
<br>

		* cependant les variables et FD sont partagées en mémoire
<br>

		* économie de commutation de contexte (la mémoire reste la même)
<br>

		* communication simplifiée car mémoire partagée
<br>

		* si perte du père perte des threads
<br>

		* le thread n'est pas tout le contenu du code du père
		* juste une fonction (plus léger qu'un fork)
		* délégation de certaines petites tâches au thread
		* optimisé par le multitâche et donc pseudo-paralélisation (de tâches diff)

<br>

		* certains problèmes : modification en parallèle des variables en mémoire
		* solutions existent (mutex = priorisation)

