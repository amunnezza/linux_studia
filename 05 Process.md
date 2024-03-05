- How to 
	Find
	View 
	Which use more resource
- Can run in :
	-  Background
	- Prioritaize and schedule
	- Kill

root > ps -----> PID TTY TIME CMD         (ONLY THE ONE FOR USER)

ROOT> ps -aux  (all the process of all user)

Can filter with name 
es: lancia metasploit e poi :

root> ps aux | grep msfconsole 
da tutti i processi con msfconsole

## check dal piu ingordo 
root> top 

## Change priority
Il concetto base è che processi si contendono risorse
Puoi usare *nice* to give priority
every process can have priority  -20 < 0 < 19 con -20 il migliore e 19 peggiore di default

owner of process can only lower priority
root can do whtaever

es: 
root> nice -n -10  /bin/fasterProcess
root> nice -n +10  /bin/slowerProcess

Esiste anche renice che(vuole valore assoluto e PID del processo)
Per esempio vuoi rallentare un fastProcess con PID 334 
root> renice 20 334 

Anche da root> top 
premi R e dai PID e nice value

## kill a process

root> kill -signal PID  
i signal possono essere 
1 - restart
2 Terminate 

## lanciare in background 
A volte conviene lanciare il programma e chiudere la shell. Per esempio 
*root > mousepad prova.txt*
 lancia editor ma rimane la finestra di shell aperta. Allora conviene usare 
*root> mousepad prova.txt **&***
per riportare in foreground usa 
*root> fg NomeProcesso (oppure PID? )*

## Scheduling 
Scheduling puo essere utile ad esempio con backup fatti a un certo orario

root> at <TIME>
			. time ha molti formati
entra in modalita interattiva e specifici i comandi che vuoi eseguire 

**Funziona una volta sola**    


Per scheduling permanente usa cron (vedremo dopo)


