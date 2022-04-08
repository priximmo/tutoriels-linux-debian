%title: LINUX
%author: xavki


# LINUX : MOTD & ISSUE

<br>

* messages à l'utilisateur :

		* avant le login : issue

		* après login : motd
				(Message Of The Day)

		* à la sortie : .bash_logout

	=> Man !!!


---------------------------------------------------------------
	
# LINUX : MOTD & ISSUE


<br>

ISSUE

* prelogin message

* attention aux informations affichées 

		* sécurité

		* éviter les versions, noms de users, société...

* fichier à éditer :

```
		/etc/issue
```

---------------------------------------------------------------
	
# LINUX : MOTD & ISSUE


<br>

MOTD

<br>

* postlogin message

* fournir des infos à l'utilisateur (ex: environnement)

<br>

* fichier à éditer

```
/etc/motd
```

---------------------------------------------------------------
	
# LINUX : MOTD & ISSUE

<br>

* script custom

```
/etc/profile.d/motd.sh
```

```
#!/usr/bin/bash
echo "Machine : "$(hostname)
echo "IP : "$(hostname -I)
```

<br>

* supprimer pour un utilisateur

```
touch ~/.hushlogin
```
 
---------------------------------------------------------------
	
# LINUX : MOTD & ISSUE


<br>

* fichier à modifier

```
~/.bashrc_logout
```

* exemple: compte à rebours

```
for i in {1..11};do
echo $((10-i))
sleep 1s
done
```
