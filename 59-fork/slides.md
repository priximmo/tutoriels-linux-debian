%title: LINUX
%author: xavki


# LINUX : Qu'est-ce qu'un fork ?


<br>

* programme = un bout de code inerte
		* du code
		* des variables
		* des données
		* dispose d'un point d'entrée (explicite ou non)

* process = un programme lancé/exécuté
		* stockage en mémoire (adresses)
		* réservation/utilisation de ressources (cpu/mémoire)
		* isolation (ex : redéfinition du contexte)

<br>

* fork :

	1- lancement du programme principal

	2- création du process parent (PID parent)
			* affectation ressources
			* owner
			* isolation...

	3- appel fork() (syscall)
			* copie presque intégrale du process actuel (parent)
			* code retour < 0 : errreur
			* code retour = 0 : pour l'enfant
			* code retour = PID de l'enfant : pour le parent

	4- identification :
			* de l'enfant vue du parent (PID)
			* parent (PPID)
			* parent lance wait() (attente de l'enfant)

	5- l'enfant termine (exit)

	6- le parent lève le wait (signal SIGCHLD) et continue

<br>

* Process suite :

		* cat /proc/1/status
		* 2 > 32767
		* pid 0 : swaper ou scheduler (responsable du paging)
		* pid_max

```
pid_max = min(pid_max_max, max_t(int, pid_max,
           PIDS_PER_CPU_DEFAULT * num_possible_cpus()));
```

https://elixir.bootlin.com/linux/v4.7.10/source/kernel/pid.c#L595

		* ses file descriptors

```
less slides.md
ps aux | grep slides
ls -la /proc/<pid>/fd
```


<br>

exemple :

```
echo $$
echo $PPID
ps aux | grep $PPID
ps faux
```

```
oki         3180  3.7  1.0 4304660 261788 ?      Ssl  21:07   1:12  \_ /usr/bin/gnome-shell
oki         3399  0.0  0.0 162700  7136 ?        Sl   21:07   0:00  |   |   \_ ...
oki         5614  0.9  0.3 841544 73416 ?        Sl   21:24   0:08  |   \_ /usr/bin/python3 /usr/bin/terminator
oki         7343  0.1  0.0  21316 15400 pts/1    Ss   21:38   0:00  |       \_ /bin/bash
oki         7504  0.0  0.0  11928  3852 pts/1    R+   21:39   0:00  |           \_ ps faux
```


* status d'un process

	* new
	* ready
	* running
	* waiting
	* terminated


```
                ┌─────────────┐
    NEW         │ Scheduler   │      TERMINATED
     │          └─────────────┘           ▲
     │                                    │
     └────► READY ────────► RUNNING ──────┘
             ▲                 │
             │                 │    ┌───────┐
             │                 │    │ EXIT  │
             └──── WAITING ◄───┘    └───────┘

            ┌───────────────────┐
            │  IO or Events     │
            └───────────────────┘
```

