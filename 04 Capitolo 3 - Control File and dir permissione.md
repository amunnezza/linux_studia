
Gruppi - Facilità gestione

Permessi **r w x**
check permission with **ls -l**

d       rwx     -r-       _ _ _
Tipo owner Group users

## To change permission:

Decimal NOtation
r--  rwx  rw_ 
100 111 100    --> chmod 475  nomeFile
4      7     5

Using UGO (USER GROUP OWNER)

lucio> chmod u-w (toglie write permissioni to user)
possibile molti permessi in un solo comando es:
*root> chmod u-w, o+x nomeFile*

## OTHER PERMISSION
 SUID 
 Set superuser access on a file with a bit 
 In command line get SUID with a 4 before the "normal" access value 
(es. root> chmod 4644 NomeFile )
Utilità per esempio user to change his own password must accessw /etc/shadow 

SGID 
Simile a SUID ma da diritti come quelli del Gruppo cui appartiene owner 
Si usa 2 prima dei diritti normali
es root >chmod 2466 NomeFile

STICKY 
non si usa più in Linux