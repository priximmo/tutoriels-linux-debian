%title: LINUX
%author: xavki


# LINUX : Crontab & les Crons


<br>

Objectif :

		* programmer des tâches régulières

		* lancer ces tâches avec un utilisateur spécifié

```
man cron
```

----------------------------------------------------------------

# LINUX : Crontab & les Crons


<br>

Deux types de configuration :

		* crontab : à travers la commande crontab ou /var/spool/cron
				* gestion par utilisateur

		* /etc/cron.d/ ou /etc/cron.daily/ (hourly...) : avec des fichiers 
				* possiblité de définir l'utilisateur dans la ligne de cron

----------------------------------------------------------------

# LINUX : Crontab & les Crons

<br>

Par la commande crontab :

* éditer 

```
crontab -e
* * * * * echo "$(date)" >> /tmp/xavki.txt
```

* lister

```
crontab -l
```

----------------------------------------------------------------

# LINUX : Crontab & les Crons

<br>

* pour lister d'un autre utilisateur

```
crontab -u toto -l
```

* supprimer tout le fichier (attention)

```
crontab -r
```

* visualiser ou éditer via spool

```
sudo cat /var/spool/cron/crontabs/oki
```

----------------------------------------------------------------

# LINUX : Crontab & les Crons

<br>

Une ligne de cron : job

		* <fréquence><user?><variable?><commande>

		* fréquence : <minute><heure><jour_mois><mois><jour_semaine>

----------------------------------------------------------------

# LINUX : Crontab & les Crons

<br>

Les caractères spéciaux :

		* "*" : toutes les occurences (ex : toutes les minutes...)

		* "," : spécifier plusieurs valeurs de temps (ex : 1,2,3 (lun/mar/mer)

		* "-" : définir une plage de temps (ex : 10-20 entre 10min et 20min)

		* "/" : définir un interval de temps (ex : */5 toutes les 5 minutes)

		* "L" : définir le dernier élément de (ex : 5L dernier vendredi

		* "#" : pour indiquer le jour du mois avec sa position (ex : 2#3 troisième mardi)

----------------------------------------------------------------

# LINUX : Crontab & les Crons

<br>

* exemples :

```
* * * * * echo "Je suis là" > /tmp/xavki.txt
* * * * * root echo "Je suis là" > /tmp/xavki.txt
*/5 * * * * /opt/monscript.sh
```

<br>

* Envoi de mail possible (sous réserv de configurer un serveur smtp

```
MAILTO="xavki@moi.fr"
```

----------------------------------------------------------------

# LINUX : Crontab & les Crons

<br>

* cas de /etc/cron.d/ ou autre

```
* * * * * root echo "$(date)" >> /tmp/xavki.txt
```

<br>

* autorisation

```
/etc/cron.allow
/etc/cron.deny
```
