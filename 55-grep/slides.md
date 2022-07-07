%title: LINUX
%author: xavki


# LINUX : La commande GREP


<br>

* recherche de patterns dans des lignes de fichiers (et un peu plus...)
		* fichiers de configuration
		* fichiers de données "plates"
		* recherches dans les logs (erreurs...)
		* filtrer des informations
		* ...

<br>

* souvent imbriqué "pipé" avec d'autres commandes (cf vidéo précédente)

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* GREP = grep, egrep, fgrep, rgrep, agrep, zgrep...
		* egrep = -E
		* fgrep = -F
		* pgrep = recherche processus
		* zgrep = recherche dans des fichiers compressés
		* agrep = recherche approximative

<br>

* à l'aide !!!

```
man grep
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* ligne de commande

```
grep <options> <recherche> <fichier>
<commande> | grep ...
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* exemple (quotes...)

```
grep 127. /etc/hosts
grep "127." /etc/hosts
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* -i : insensible à la casse

```
grep "LOCAL" /etc/hosts
grep -i "LOCAL" /etc/hosts
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* -c : retourne le nombre d'occurences dans le fichier

```
grep -i -c "LOCAL" /etc/hosts
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* -n : ajoute le numéro de la ligne en plus

```
grep -i -n "LOCAL" /etc/hosts
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* -v : inverse la recherche

```
grep -i -v "LOCAL" /etc/hosts
```

Note : exemple les commentaires

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* -r : recherche récursive

```
grep -ri "LOCAL" 
grep -ri "LOCAL" /etc/
grep -ri "LOCAL" /etc/hosts /etc/resolv.conf
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* -E : pattern regexp

```
grep -E "(127|192).(0|168).[01].[176]" /etc/hosts
egrep "127.0.[01].1" /etc/hosts
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* -m : limiter aux x premiers lignes sélectionnées

```
grep -E -m 2 "(127|192).(0|168).[01].[176]" /etc/hosts
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* -l : juste afficher les fichiers contenant le pattern

```
grep -rl "127" /etc/hosts
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* -A/-B/-C : nombre de lignes après / nombre de lignes avant

```
grep -A2 -B1 "5" test.txt
grep -C1 "5" test.txt
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* -e : multiple pattern

```
grep -e "127" -e "192" /etc/hosts
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* et parfois

```
alias grep
 --color=always
```

-----------------------------------------------------------------------------

# LINUX : La commande GREP

<br>

* -o : seulement le résultat du pattern (regexp)

```
grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}" /etc/hosts
```
