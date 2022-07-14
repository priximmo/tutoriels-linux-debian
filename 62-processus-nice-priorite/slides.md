%title: LINUX
%author: xavki


# LINUX : Process & Priorités (niceness)


<br>

* Linux : OS Multitâches & Preemptive

* Management des tâches par le scheduler

* outil : nice (ionice pour les io)

-------------------------------------------------------------------------

# LINUX : Process & Priorités (niceness)

<br>

NICE :

<br>

		* nice : combien tu es "nice" avec les autres ??
<br>

		* nombre entre -20 et +19

<br>

		* plus la valeur est haute = moins prioritaire (become nice ;) )

<br>

		* plus la valeur est faible ou inf à 0 = plus prioritaire (less nice)

<br>

		* moins utilisé (capacités des CPU et scheduler)

<br>

		* valeur hérité du parent
	
<br>

		* sécurité : un owner du process ne peut que augmenter la valeur ;) (devenir root)

-------------------------------------------------------------------------

# LINUX : Process & Priorités (niceness)

<br>

* lançons un process

```
nice -n 5 /usr/bin/sleep infinity
```

* si process déjà existant

```
renice 10 $(pgrep sleep)
ps -l $(pgrep sleep)
renice 11 $(pgrep sleep)
renice 5 $(pgrep sleep)
sudo renice 5 $(pgrep sleep)
```
