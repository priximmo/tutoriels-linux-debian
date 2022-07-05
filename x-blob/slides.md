%title: LINUX
%author: xavki


# LINUX : DU & DF


<br>

## DU = Disk Usage

<br>

Options courantes :

	* -h : format humain (juste répertoires)

```
du -h /tmp
```

	* -s : summarize (somme pour un répertoire)

```
du -sh /tmp
```

---------------------------------------------------------------

# LINUX : DU & DF


<br>

	* -a : fichiers et répertoires

```
du -sh /tmp
```

  * -c : ajoute le total

```
du -csh /tmp
```

	* --time : ajout de la dernière date de modification

```
du -h --time *
```

	* combinaison avec sort et head

```
du | sort -n -r | head
du * | sort -n -r | head
```

---------------------------------------------------------------

# LINUX : DU & DF


<br>

## DF

<br>

DF = Disk Filesystem

    * -a : affiche tous les montages

    * -h : format de taille humain

    * -i : consommation en inodes

    * --total : dernière ligne (tail -1)

    * -T : type de filesystem

    * -t <ext4> : un type de filesystem

    * -x <tmpfs> : exclure un type de filesystem

---------------------------------------------------------------

# LINUX : DU & DF

<br>


  * colonnes :

    * Filesystem : devices des filesystems

    * 1k-block : taille en block de 1Kb

    * Used : taille utilisée

    * Available : taille disponible

    * Use% : utilisation en pourcentage

    * Mounted on : où le device est monté sur FHS

