
Un corso a parte con Cannon. 
Solo alcune info.
**RICORDA SHEBANG**

**SET** execute permission (chmod 755 nomeScript.sh ed esegui con ./nomeScript.sh)

**VARIABILI**:

read nomeVariabile # da 

```sh
#!/bin/bash

#script per dare valori a due variabili e metterle a video
echo "come ti chiami?"
read NOME 

echo "A che capitolo sei arrivato?"
read CAPITOLO

echo "benvenuto ${NOME} bravo che sei riuscito ad arrivare sino al capitol ${CAPITOLO}"

```
##### Primo script da hacker

Facciamo uso di nmap per cercare in rete locale se esiste porta 3306 per mysql

```sh
#!/bin/bash


echo "enter start ip address"
read FIRSTIP

echo "enter last octec of the last iPaddress"
read LASTOCTET

echo "enter the port"

read PORT


 nmap -sT ${FIRSTIP}-${LASTOCTET} -P3306 > /dev/null -oG MySQLscan
 cat MySQLscan | grep open > MySQLscan2
	 cat MySQLscan2

```

| Command | Function                |
| :-----: | ----------------------- |
|  **:**  | Return 0 or true        |
|  **.**  | Executes a shell script |

Command Function  . bg Puts a job in the background break Exits the current loop cd Changes directory continue Resumes the current loop echo Displays the command arguments eval Evaluates the following expression exec Executes the following command without creating a new process exit Quits the shell export Makes a variable or function available to other programs fg Brings a job to the foreground getopts Parses arguments to the shell script jobs Lists background (bg) jobs pwd Displays the current directory read Reads a line from standard input readonly Declares as variable as read-only set Lists all variables shift Moves the parameters to the left test Evaluates arguments [ Performs a conditional test times Prints the user and system times trap Traps a signal type Displays how each argument would be interpreted as a command umask Changes the default permissions for a new file unset Deletes values from a variable or function wait Waits for a background process to complete


EXERCISES Before you move on to Chapter 9, try out the skills you learned from this chapter by completing the following exercises: 
1. Create your own greeting script similar to our HelloHackersArise script. 
2. Create a script similar to MySQLscanner.sh but design it to find systems with Microsoft’s SQL Server database at port 1433. Call it MSSQLscanner. 
3. Alter that MSSQLscanner script to prompt the user for a starting and ending IP address and the port to search for. Then filter out all the IP addresses where those ports are closed and display only those that are open