%title: LINUX
%author: xavki


# LINUX : Signaux & Kill


<br>

* signal = moyen d'interagir avec un process en cours

<br>

* capturé par les programmes > actions en conséquence

<br>

* environ 30 signaux

* connus par un numéro ou un nom

-----------------------------------------------------------------------

# LINUX : Signaux & Kill

<br>

* comportements différents :

		* certains signaux peuvent être capturés

		* certains peuvent être bloqués

		* certains peuvent entrainer un core dump
			(génère un fichier avec la mémoire, registres, détails)

-----------------------------------------------------------------------

# LINUX : Signaux & Kill


<br>

* signal = moyen d'interagir avec un process en cours
* envoyer des signaux :

```
kill -<signal> <pid>
kill -s <signal> <pid>
```

-----------------------------------------------------------------------

# LINUX : Signaux & Kill


<br>

Les principaux SIG :

	HUP (1) : Hangup - capturé / bloqué
			* soit utilisé par certains programme pour se "reloader" 
			* soit utilisé par les shell pour arrêter leurs process fils

-----------------------------------------------------------------------

# LINUX : Signaux & Kill


<br>

	INT (2) : Interrupt - capturé / bloqué
			* équivalent d'un Ctrl+C

-----------------------------------------------------------------------

# LINUX : Signaux & Kill


<br>

	QUIT (3) : Quit - capturé / bloqué / dumpé
			* identique à TERM mais avec core dump

-----------------------------------------------------------------------

# LINUX : Signaux & Kill


<br>

	KILL (9) : Kill - rien
			* coupure brutale et inarrêtable

-----------------------------------------------------------------------

# LINUX : Signaux & Kill


<br>

	TERM (15) : capturé / bloqué
			* arrêt propre du process

-----------------------------------------------------------------------

# LINUX : Signaux & Kill


<br>

	SEGV (11) : Segmentation Fault - capturé / bloqué / dumpé
			* arrêt suite à une erreur mémoire

-----------------------------------------------------------------------

# LINUX : Signaux & Kill


<br>

	STOP (17) : Stop - rien
			* mettre en pause un process

-----------------------------------------------------------------------

# LINUX : Signaux & Kill


<br>

	CONT (19) : Continue - capturé
			* reprendre un process en STOP


