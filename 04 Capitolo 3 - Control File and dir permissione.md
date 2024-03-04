
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
root> chmod u-w, o+x nomeFile

