%title: LINUX
%author: xavki


# LINUX : USERS & GROUPS

<br>

* point important pour sysadmin/devops/sre
		* indication sur la bonne gestion du parc

<br>

* souvent automatisée par des outils (ansible, puppet...)

--------------------------------------------------------------------

# LINUX : USERS & GROUPS

<br>

* UID/GID

<br>

	* identifiants uniques

<br>

	* UID : 
			* 0 pour root
			* 0 - 100 : mode statique pour le système
			* < 1000 : dynamique pour le système
			* > 1000 : autres
			* nobody : valeur max définie

--------------------------------------------------------------------

# LINUX : USERS & GROUPS

<br>

	* GID :
			* pour les groupes
			* 0 pour le groupe root
			* 100 le groupe par défault (users)
			* groupe utilisateur à partir de 1000

--------------------------------------------------------------------

# LINUX : USERS & GROUPS


<br>

GROUPES

<br>

* lister les groupes :

	* getent group

	* /etc/group

--------------------------------------------------------------------

# LINUX : USERS & GROUPS

<br>

* ajouter un groupe :

```
groupadd
```

		* -g : forcer le GID

		* -r : groupe système

<br>

Note :

		* fichier de configuration de groupadd /etc/login.defs

		* changer des fichiers ou répertoires chgrp ou chown

		* si changement de GID pour un groupe : newgrp / groupmod

--------------------------------------------------------------------

# LINUX : USERS & GROUPS

<br>

* supprimer un groupe :

```
groupdel
```

--------------------------------------------------------------------

# LINUX : USERS & GROUPS

<br>

USERS

<br>

* différentes actions possibles :
		
		* useradd : ajout

		* userdel : suppression

		* usermod : modification

<br>

* similaires à : adduser, deluser

--------------------------------------------------------------------

# LINUX : USERS & GROUPS

<br>

* useradd :

		* /etc/default/useradd ou /etc/adduser.conf > configuration

		* -s : spécifier le shell

		* -c : commentaire

		* -d : localisation de la home

		* -g : le groupe de l'utilisateur

		* -G : les groupes additionnels

		* -k : localisation du squelette

--------------------------------------------------------------------

# LINUX : USERS & GROUPS

<br>

```
sudo useradd usertest
sudo useradd -c "Mon nom est personne"
-d /home/mydir -g usertest2 -G docker -m 
-s /usr/bin/sh
```

Note : account désactivé par défaut > définir le password

```
sudo passwd usertest
su - usertest
```

--------------------------------------------------------------------

# LINUX : USERS & GROUPS

<br>

* comment lister les utilisateurs :

		* /etc/passwd

		* getent passwd

		* compgen -u

--------------------------------------------------------------------

# LINUX : USERS & GROUPS

<br>


Note : 

		* si ajout/update de users en masse (bulk) : newusers					

		* autre option via adduser

--------------------------------------------------------------------

# LINUX : USERS & GROUPS

<br>

* comment supprimer un utilisateur ?

	* userdel :

		* -r : suppression de la home


	* deluser :
			
			* --remove-home

			* --backup-to

			* --remove-all-files : attention

--------------------------------------------------------------------

# LINUX : USERS & GROUPS

<br>

* générer un password

```
openssl rand -base64 12
```

--------------------------------------------------------------------

# LINUX : USERS & GROUPS

<br>

* passwd la commande :

			* changer le mot de passe d'un user (ou du sien)

			* -e : force l'expiration (réinitialisation)

			* -l : locker un user

			* -n : minimum de jour entre les changements

			* -u : unlock

			* -x : maximum de validité

			* -w : nombre de jour avant la demande de changement

			* -S : statut (couplé à -a)
