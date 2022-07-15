%title: LINUX
%author: xavki


# LINUX : Jobs & Nohup


<br>

* jobs = comment faire tourner un process en backgroud ?

* pour ne pas perdre le process :
		* fermeture du terminal
		* perte de connexion réseau
		* ...

---------------------------------------------------------

# LINUX : Jobs & Nohup

<br>

* créer un job

```
<command> &
```

<br>

* lister les jobs

```
jobs
jobs -l
jobs -p
jobs -r
```

---------------------------------------------------------

# LINUX : Jobs & Nohup

<br>

* reprendre un job

```
fg %<num>
```

---------------------------------------------------------

# LINUX : Jobs & Nohup

<br>

* mettre en pause (stopped)

Ctrl+Z

```
jobs -s
bg %1 # running
fg %1
Ctrl+Z
```

---------------------------------------------------------

# LINUX : Jobs & Nohup

<br>

* nohup = pas de signal up possible (attention ça limite pas tout)

* combinaison avec le job

```
nohup sleep 3600 &
```


