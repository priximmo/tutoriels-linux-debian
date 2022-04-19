%title: LINUX
%author: xavki


# LINUX : Copie / Déplacement / Compression de répertoires

<br>

3 commandes importantes pour agir sur les répertoires :

		* cp

		* mv

		* tar

------------------------------------------------------------------------------

# LINUX : Copie / Déplacement / Compression de répertoires

<br>

CP

* copie de fichiers

```
cp <source> <destination>
cp <source1> <source2> <destination>
```

<br>

* copie de répertoires

```
cp -r <source> <destination>
```

<br>

* avec confirmation

```
cp -ri <source> <destination>
```

------------------------------------------------------------------------------

# LINUX : Copie / Déplacement / Compression de répertoires

<br>

* avec backup si on écrase

```
cp -b toto.txt titi.txt
```

<br>

* si pas les permissions d'écriture
sur le fichier de destination

```
cp -f toto.txt titi.txt
```

<br>

* préserver les droits et owner/group

```
cp -p toto.txt titi.txt
```

------------------------------------------------------------------------------

# LINUX : Copie / Déplacement / Compression de répertoires

<br>

MOVE

<br>

* déplacer/renommer fichiers et répertoires

* avec confirmation

```
mv -i rep1 rep2
```

<br>

* ne pas écraser un fichier existant

```
mv -n file1.txt rep2/
```

------------------------------------------------------------------------------

# LINUX : Copie / Déplacement / Compression de répertoires

<br>

* écraser si plus récent

```
mv -u file1.txt rep2/
```

<br>

* créer un backup de la destination si existante

```
mv -b file1.txt file2.txt
```

------------------------------------------------------------------------------

# LINUX : Copie / Déplacement / Compression de répertoires

<br>

COMPRESSION/REGROUPEMENT

<br>

* créer un tarball et souvent gzipper

* avec tar (existe d'autres solution zip...)

<br>

* créer une tarball

```
tar -cf mytarball.tar mydir/
tar -cvf mytarball.tar mydir/
```

* extraction

```
tar xvf mytar.tar
```

<br>

* avec compression/décompression

```
tar -czvf mytarball.tar.gz mydir/
tar -xzvf mytar.tar.gz
```

------------------------------------------------------------------------------

# LINUX : Copie / Déplacement / Compression de répertoires

<br>

* en format bz plus compressé

```
tar -cjvf mytarball.tar.bz2 mydir/
tar -xjvf mytar.tar.bz2
```

<br>

* juste lister le contenu et sa structure

```
tar -tvf mytar.tar.gz
```

------------------------------------------------------------------------------

# LINUX : Copie / Déplacement / Compression de répertoires

<br>

* extraite juste un, des fichiers ou pattern

```
tar -xzvf mytar.tar.gz mydir/toto.txt
tar -xzvf mytar.tar.gz mydir/toto.txt --wildcards "\*.txt"
```

<br>

* ajouter juste un fichier

```
tar -rvf mytar.tar.gz file1.txt
```
