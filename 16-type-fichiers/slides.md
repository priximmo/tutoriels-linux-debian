%title: LINUX
%author: xavki


# LINUX : Type de Fichiers

<br>

Types :

		* Fichier standard  (-)

		* Directory/Répertoire (d)

		* Hard link (-)

		* Symbolic link (l)

		* Character/Block device (c) (b)

		* Local domain socket (s)

		* Named pipe (p)

-------------------------------------------------------------------------

# LINUX : Type de Fichiers


<br>

FICHIER

		* assemblage cohérent de Bytes

		* tout est fichier sur linux

		* texte, vidéos, musiques, images, données...

* déterminer le type de contenu :

```
touch <fichier>
vim <fichier>
...
file <fichier>
stat <fichier>
```

-------------------------------------------------------------------------

# LINUX : Type de Fichiers

<br>

DIRECTORY

		* un fichier permettant de regrouper d'autres fichiers

		* "." / ".."

```
mkdir <répertoire>
rmdir <répertoire>
rm -r <répertoire>
...
stat <répertoire>
```

-------------------------------------------------------------------------

# LINUX : Type de Fichiers

<br>

HARD LINK (link)

		* différents des symbolic links (symlink)

		* lien vers l'inode : adresse du contenu du fichier
				* hard links = même adresse

		* sur des fichiers ou des directory

```
ln <source> <dest>
rm <link>
ls -i 
stat <link>
```

-------------------------------------------------------------------------

# LINUX : Type de Fichiers

<br>

SOFT LINK (symlink)

		* différents des hard links (links)

		* ne pointe pas vers le même inode (adresse)

		* sur des fichiers ou directory

```
ln <source> <dest>
rm <link>
ls -i 
stat <link>
```

-------------------------------------------------------------------------

# LINUX : Type de Fichiers

<br>

CHARACTER/BLOCK DEVICES

		* devices (https://en.wikipedia.org/wiki/Device_file) 

		* device file = interface avec un driver (disks, mémoire...)

		* character = 
				* accessible directement sans tampon (buffer/cache)
				* caractère par caractère
				* ex : terminal, imprimantes...

		* block = 
				* accessible via un tampon (cache)
				* envoi/lecture par block (routine de cache)
				* ex : la mémoire, les disques...
				
		* device file = interface avec un driver (disks, mémoire...)

https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/admin-guide/devices.txt

```
mknod xavki_c_device c 100 1
mknod xavki_b_device b 100 1
```

-------------------------------------------------------------------------

# LINUX : Type de Fichiers

<br>

LOCAL DOMAIN SOCKET

		* socket = connexion entre processus (process)

		* socket interne et socker réseau (connexion réseau)

		* créé via un syscall (fonction système) spécifique "socket()"

```
man 2 socket
```

-------------------------------------------------------------------------

# LINUX : Type de Fichiers

<br>

NAMED PIPE (FIFO)

		* similaire à un pipe (communication entre process)

		* "pipe" = anonymous pipe "|"

		* "named" pipe = un fichier

		* sans stockage de la donnée

```
mknode xavki_named_pipe p
mkfifo xavki_fifo
```
