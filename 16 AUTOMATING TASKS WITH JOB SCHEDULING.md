##### Cron and crontab
Comandi e concetti sono **cron** e **crontab**

**cron** is a daemon and **crontab** is a table of execution of job using cron 
To edit crontab use
kali > crontab -e 

La tabella mostra i campi che saranno 

M H DOM MON DAY USER COMMAND 
(Minute 0-59) (0 23Ora)  (Month 1-12) (DayOfMonth 1 -31) (giornoSettimana0-7) (utente )(comando )

Useful shortcut

@yearly
@noon
@midnight
@reboot
e altri leggiteli eventualmente

##### Using rc scripts to run job at startup

At startup many scripts are run ----> **rc scripts**

Boot ha seguenti fasi
- Kernel inizializza e carica i moduli
- Poi inizia il daemon **init** (o **initd**) che lancia i servizi necessari per Linux
Esiste il concetto di **runlevel** ovvero a seconda del runlevel vengono eseguiti i relativi rc scripts. I run level sono:
- 0 Halt
- 1 Single User/ Minimal
- 2 - 5 Multiuser mode 
- 6 Reboot

Come aggiungo servizi? Lavorando su **rc.d** con :
kali > update-rc.d <newScriptOrService> <remove|default|disable|enable> 

Esempio vuoi avere avviato all inizio postgresql
- verifica che esiste il servizio con *kali> ps aux | grep postgresql*
- poi fai *kali > update-rc.d postgresql -default* 
Al riavvio ti rendi conto che il servizio postgresql viene avviato autonomamente. 
