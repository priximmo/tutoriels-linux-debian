%title: LINUX
%author: xavki


# LINUX : Recap RAID & LVM & DEVICE


<br>

* Storage Device : disque SSD, HDD, RAID ARRAY
		* accès à des block devices
		* superblock : metadatas relatives au filesystem
<br>

* Partition : sous ensemble d'un device de stockage
		* primaire/étendue
		* typée

-----------------------------------------------------------------------------------

# LINUX : Recap RAID & LVM & DEVICE

<br>

* RAID Array (Redundant Array of Independent Disks)
		* redondance & aggrégation
		* physique ou logiciel ou mixte
		* différent type : 0,1,5,10 ...

<br>

* LVM : PV + VG + LV

<br>

* Filesystem : comment stocker fichiers, répertoires, journalisation...


-----------------------------------------------------------------------------------

# LINUX : Recap RAID & LVM & DEVICE

<br>



    ┌──►   FILESYSTEM ◄──────┐◄──┐◄───┐
    │                        │   │    │
    │                        │   │ LV │
    │                        │   │    │
    │                        │   │    │
    │                        │   │ VG │
    ├────────┬─►  RAID  ─────┼───┤    │
    │        │               │   │    │
    │        │               │   │ PV │
    │        │               │   │    │
    │                        │   │    │
    ├─────► PARTITIONS  ─────┴───┘    │
    │                                 │
                                      │
  DISKS ──────────────────────────────┘

