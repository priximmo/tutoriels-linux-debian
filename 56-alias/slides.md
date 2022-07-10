%title: LINUX
%author: xavki


# LINUX : Les ALIAS


<br>

* alias = utilisation de commandes & options via des raccourcis

* partie intégrante de votre environnement
		* .bash_rc, .bash_profile... .bash_aliases

<br>

* comment lister les alias ?

```
alias
alias ls
```

--------------------------------------------------------------------------------------

# LINUX : Les ALIAS

<br>

* créer ponctuellement un alias

```
alias xavki='ls -i'
alias c='clear'
```

<br>

* supprimer un alias

```
unalias ls
unalias -a
```

--------------------------------------------------------------------------------------

# LINUX : Les ALIAS

<br>

* pour en bénéficier à toutes nouvelles sessions

```
vim ~/.bashrc
source ~/.bashrc
```

<br>

* ne pas utiliser un alias

```
\grep -i "alias" *
```

--------------------------------------------------------------------------------------

# LINUX : Les ALIAS

* les alias c'est bien mais c'est du oneline ??!! = fonction

```
hello(){
echo "hello"
}
```

<br>

```
mkcd(){
mkdir $1 && cd $1
}
```

--------------------------------------------------------------------------------------

# LINUX : Les ALIAS

<br>

* exemple up

```
up() {
if [ "${1/[^0-9]/}" == "$1" ];then p=./;
for i in $(seq 1 $1);
do p=${p}../;
done;
cd $p;
else echo 'usage: up N';
fi
}
```


