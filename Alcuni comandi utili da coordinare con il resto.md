
REGOLE PER BACKUP 3 - 2 - 1

3 DATA COPIES 

2 DEVICES 
	- usb flash drive
	- ssd disk
	- external ssd disk 
	- ecc. ecc.
1 OFFSITE COPY
	- cloud
	- disk in safe somewhere
	- disk in car
	- ecc.ecc. 

----- 


per compresso file 

kali> zip -r <nomeFileCompresso.zip> <nome Directory>

per mettere criptaggio usa 

kali> zip --encrypt -r <nomeFileCompresso.zip> <nome Directory>
 (chiede password per aprire)

come protezione non è il massimo perchè anche senza password puoi comunque vedere quali file contiene con i suoi metadata

Esistono anche altri algoritmi di compressione (7z - xzip) e uniti a tar che non comprime ma archivia (vedi lezione)

Un ulteriore layer di protezione si puo ottenere con gpg (il manuale interessante ma lungoooooo)

kali> gpg -c <filezip.zip>
(domanda una passphrase - in sostanza una password) 
crea un file chiuso da gpg che non ti fa vedere niente se non conosci la passphrase 
(quindi zippato magari con password e poi criptato per non far vedere il contenuto nemmeno cosa e i metadati)
(In realta usando gpg puoi anche non zippare con password, perche anonimo garantito da gpg)

Nota che gpg tende a ricordare le password messe per cui se ad esempio dai 
kali> gpg nomefile.zip.gpg 
puo succedere che se lo hai criptato sullo stesso computer te lo esplode senza altri problemi

-----

su uno delle macchine (ad esempio ubuntu based)
ubuntu> sudo apt-get update

ubuntu> sudo apt-get install openssh-server

setta password dell user

ubuntu> sudo passwd ubuntu
  <aggiona passwordo>

ubuntu> ip a s | grep inet ---> (ricavi indirizzo ip) (esempio 192.168.1.10)


controlla se sta girando il server openssh

ubuntu> sudo service ssh status

controlla che è in stato active/running. 
Sempre riguardo questa macchina fai 
ubuntu> whoami (per sapere chi sei osboxes
ubuntu> pwd (/home/osboxes)

Passo successivo è quello di partire da un altro computer e copiare dei file in maniera sicura

Supponi sei in kali in una dir con il file segreto.txt allora fai:

kali> scp <nomeFile> <utenteRemoto>@<ip_remoto>:<directory remota/>

ti chiede di aggiungere la chiave tra le tue e di mettere password dell'utente remoto

Funziona ho provato
Funziona anche con sftp se fai qualcosa del tipo

kali> sftp <utenteRemoto>@<ip o nome server remoto>

entri in un interfaccia del tipo 
sftp> (puoi usare vari comandi tipo ls e altri che puoi vedere facendo 
sftp> help 

Chiaramente la piu potente è  

kali> ssh <utenteRemoto>@<ip o nome server remoto>

da accesso al terminale sul server remoto ed hai stessi privilegi come se fossi in locale


Nota bene funziona anche su windows installando openssh sui server e comandi similari per quanto r4iguarda scp e o 
sftp su windows

-----
Cancellare e sovrascrivere con 

root > shred -u -z -n 5 NomeFileDaDistruggere.txt  (-u cancella alla fine -z sovrascrive con zero - n 5 numero di volte che sovrascrive)

Creare fingerprint di file usando funzioni di hash come 

kali > sha256sum  nomeFile.txt   ---> dara un codice unico per quel file. Se lo cambi il risultato cambia anche lui

NB Esistono molti algoritmi di hash come MD5 ad esempio
Ricorda che il concetto di hash nasce da algoritmo per effettuare una ricerca lineare (vedi libro su algoritmi)




