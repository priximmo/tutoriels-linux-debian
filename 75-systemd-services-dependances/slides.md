%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Les Dépendances


<br>

```
man systemd.service
```

Objectif : comment permettre de l'auto-guerisson de vos services ?

* gérées par le [Unit]

----------------------------------------------------------------------------------

# LINUX : SYSTEMD - Propriétés de restart & Fails

<br>

Différentes propriétés de la section Unit :

	* After

	* Before

	* Wants

	* Requires

	* Requisite

	* BindsTo

	* PartOf

	* Conflicts

After : lancé après peu importe l'état

Before : 

Wants : devrait être activée avec d'autres unités (non obligatoire)

Requires : doit être activé sinon fail du service

Requisite : n'inclus pas de notion d'ordre (même transaction > After) 

