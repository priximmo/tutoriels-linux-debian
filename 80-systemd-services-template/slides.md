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



    %n: Anywhere where this appears in a template file, the full resulting unit name will be inserted.
    %N: This is the same as the above, but any escaping, such as those present in file path patterns, will be reversed.
    %p: This references the unit name prefix. This is the portion of the unit name that comes before the @ symbol.
    %P: This is the same as above, but with any escaping reversed.
    %i: This references the instance name, which is the identifier following the @ in the instance unit. This is one of the most commonly used specifiers because it will be guaranteed to be dynamic. The use of this identifier encourages the use of configuration significant identifiers. For example, the port that the service will be run at can be used as the instance identifier and the template can use this specifier to set up the port specification.
    %I: This specifier is the same as the above, but with any escaping reversed.
    %f: This will be replaced with the unescaped instance name or the prefix name, prepended with a /.
    %c: This will indicate the control group of the unit, with the standard parent hierarchy of /sys/fs/cgroup/ssytemd/ removed.
    %u: The name of the user configured to run the unit.
    %U: The same as above, but as a numeric UID instead of name.
    %H: The host name of the system that is running the unit.
    %%: This is used to insert a literal percentage sign.



Alias=
Also=
WantedBy=
RequiredBy=
DefaultInstance=

AssertPath
