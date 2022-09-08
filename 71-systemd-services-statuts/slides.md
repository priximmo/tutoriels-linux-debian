%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Statuts des Services


<br>

Lister les services 

```
systemctl -t service
systemctl list-units -t service
```

	* load : l'unité a été lancée

	* active : englobe les états

	* sub : état détaillé

----------------------------------------------------------------------------

# LINUX : SYSTEMD - Statuts des Services

<br>

Lister les états

```
systemctl list-unit-files
sudo systemctl list-unit-files hello.service
```

----------------------------------------------------------------------------

# LINUX : SYSTEMD - Statuts des Services

<br>

Liste des States

	* bad : dans le cas de problème avec systemd

	* disabled : non lancé au boot

	* enabled : lancé au boot

	* indirect : disabled mais enabled via une autre unité

	* linked : l'unité disponible via un lien symbolique

	* masked : non disponible à systemd (masqué)

	* static : sans bloc INSTALL

----------------------------------------------------------------------------

# LINUX : SYSTEMD - Statuts des Services

<br>

* masked 

```
sudo mv /etc/systemd/system/hello.service /lib/systemd/system/
sudo systemctl mask hello
```

* linked

```
sudo systemctl link /etc/hello.service
```
