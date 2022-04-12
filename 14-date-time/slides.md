%title: LINUX
%author: xavki


# LINUX : DATE & TIME

<br>

* date / heure : élément crucial
		* logs
		* systèmes distribués
		* différents calculs
		* gettimeoftheday
		* tellement important 
				* NTP/PTP

-----------------------------------------------------------------

# LINUX : DATE & TIME

<br>

* notion de format / localisation
		* yyyy/mm/dd...
		* CEST : Central European Summer Time
		* UTC : Universal Time Coordinated
		* RTC : Real Time Clock

-----------------------------------------------------------------

# LINUX : DATE & TIME

<br>
<br>

* format epoch = nb secondes depuis 01/01/1970 00:00:00
		* problématique du 32bits en 2038 ;)
		* vive le 64bits

<br>

* temps de la machine VS temps du système
		* machine : horloge RTC / bios / pile...
		* système : prise en compte des fuseaux horaires...

--------------------------------------------------------------------------------

# LINUX : DATE & TIME

<br>

DATE/HEURE

* commande pour le système

```
date
timedatectl
```

<br>

* spécification de format

```
date +%Y%m%d
date +%Y%m%d-%H:%M:%S
date +%T.%N
```

--------------------------------------------------------------------------------

# LINUX : DATE & TIME

<br>

MACHINE

* commande : hwclock

* réglage commande ou bios

* afficher l'heure

```
sudo hwclock --show
```

--------------------------------------------------------------------------------

# LINUX : DATE & TIME

<br>

<br>

* pour changer

```
sudo hwclock --set --date "13 Jan 2022 20:08" --utc
```

<br>

* synchroniser matériel et système

```
sudo hwclock --systohc
```

et inversement

```
sudo hwclock --hctosys
```

--------------------------------------------------------------------------------

# LINUX : DATE & TIME

<br>

TIMEZONE

* vérifier la timezone du système

```
cat /etc/timezone
timedatectl
date +%Z  #%z
ls -la /etc/localtime
```

<br>

* changer de timezone (2 méthodes)

```
timedatectl list-timezones
timedatectl set-timezone 

sudo rm -rf /etc/localtime
sudo ln -s /usr/share/zoneinfo/America/New_York /etc/localtime
```

--------------------------------------------------------------------------------

# LINUX : DATE & TIME

<br>

DATE & HEURE

* changer ou définir la date et l'heure

```
timedatectl set-time "2022-01-01 00:00:01"
timedateclt set-date "2022-02-01"
timedatectl set-time "00:30:01"
```

<br>

* ou avec date 

```
date -s HH:MM:SS
date -s MM/JJ/AAAA
```

--------------------------------------------------------------------------------

# LINUX : DATE & TIME

<br>

NTP SERVICE

```
timedatectl status
timedatectl timesync-status
timedatectl show-timesync
```

