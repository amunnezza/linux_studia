Cap. 7 Occupy the web - Linux for Hacker
environment variables crucial argument.
There are two types of variables: **shell** and **environment**. 
#### Environment variables 
system-wide variables built into your system and interface.
Control the way your system looks, acts, and “feels” to the user,are inherited by any child shells or processes. 
#### Shell variables
typically listed in lowercase and are only valid in the shell they are set in.


**Variables** are simply strings in key-value pairs. 
KEY=value. 
Can have multiple values, 
KEY=value1:value2. 
As with most things in Linux, if there are spaces in the value, it needs to be contained in quotation marks. 

Often  Linux environment is your bash shell. 
Each user, including root, has a default set of environment variables that determine how the system looks, acts, and feels. 
You can change the values for these variables to tailor your need.

#### Viewing and Modifying Environment Variables
Can view all your default environment variables by entering *env* 

*kali >env*
XDG_VTNR=7
SSHAGENT_PID=922
XDG_SESSION_ID=2
XDG_GREETER_DATA_DIR=/var/lib/lightdm/data/root
GLADE_PIXMAP_PATH=:echo
TERM=xterm
SHELL=/bin/bash
--snip--
USER=root
--snip--
PATH=/usr/local/sbin :usr/local/bin:/usr/sbin:/sbin/bin
--snip--
HOME=/root
--snip--

Environment variables are
- always uppercase 
- are the default environment variables  
User can create their own variables and  include those in the output.

##### Viewing All Environment Variables
To view all environment variables  *set* command. 
list all environment variables unique to your system. Long output so use piping to more

***kali >set | more***
*BASH=/bin/bash*
*BASHOPTS=checkwinsize:cmdlist:complete_fullquote:expand_aliases:extglob.....*
*BASH_ALIASES=()*
*BASH_ARGC=()*
*BASH_ARGV=()*
*--snip--*

##### Filtering for Particular Variables
Let’s use the variable HISTSIZE as an example. :

*kali >set | grep HISTSIZE
HISTSIZE=1000*

As you can see the default value set to 1000  This indicates that the terminal will store your last 1,000 commands by default.

##### Changing Variable Values for a Session
As noted, the HISTSIZE is the value of the number of commands to store in the
history file. 
Sometimes, you won’t want your system to save past commands—perhaps because you don’t want to leave any evidence of your activity on your own system or a target system. 
In that case, you can set the HISTSIZE variable to 0 

*kali >HISTSIZE=0**

Now, when you try to use the up- and down-arrow keys to recall your
commands, nothing happens because the system no longer stores them.
This is stealthy, although it can be inconvenient.

##### Making Variable Value Changes Permanent
That change only occurs in that particular environment; in this case, that environment is the bash
shell session. 
This means that when reopen  the terminal changes  are lost and values set back to defaults. 
To make the changes permanent use the **export** command. 
Il nuovo valore dal attuale ambiente (the bash shell) andra nel resto del sistem disponibile in ogni ambiente.

Variabili sono stringhe quindi accortamente salva i valori prima di modificarli.
Es. PS1 controlla info del prompt:
Prima salvi il valore in file di testo :
*kali >echo $HISTSIZE> ~/valueofHISTSIZE.txt*
per ristabilirlo se vuoi dopo.

Ancora meglio salva tutti i settings correnti con 
*kali >set> ~/valueofALLon01012017.txt*

Rendi cambio permanente con:
*kali >export HISTSIZE*

Per tornare indietro a 1,000:
*kali >HISTSIZE=1000*
*kali >export HISTSIZE*

Esempio cambio Shell Prompt
La shell prompt da info . Di default è in forma :
username@hostname:current_directory
I
Agendo come root avra forma:
root@kali:current_directory

Puoi cambiarlo agendo sulla variabile  PS1. 
PS1  ha set di segnaposto come :
**u** The name of the current user
**h** The hostname
**W** The base name of the current working directory

Molto utile se hai molte macchine o molti terminali su diversi accounts.
Usando diversi u ed h per shell diverse puoi capire subito cosa stai usando e chi sei
Example: 
kali >PS1="World's Best Hacker: #"
World's Best Hacker: #
Quando usi questo terminale sai che sei il  “World’s Best Hacker.”
Altri non lo hanno e avranno il prompt di default a meno che non esporti
_kali > export PS1_

How about a little more fun? Say you really want your terminal to look
like a Windows cmd prompt. In this case, you could change the prompt
name to C: and keep the \w to have the prompt show your current
directory, as shown in Listing 7-2.
kali >export PS1='C:\w> '
C:/tmp>

Listing 7-2: Cambiare  prompt mostra  current directory di solito serve 

##### Changing Your PATH
PATH molto importante. Dice dove il sistema cerca i comandi di shell. Se non trova nelle directory della PATH da errore anche se esiste ma fuori dal PATH. 
_kali >echo $PATH
/usr/local/sbin:usr/local/bin:/usr/sbin:/sbin/bin_
mostra le directory separati da semi colon. 

- Adding to the PATH Variable

Important to add tool in unusual directory.
if you downloaded and installed a new tool newhackingtool  into the /root/newhackingtool can use only if sei in quella dir (noiioso andarci ogni volta). 
Allora aggiungi alla variabile PATH CON 
_kali >PATH=$PATH:/root/newhackingtool_

**VA FATTO COSI PER AGGIUNGERE A PATH GIA ESISTENTE. SE non fai cosi e fai 
kali >PATH=/root/newhackingtool
il PATH SARA SOLO QUELLA DIRECTORY E NON FUNZIONA PIU NIENTE.**
Nota anche che  $PATH con troppi elementi rallenta perchè va a cercare in tutte le directory.

##### Creating a User-Defined Variable
Semplicemente assegni un valore a un nome di variabile che ti piace.
_kali >MYNEWVARIABLE="Hacking is the most valuable skill set in the 21st century"_
Vedi anche corso script e nota che in assegnazione nessuno spazio. 
Devi export per farlo persistere. 
Per **cancellare** usa unset ad es:
kali >unset MYNEWVARIABLE
che darà 
kali >echo $MYNEWVARIABLE
kali >
EXERCISES
Before you move on to Chapter 8, try out the skills you learned from this chapter by
completing the following exercises:
1. View all of your environment variables with the more command.
2. Use the echo command to view the HOSTNAME variable.
3. Find a method to change the slash (/) to a backslash (\) in the faux Microsoft cmd
PS1 example (see Listing 7-2).
4. Create a variable named MYNEWVARIABLE and put your name in it.
5. Use echo to view the contents of MYNEWVARIABLE.
6. Export MYNEWVARIABLE so that it’s available in all environments.
7. Use the echo command to view the contents of the PATH variable.
8. Add your home directory to the PATH variable so that any binaries in your home
directory can be used in any directory.
9. Change your PS1 variable to “World’s Grea