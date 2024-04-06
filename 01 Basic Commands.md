Capitolo 1 Occupy the web - Book on linux
Chi sono --> __*whoami*__
Dove sono --> __*pwd*__
## Navigate file system
*__cd__* change directory
	path assoluto **_cd /home/lucian_**
	path relativo __*cd ./sopra*__ (dalla dir in cui sei data dal punt  a sopra )
	path scendi di un livello con __*cd ..*__ e puoi scendere di quanti livelli vuoi con 
	**_cd ../../usr_**
## Listing content of directory

**_ls_** comando con opzioni -a (mostra nascosti) -l (da piu info ) usa molto **_ls -la_**

## Getting help

**_man_** seguito dal nome del comando 
oppure anche 
**_nomeComando -h_** o anche **_nomeComando --help_**
 
## Finding Stuff
 
**_locate nomeOggetto_**

per i file binaries usi anche 
**_whereis nomeBinaries_**
	
per binaries in path usa 
**_which BinariesInPath_**

Il piu potente è __*find*__
find *directory options expression*
es.
**_find /etc -type f -name apache2.*_**
Trova da directory /etch  - di tipo file  con nome apache2 e qualunque estensione

## Filtri con grep

**Concetto di piping con |** 
Spesso output di un comando serve in piping su un altro comando.
Ora per esempio kali> **_ps aux_** mi da tuti i processi che girano ma se mi serve solo sapere i processi con una certa keyword lo mando in pipe a **grep** usando

kali> **_ps aux | grep apache2_** mi ritorna solo i processi che hanno apache2

## Modifica files e directory

### Creare files

**_cat_** serve a concatenare files ma se faccio **_cat > nomeFile_** crea il file e quello che inserisci dopo andra nel file. Puo confondere perchè cat va in interactive mode e per uscire devi usare Ctrl+d
Per esempio se fai 
 **_cat > nomeFile_**  (enter e va in interactive mode)
 _voglio inserire questo nel file_ (sono in interactive mode e inserisce )
 (esco con Ctrl+d) 
 ora in nomeFile trovi quello che hai scritto
Per appendere sul file usi 
**_cat >> nomeFile_** 
_voglio aggiungere questo _ 
(Ctrl+d)

per veder usi 
**_cat nomeFile_**

per sovrascrivere usi di nuovo 
**_cat > nomeFile_**

-----
comando **touch**
_____
Crea directory
kali> _**mkdir**_ nomeDirectory
_______
Copia file 
kali> **_ cp oldFile /root/newDir/newFile_**

Rinomina usi move !!
kali> **_mv oldFilename newFilename_**

Cancelli con 
kali> **_rm nomeFile_**
e per directory
kali > **_rmdir nomeDir_**  (NB FUNZIONA SOLO CON DIR VUOTE !!)
PER RIMUOVERE E ITERATIVAMENTE ANCHE CONTENUTO USA OPZIONA -r

kali> **_rmdir -r nomeDir_**


EXERCISES Before you move on to Chapter 2, try out the skills you learned from this chapter by completing the following exercises: 
1. Use the lscommand from the root (/) directory to explore the directory structure of Linux. Move to each of the directories with the cdcommand and run pwdto verify where you are in the directory structure. 
2. Use the whoami command to verify which user you are logged in as. 
3. Use the locate command to find wordlists that can be used for password cracking. 
4. Use the cat command to create a new file and then append to that file. Keep in mind that >redirects input to a file and >>appends to a file. 
5. Create a new directory called hackerdirectory and create a new file in that directory named hackedfile. Now copy that file to your /root directory and rename it secretfile.
