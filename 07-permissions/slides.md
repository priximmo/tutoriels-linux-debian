%title: LINUX
%author: xavki


# LINUX : Permissions sur fichiers et répertoires

<br>

* Comment lister les permissions (mode) sur des fichiers ou répertoires ? 

```
ls -l
-rw-rw-r--  1 oki oki     0 avril  3 16:46 toto
drwxrwxr-x  2 oki oki  4096 mars   4 21:48 x-process

stat <fichier>
  File: toto
  Size: 0         	Blocks: 0          IO Block: 4096   regular empty file
Device: fd01h/64769d	Inode: 8138908     Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/     oki)   Gid: ( 1000/     oki)

getfacl toto
# file: toto
# owner: oki
# group: oki
user::rw-
group::rw-
other::r--
```

----------------------------------------------------------------------------------

# LINUX : Permissions sur fichiers et répertoires

<br>

INTERPRETATION

```
-rw-rw-r--  1 oki oki     0 avril  3 16:46 toto
drwxrwxr-x  2 oki oki  4096 mars   4 21:48 x-process
```

* 1er caractère

    d : directory
    c : character device
    l : symlink
    p : named pipe
    s : socket
    b : block device
    D : door
    - : file

----------------------------------------------------------------------------------

# LINUX : Permissions sur fichiers et répertoires

<br>

INTERPRETATION

```
-rw-rw-r--  1 oki oki     0 avril  3 16:46 toto
drwxrwxr-x  2 oki oki  4096 mars   4 21:48 x-process
```

* par bloc de 3 : owner / group / other

		r : read
		w : write
		x : executable

* notation en octal (cf stat):

		4 = read (r)
		2 = write (w)
		1 = executable (x)

		exemple : 765 ( rwx rw- r-x )

----------------------------------------------------------------------------------

# LINUX : Permissions sur fichiers et répertoires

<br>

COMMANDES DE MODIFICATION

* changement de mode/permissions

```
chmod
```

		* options : -R et -c

<br>

* changer le owner et le groupe

```
chgroup
chown
```
