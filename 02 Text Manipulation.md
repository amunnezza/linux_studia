Reference: Ch 2 of Occupy the Web - Linux

Almost **everything is a File, often text**

So text manipulation is a must. 
For experimenting use snort configuration files.

1. simplest viewer is **cat**   
2.  uso di ***head*** and ***tail*** per vedere inizio e fine file (di default 10 righe) 
3. utilità di usare ***nl***  per visualizzare aggiungendo numero di linea (utile per ricerca termini unito a grep)
#### Filtering with grep 
Lo vedremo piu in dettaglio per ora semplice ricerca per esempio (grep utility per regular expression in bash)

**kali** > *cat /etc/snort/snort.conf | grep output* > 
> [!Risultato]- 
>  (kali㉿kali)-[~/Documents]
└─*$ sudo nl    /etc/snort/snort.conf | grep output*
   445  # Step #6: Configure output plugins
   450  # output unified2: filename merged.log, limit 128, nostamp, mpls_event_types, vlan_event_types
   451  output unified2: filename snort.log, limit 128, nostamp, mpls_event_types, vlan_event_types
   453  # output alert_unified2: filename snort.alert, limit 128, nostamp
   454  # output log_unified2: filename snort.log, limit 128, nostamp 
   456  # output alert_syslog: LOG_AUTH LOG_ALERT
   458  # output log_tcpdump: tcpdump.log

NOTA BENE PER FAR SCOMPARIRE IL RIQUADRO USA IL SEGNO '-' DOPO il link
**kali** > *nl /etc/snort/snort.conf | grep output*  : per veder numeri di linea dove appare il filtro 

>[!Risultato]-
>sudo nl    /etc/snort/snort.conf | grep output 
  > 33  #  6) Configure output plugins
   > 445  # Step #6: Configure output plugins
   > 450  # output unified2: filename merged.log, limit 128, nostamp, mpls_event_types, vlan_event_types
   > 451  output unified2: filename snort.log, limit 128, nostamp, mpls_event_types, vlan_event_types
   > 453  # output alert_unified2: filename snort.alert, limit 128, nostamp
   > 454  # output log_unified2: filename snort.log, limit 128, nostamp 
   > 456  # output alert_syslog: LOG_AUTH LOG_ALERT
   > 458  # output log_tcpdump: tcpdump.log

Let’s say you want to display the five lines immediately before a line that says 
 *Step #6: Configure output plugins*

Un modo di risolsere è: 
>[!Primo Passo]-
>
>sudo nl --body-numbering=a   /etc/snort/snort.conf | grep output 
> /# body-numbering=a per contare anche righe vuote
  > 34  #  6) Configure output plugins
   529  # Step #6: Configure output plugins
   535  # output unified2: filename merged.log, limit 128, nostamp, mpls_event_types, vlan_event_types
   536  output unified2: filename snort.log, limit 128, nostamp, mpls_event_types, vlan_event_types
   539  # output alert_unified2: filename snort.alert, limit 128, nostamp
   540  # output log_unified2: filename snort.log, limit 128, nostamp 
   543  # output alert_syslog: LOG_AUTH LOG_ALERT
   546  # output log_tcpdump: tcpdump.log


> [!Secondo Passo]- Scoperto la riga procedi con il comando
> ```sh
sudo tail -n+529 /etc/snort/snort.conf | head -n 6
> # Step #6: Configure output plugins
> # For more information, see Snort Manual, Configuring Snort - Output Modules
###################################################
>
># unified2 
># Recommended for most installs

##### Using sed to find and replace 
***sed*** comando che in forma basilare trova e sostituisce

Esempio trova string mysql nel solito snort.conf

>[!comandi]- 
>```sh
 >                            
┌──(kali㉿kali)- /Documents]
└─$ sudo cat /etc/snort/snort.conf | grep mysql
sudo] password for kali: 
include $RULE_PATH/mysql.rules
>                                                                                                            
┌──(kali㉿kali)-[/Documents]
└─$ sudo sed s/mysql/MySQL/g /etc/snort/snort.conf > snort2.conf
>                                                                                                             
┌──(kali㉿kali)-[~/Documents]
└─$ cat snort2.conf | grep MySQL          
include $RULE_PATH/MySQL.rules
\#include $RULE_PATH/server-MySQL.rules
    >  ```                                                              

##### *more* e *less*

root> *more*  nomeFile 
fa visualizzare il file e si esce con q. Navigazione con enter o tasti freccia

Simile ma piu potente è ***less*** che in piu ha anche l'opzione di ricerca nel file visualizzato. Una volta lanciato puoi ricercare nel file con i il comando in basso a sinistra:

: /TermineDaCercare

puoi ripetere l'ultima ricerca con **n**
navigazione simile a vim . 
Le varie opzioni durante uso di less si hanno scrivendo  
:help 


Exercises 
Before you move on to Chapter 3, try out the skills you learned from this chapter by completing the following exercises: 
1. Navigate to /usr/share/wordlists/metasploit. This is a directory of multiple wordlists that can be used to brute force passwords in various passwordprotected devices using Metasploit, the most popular pentesting and hacking framework. 
2. Use the cat command to view the contents of the file passwords.lst. 
3. Use the more command to display the file passwords.lst. 
4. Use the less command to view the file passwords.lst. 
5. Now use the nl command to place line numbers on the passwords in passwords.lst. There should be 88,396 passwords. 
6. Use the tail command to see the last 20 passwords in passwords.lst. 
7. Use the cat command to display passwords.lst and pipe it to find all the passwords that contain 123


> [!question]- Can callouts be nested? 
>> [!todo]- Yes!, they can. 
> > > > [!example] You can even use multiple layers of nesting.


