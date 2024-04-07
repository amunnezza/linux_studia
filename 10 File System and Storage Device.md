Base concept : **EVERYTHING IS A FILE** 

- Start from **/dev**
  It is a list of the device. eg.
  sda ---> primo Hard Disk
  sda1 ---> prima partizione del HD sda
  sda2 ---> seconda partizione di HD sda ecc. ecc.
Per default lista è alfabetica.
Per vedere le partizioni usa 
*kali> fdisk -l*

Osserva anche che esiste il device loop. 
Osserva anche che i device possono essere 
crw ___ ___ ecc. (char device)
brw ___ ___ ecc (block device)

Osserva anche che i device anche se presenti in dev non sono accessibili a meno che non crei **"una connessione logica "**
in pratica devi usare un *mount* 
kali > mount /dev/sda1 /mnt aggiungendo eventualmente dei parametri (dici si dove montarlo ma anche come deve essere trattato)