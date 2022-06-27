%title: LINUX
%author: xavki


# LINUX : STDIN & STDOUT & STDERR


<br>

file descriptor (FD) : fichiers numérotés et réservés
		* moyens d'échanges/communication
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

```
ls /dev/std*
```


file descriptor :

3-9 : usage temporaire


* stdin & stdout

```
echo "stdin" > /dev/stdin
echo "stdout" > /dev/stdout
echo "nothing" | sudo tee /dev/stderr
read
echo $REPLY
```

* stderr

```
ls nothing
ls * toto  2>/dev/null
ls * toto 2>&1 >/dev/null
```

```
cat <<EOF 
toto
EOF
```

```
echo $$
sudo cat /proc/16806/fd/0
```

```
exec 7<<EOF
Salut Xavki
EOF
read -u 7
echo $REPLY
```


https://medium.com/100-days-of-linux/input-output-redirection-in-linux-56571b7c201c
