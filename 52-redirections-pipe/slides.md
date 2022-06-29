%title: LINUX
%author: xavki


# LINUX : Redirections & Pipe & tee


<br>

* Rediriger les flux (cf vidéo précédente stdin/stderr/stdout)
		* interaction avec le terminal	

* redirection simple de stdout vers un fichier

```
ls /tmp > output.txt
```

Note : on écrase le contenu du fichier à chaque fois


---------------------------------------------------------------------

# LINUX : Redirections & Pipe & tee

<br>

* redirection

```
ls /tmp >> output.txt
```

<br>

* rediriger stdout (file descriptor 1)

 
```
ls /tmp 1> output.txt
```

---------------------------------------------------------------------

# LINUX : Redirections & Pipe & tee

<br>

* rediriger stderr


```
ls /tmp 2> output.txt
```

---------------------------------------------------------------------

# LINUX : Redirections & Pipe & tee

<br>

* séparation dans 2 fichiers

```
ls . nothing 2> stderr.txt 1> stdout.xt
```

---------------------------------------------------------------------

# LINUX : Redirections & Pipe & tee

<br>

* rediriger stderr vers stdout


```
ls /tmp 2>&1 > output.txt
ls nothing &> test.txt
```

Note : attention l'ordre compte

---------------------------------------------------------------------

# LINUX : Redirections & Pipe & tee

<br>

* injecter un fichier avec stdin

```
ls < stdout.xt
ls . nothing 2> stderr.txt 1> stdout.new < stdout.xt 
```

* idem à :

```
echo "hello world" |& cat
```

---------------------------------------------------------------------

# LINUX : Redirections & Pipe & tee

<br>

* combiner 2 commandes sans erreurs

```
ls nothing && echo toto
```

<br>

* combiner avec/sans erreur

```
ls nothing || echo toto
```

---------------------------------------------------------------------

# LINUX : Redirections & Pipe & tee

<br>

* le pipe (communication inter-processus)

```
cat /etc/hosts | grep 127
```

Note : stdout de 1 écrit dans stdin de 2

---------------------------------------------------------------------

# LINUX : Redirections & Pipe & tee

<br>

* avec tee (option-a) :

```
ls /tmp | tee output.txt
ls /tmp | tee -a output.txt
```

