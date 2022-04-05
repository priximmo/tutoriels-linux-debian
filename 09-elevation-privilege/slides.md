%title: LINUX
%author: xavki


# LINUX : Elevation de privilèges & su / sudo

<br>

* sur notre VM on a créé deux utilisateurs :

		* xavki > user standard

		* root > administrateur (super)

<br>

COMMANDE : SU (Switch User)

* commande pour changer d'utilsateur ou jouer une commande

```
su
```

		* -c 

		* - : ouvre un shell dans l'environnement du user

		* -s : spécification d'un shell

```
su -c "whoami" root
su -c "ls /root/" - root
su -c "env" root
```

* su c'est bien mais : 

		* tout ou rien : root sinon rien (ou droits peu facile et fins)

		* tout temps changer d'utilisateur

		* sécurité = éviter de disposer du user root

<br>

COMMANDE : SUDO (Super User DO)


* parfois nécessaire de l'installer (en tant que root)

```
apt update
apt install sudo
```

* permet :

		* lancer une commande en tan qu'un user (défaut root)

		* permet une gestion fine des droits (par commande, users, groupes...)

exemple :

```
sudo ls /root
```


