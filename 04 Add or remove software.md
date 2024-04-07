Concetto di repository.
Esistono diversi tipi di package manager (essenzialmente sono **apt** per debian e sue derivate e **yum** per red hat e derivate anche se ne abbiamo un altra per le derivazioni di Centos che è stata discontinuata e sostituita da RockyLinux e AlmaLinux vedere come si chiama)

Concetto di repository

comandi :

*kali > apt cache search <packageName>**
*
*kali > apt install <packageName>**
*
*kali > apt -get remove  <packageName>*
NB rimuove il package ma NON i config files unless you use option purge

*kali > apt-get purge  <packageName>*

UPDATE CON NUOVE VERSIONI 
*kali > apt-get update*
*kali > apt-get upgrade*


Aggiungi repository in /etc/apt/sources.list








