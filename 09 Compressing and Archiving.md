
Primo comando è tar:

Il concetto è creare un unico file che ne contiene molti altri:

kali> tar -cvf NomeFile.tar  [lista di file o anche una intera directory]  
(c sta per create , v per verbose , f nome file)

Per vedere i file in un archivio usi 
*kali> tar -tvf NomeFile.tar*
Per estrarre usi 
*kali > tar -xvf NomeFile.tar*

NB tar è utility di ARCHIVIAZIONE quindi puo succedere che la dimensione supera la somma delle dimensioni dei file raggruppati. 

Per comprimere le dimensioni in linux ci sono 3 utility:
- bzip2 - compressione elevata ma lento (ideale per file piccoli)
 - compress - compressione meno buona ma veloce (ideale per file grandi)
 - gzip - una via di mezzo fra i due 
in generale utilizzo è

*kali> bzip2 NomeFile*  ----> NomeFile.bzip2

*kali> compress NomeFile* ----> NomeFile.z

#### CREATING BIT-BY-BIT OR PHYSICAL COPIES OF STORAGE DEVICES

Copia bit per bit usi dd con sintassi:

*kali > dd if=InputFile of=OutFile*

es. chiavetta usb in /dev/sdb sara

*kali> add if=/dev/sdb of=/root/flashUsbCopia*

NB dd MOLTO LENTO PERCHE FA COPIA BIT A BIT SOPRATTUTTO USATO PER SCOPI FORENSI. 