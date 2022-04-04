%title: LINUX
%author: xavki


# LINUX : L'édition avec Vi/Vim

<br>


* ouverture d'un fichier

```
vi toto
```

* mode ajout

```
a
```

* mode insertion

```
i
```

* mode visuel

```
ctrl + v
```

* mode normal

```
Esc
```

* enregistrer

```
:w
```

* enregistrer et quitter

```
:wq
:wq!
```

* première et dernière ligne (en mode normal)

```
gg
G
```

* la recherche de caractères

```
/
```

* la recherche d'une ligne

```
:<num_ligne>
```

* undo/redo

```
u
:undo
:redo
```

* copier/coller une ligne

```
yy
p
```

* copier coller plusieurs ligne

```
3yy
p
```

* copier/coller d'un numéro de ligne à un autre

```
:set number
11,35y
p
```

* supprimer des lignes

```
dd
10dd
```

* remplacer des caracères

```
:s///g
:%s///g
```


