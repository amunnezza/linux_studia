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
crw ___ ___ ecc. (char device) Byte per Byte
brw ___ ___ ecc (block device) A Bocchi (maggiore velocita usato per esempio in CdRom)
Per avere informazioni sui dispositivi di tipo block usi 
*kali> lsblk*

#### Mounting and umounting device
Osserva anche che i device anche se presenti in dev non sono accessibili a meno che non crei **"una connessione logica "**
in pratica devi usare un *mount*  
In alcuni sistemi attivato automount ma in altri no quindi bene conoscere come fare
kali > mount /dev/sda1 /mnt aggiungendo eventualmente dei parametri (dici si dove montarlo ma anche come deve essere trattato)

Per smontarlo (eject) usare 
kali > umount /dev/dispositivo

NB per procedere al umount il dispositivo NON deve essere in uso in lettura o scrittura altrimenti da errore.

##### Info on mounted disk

Usa
*kali> df* 
che fornisce informazioni su tutti i dispositivi montati compreso partizioni presenti con tipo.

Info su errori eventuali si usa 
*kali > fschk*