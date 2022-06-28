%title: LINUX
%author: xavki


# LINUX : STDIN & STDOUT & STDERR


<br>

* pour chaque programme

* 3 streams (canaux de communications) :

		* entrées

		* sorties

		* erreurs

---------------------------------------------------------------

# LINUX : STDIN & STDOUT & STDERR

<br>

sdtin (0) : standard input

stdout (1) : standard output

stderr (2) : standard error

```
man stdout
```

<br>

* disposent aussi d'un device

```
ls /dev/std*
```

---------------------------------------------------------------

# LINUX : STDIN & STDOUT & STDERR

<br>

file descriptor (FD) : fichiers numérotés et réservés
		* moyens d'échanges/communication
		* chaque process dispose de ses files descriptors
		* à retrouver dans /proc/<pid>/fd/1...
		* potentiellement communicable entre programmes
		* ex : un fichier lu/sortie est représenté sous forme de FD à sa lecture
		* par opposition à la socket descriptor (réseau)
		* 0/1/2 et 3-9 (temporaires)

```
man open
```

---------------------------------------------------------------

# LINUX : STDIN & STDOUT & STDERR

<br>

* stdin & stdout

```
echo "stdin" > /dev/stdin
echo "stdout" > /dev/stdout
echo "nothing" | sudo tee /dev/stderr
read
echo $REPLY
```

---------------------------------------------------------------

# LINUX : STDIN & STDOUT & STDERR

<br>

* stderr

```
ls nothing
ls * toto  2>/dev/null
ls * toto 2>&1 >/dev/null
```

<br>

```
cat <<EOF 
toto
EOF
```

---------------------------------------------------------------

# LINUX : STDIN & STDOUT & STDERR

```
echo $$
sudo cat /proc/16806/fd/0
```

---------------------------------------------------------------

# LINUX : STDIN & STDOUT & STDERR

<br>

```
exec 7<<EOF
Salut Xavki
EOF
read -u 7
echo $REPLY
```
