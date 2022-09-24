%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Les Templates


<br>


Objectif : Et si j'ai des services que je veux instancier ?
						Avec une seule unité ?

<br>

* un service simple sans template

```
<service_name>.service
```

<br>

* un service simple avec template 

```
<service_name>@<argument>.service
```

Note : argument = instance = variable réutilisable dans la configuration

Attention : le nom du fichier doit aussi comporter le @

<br>

* deux formats de variables possibles:

%i : échappe les caractères spéciaux

%I : sans échappemement

<br>

* et d'autres variables

```
    %n: nom de l'unité
    %N: idem %n mais avec échappement
    %p: préfix de l'unité (ex: hello) avant le @
    %P: idem %p mais avec échappement
    %f: nom de l'instance de l'unité avec un / devant
    %c: indique le contrôle group (cgroup) d'appartenance
    %u: nom du user qui lance l'unité
    %U: UID du user qui lance l'unité
    %H: le nom du serveur où a été lancé l'unité (hostname)
```


Alias=
Also=
WantedBy=
RequiredBy=
DefaultInstance=

AssertPath
