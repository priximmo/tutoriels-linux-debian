%title: LINUX
%author: xavki


# LINUX : Elevation de privilèges & su / sudo

<br>

* sur notre VM on a créé deux utilisateurs :

		* xavki > user standard

		* root > administrateur (super)


--------------------------------------------------------------------------------------

# LINUX : Elevation de privilèges & su / sudo


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

--------------------------------------------------------------------------------------

# LINUX : Elevation de privilèges & su / sudo


<br>

* su c'est bien mais : 

		* tout ou rien : root sinon rien (ou droits peu facile et fins)

		* tout temps changer d'utilisateur

		* sécurité = éviter de disposer du user root

--------------------------------------------------------------------------------------

# LINUX : Elevation de privilèges & su / sudo


<br>

COMMANDE : SUDO (Super User DO)


* parfois nécessaire de l'installer (en tant que root)

```
apt update
apt install sudo
usermod -aG sudo xavki
```

* permet :

		* lancer une commande en tan qu'un user (défaut root)

		* permet une gestion fine des droits (par commande, users, groupes...)

exemple :

```
sudo ls /root
```

--------------------------------------------------------------------------------------

# LINUX : Elevation de privilèges & su / sudo


<br>

* configuration

```
sudo cat /etc/sudoers
sudo visudo
sudo EDITOR=vim visudo
sudo -l
sudo -k
sudo -i
```

```
Defaults editor=/usr/bin/vim
```

<qui> <sys_source> = (<où> <qui_cible>) <quoi> 
<qui> <sys_source> = (<où> <qui_cible>) <quoi>, <quoi>, <quoi>

xavki ALL = (ALL) ALL
xavki ALL = (ALL) ALL


Note : toujours garder une session de root ouverte à coté
