%title: LINUX
%author: xavki


# LINUX : Pseudos Devices


<br>

* /dev/null

* /dev/zero

* /dev/full

* /dev/random

* /dev/loop

man null

---------------------------------------------------------------------------------------

# LINUX : Pseudos Devices

<br>

* /dev/null : pas d'output, pas de valeur

```
cat /dev/null
ls > /dev/null
ls nothing 2> /dev/null
dd if=/dev/null of=test.txt count=1 bs=1024
ls -a
```

---------------------------------------------------------------------------------------

# LINUX : Pseudos Devices

<br>

* /dev/zero : flux continu de valeur null (ASCII 0 = 0x00) c'est à dire de 0 en binaire

```
man ascii
cat /dev/zero
dd if=/dev/zero of=/opt/zero.txt bs=2048 count=2048
dd if=/dev/zero of=test.txt count=1 bs=1024
ls -a
```

Note : American Standard Code for Information Interchange
Codage de caractères

---------------------------------------------------------------------------------------

# LINUX : Pseudos Devices

<br>

* /dev/full : idem à /dev/zero mais avec un retour d'espace plein

```
echo "toto" > /dev/full
```

---------------------------------------------------------------------------------------

# LINUX : Pseudos Devices

<br>

* /dev/random : génère des chiffres aléatoire (souvent utilisé en cryptographie)

```
dd if=/dev/random of=test.txt count=1 bs=1024
head -c 500 /dev/random | tr -dc 'a-zA-Z0-9~!@#$%^&*_-'
head -c 500 /dev/random | base64
```

---------------------------------------------------------------------------------------

# LINUX : Pseudos Devices

<br>

* /dev/loop : mise à disposition de fichiers sous forme de block device (/dev) 

```
losetup --list
```

