%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Hostname & HostnameCTL


<br>

* hostname : nom du serveur localement

```
echo $HOSTNAME
hostname
sysctl kernel.hostname
```

Note : si modif de sysctl non préservé au reboot

--------------------------------------------------------------------------------

# LINUX : SYSTEMD - Hostname & HostnameCTL

<br>


* un daemon hostnamed géré via un service (unité)

```
man systemd-hostnamed
sudo systemctl status systemd-hostnamed.service
```

--------------------------------------------------------------------------------

# LINUX : SYSTEMD - Hostname & HostnameCTL

<br>

* redirige sur l'interface locale (vidéo network plus tard)

```
ping $HOSTNAME
```

--------------------------------------------------------------------------------

# LINUX : SYSTEMD - Hostname & HostnameCTL

<br>

* gérez dans un fichier de configuration

```
cat /etc/hostname
```

Note : si changement /etc/hosts aussi

--------------------------------------------------------------------------------

# LINUX : SYSTEMD - Hostname & HostnameCTL

<br>

* avec hostnamectl le nom standard

```
hostnamectl status
hostnamectl --static
hostnamectl set-hostname doki1
hostnamectl --static
cat /etc/hostname
```

--------------------------------------------------------------------------------

# LINUX : SYSTEMD - Hostname & HostnameCTL

<br>

* définir un pretty hostname

```
hostnamectl --pretty set-hostname "Xavki Computer"
hostnamectl --pretty
cat /etc/machine-info
```

--------------------------------------------------------------------------------

# LINUX : SYSTEMD - Hostname & HostnameCTL

<br>

* définir une localisation (Rack, DC, U, immeuble, bureau...)

```
hostnamectl set-location "XavCave"
```
