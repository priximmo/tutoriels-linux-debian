%title: LINUX
%author: xavki


# LINUX : SYSTEMD - Edit & Override

<br>

* lister les propriétés d'une unité

```
sudo systemctl status hello
systemctl show hello.service --all
```

<br>

* Visualiser la valeur d'une propriété

```
systemctl show hello.service --property ExecStart,Description
```

------------------------------------------------------------------------------

# LINUX : SYSTEMD - Edit & Override

<br>

* Surcharger une propriété

```
systemctl edit hello.service
systemctl edit hello.service --full
```

Note : attention se base sur le fichier override.conf

------------------------------------------------------------------------------

# LINUX : SYSTEMD - Edit & Override

<br>

* surcharger des propriétés

```
/etc/systemd/system/hello.service.d/override.conf
```

* Ajout d'une propriété (exemple: After)

* Override properties (exemple : ExecStart)

/etc/systemd/system/hello.service.d/override.conf
