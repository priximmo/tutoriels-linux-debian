%title: LINUX
%author: xavki


# LINUX : Le statut des Process


<br>

* status d'un process

<br>

	* created

<br>

	* ready (runnable R)

<br>

	* running (running R)

<br>

	* waiting (sleeping) > libère le core/cpu
		* interruptible (S)
		* ininterruptible (D - ex : iowait) 

<br>

	* arrêté (stopped T)

<br>

	* terminated 

<br>

	* orphelins (zombie Z)

---------------------------------------------------

# LINUX : Le statut des Process

<br>

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

