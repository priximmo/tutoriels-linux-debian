%title: LINUX
%author: xavki


# LINUX : STDIN & STDOUT & STDERR


<br>

file descriptor (FD) : fichiers numérotés et réservés
		* chaque process dispose de ses files descriptors
		* à retrouver dans /proc/<pid>/fd/1...
		* potentiellement communicable entre programmes
		* un fichier lu est représenté sous forme de FD à sa lecture
		* par opposition à la socket descriptor (réseau)

```
man open
```

<br>

sdtin (0) : standard input

stdout (1) : standard output

stderr (2) : standard error

fieldescriptor :

3-9 : usage temporaire

```
ls * toto  2>/dev/null
ls * toto 2>&1 >/dev/null
```

```
cat <<EOF 
toto
EOF
```
