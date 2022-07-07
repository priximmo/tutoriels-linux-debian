%title: LINUX
%author: xavki


# LINUX : La commande GREP


<br>

* recherche de patterns dans des lignes de fichiers (et un peu plus...)

* GREP = grep, egrep, fgrep, rgrep, agrep, zgrep...
		* egrep = -E
		* fgrep = -F
		* pgrep = recherche processus
		* zgrep = recherche dans des fichiers compressés
		* agrep = recherche approximative

<br>


* ligne de commande

```
grep <options> <recherche> <fichier>
<commande> | grep ...
```

* exemple (quotes...)

```
grep 127. /etc/hosts
grep "127." /etc/hosts
```

* -i : insensible à la casse

```
grep "LOCAL" /etc/hosts
grep -i "LOCAL" /etc/hosts
```

* -c : retourne le nombre d'occurences dans le fichier

```
grep -i -c "LOCAL" /etc/hosts
```

* -n : ajoute le numéro de la ligne en plus

```
grep -i -n "LOCAL" /etc/hosts
```

* -v : inverse la recherche

```
grep -i -v "LOCAL" /etc/hosts
```

* -r : recherche récursive

```
grep -ri "LOCAL" 
grep -ri "LOCAL" /etc/
grep -ri "LOCAL" /etc/hosts /etc/resolv.conf
```

* -E : pattern regexp

```
grep -E "(127|192).(0|168).[01].[176]" /etc/hosts
egrep "127.0.[01].1" /etc/hosts
```

* -m : limiter aux x premiers lignes sélectionnées

```
grep -E -m 2 "(127|192).(0|168).[01].[176]" /etc/hosts
```
