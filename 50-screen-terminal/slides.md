%title: LINUX
%author: xavki


# LINUX : Multiplexer de terminaux - SCREEN


<br>

* multiplexer de terminaux

* permet : 

		* partager un terminal

		* maintenir des commandes longues (sinon nohup &)

		* organiser le travail

--------------------------------------------------------------------------

# LINUX : Multiplexer de terminaux - SCREEN


<br>

* lister les screens

```
screen -ls
```

<br>

* ouvrir un screen

```
screen
screen -ls
```

<br>

* s'attacher à un screen

```
screen -r <id_screen>
exit
```

--------------------------------------------------------------------------

# LINUX : Multiplexer de terminaux - SCREEN

<br>

* donner un nom

```
screen -S <nom_session>
screen -r <nom_session>
```

<br>

* multi-attachement

```
screen -S <nom_session>
sleep 10000
screen -x <nom_session> 
```

--------------------------------------------------------------------------

# LINUX : Multiplexer de terminaux - SCREEN

<br>

* raccourcis

```
    [CTRL]+[a] suivi de [n]: pour «next», aller au terminal suivant.
    [CTRL]+[a] suivi de [p]: pour «previous», aller au terminal précédent.
    [CTRL]+[a] suivi de [0]..[9]: aller au terminal n.
    [CTRL]+[a] suivi de [']: saisir dans le prompt le numéro du terminal.
    [CTRL]+[a] suivi de ["]: lister des différents terminaux, avec la possibilité d'en choisir un.
    [CTRL]+[a] suivi de [w]: lister les terminaux actuels avec leur nom.
    [CTRL]+[a] suivi de [a]: retourner au terminal d'où l'on vient.
    [CTRL]+[a] suivi de [A]: nommer les terminaux et s'y rendre par la suite plus aisément.
```
