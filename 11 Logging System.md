Debian usa come demone di logging rsyslog
In realta ogni sistema usa il suo metodo. 
Interessante è andare in cerca di rsyslog che è il demone piu usato. 
Comincia a guardare rsyslog.conf che file di configurazione (nel kali attuale in realta è il file /etc/syslog.d/50-default.conf) . 
Ci concentriamo su RULES

FORMATO RULES SARA

**facility.priority action** 
qualeServizio.chePrioritaMiInteressa cosaFare

Per la gestione dei log quali frequenza e dove salvarli vedere logrotate che permette anche un po di pulizia. 
Visto poi qualcosa con il comnado shred per sovrascrivere
(usare shres --help per info)

Per rimanere stealth usare anche i comandi 
> service NOmeServizio start|stop|restart 

andando a fermare i servizi di logging
