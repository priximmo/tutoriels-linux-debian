%title: LINUX
%author: xavki


# LINUX : La commande FIND


<br>

Permet : 

	* trouver des fichiers et des répertoires

	* multicritères : noms, date de modification, taille...

	* exécuter des commandes à partir des fichiers/réperoires

-------------------------------------------------------------

# LINUX : La commande FIND

<br>

* commande

```
find <point_recherche> <options> <expression>
```

<br>

* tout lister (fichiers/répertoires et récurrence)

```
find .
```

-------------------------------------------------------------

# LINUX : La commande FIND

<br>

* à partir d'un nom exact

```
find . -name "slides.md"
find . -name "Slides.md"
find . -name "*.txt"
```

<br>

* incensitive

```
find . -iname "slides.md"
```

-------------------------------------------------------------

# LINUX : La commande FIND

<br>

* avec un pattern & regex

```
find . -name "*.txt"
find . -regextype sed -regex ".*/[to]\{4\}\.txt"
```

<br>

* inverse/reverse

```
find . ! -name "slides.md"
```

-------------------------------------------------------------

# LINUX : La commande FIND

<br>

* en précisant le type

```
find . -type d
find . -type d -iname "*iops*"
find . ! -type f -iname "*iops*"
```

```
f plain files
d directories
l symbolic links
b block devices
c character devices
p named pipes
s sockets
```

-------------------------------------------------------------

# LINUX : La commande FIND

<br>

* limiter le niveau de profondeur

```
find . -type d -iname "*iops*" -maxdepth 1
```

<br>

* par la taille

```
find . -size +3k -type f
find . -size -3k -type f
find . -empty
```

Note : G,M,k,c

-------------------------------------------------------------

# LINUX : La commande FIND

<br>

* date/heure de modification

```
find . -cmin -60
find . -cmin +60
find . -mtime +100
```

Note: a = access ; m = modification ; c = creation

-------------------------------------------------------------

# LINUX : La commande FIND

<br>

* coupler avec l'exécution d'une commande

```
find . -mtime +100 -exec cat '{}' \;
find . -mtime +10 -mtime -20 -exec cat '{}' \;
find . -mtime +10 -mtime -20 -exec wc -l {} \;
find . -name "*.png" -exec cp {} /backups/images \;
```

Note : pour supprimer rm ou -delete

-------------------------------------------------------------

# LINUX : La commande FIND

<br>

* en fonction des permissions & user

```
find . -perm 775
find . -perm /u=x
find . -user xavki -group www-data
```

<br>

* opérateur

```
find . -name "*.txt" -or -name "*.pdf"
find . -name "*.txt" -and -name "*.pdf"
find . -name "*.txt" -and ! -name "*test*"
```
