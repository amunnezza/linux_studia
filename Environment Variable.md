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

Environment variables are always uppercase are only the default environment variables that come on your system. 
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
This means that when you close the terminal, any changes you made are lost and values set back to their defaults. 
To make the changes permanent use the **export** command. 
will export the new value from your current environment (the
bash shell) to the rest of the system, making it available in every
environment until you change and export it again
.
Variables are strings, so  cautious side is  save the contents of a variable to a text file before you modify it.
For example, if we change the PS1 variable, which controls
the information you display in the prompt, first save the existing values to a text file in the current user’s home directory:
*kali >echo $HISTSIZE> ~/valueofHISTSIZE.txt*

so  you can always undo your changes. Can  be even more cautious and create a text file with all the current settings:
*kali >set> ~/valueofALLon01012017.txt*

you can make the change permanent by export:
*kali >export HISTSIZE*

Now the HISTSIZE  set to 0. To reset HISTSIZE variable to 1,000:
*kali >HISTSIZE=1000*
*kali >export HISTSIZE*

Esempio cambio Shell Prompt
La shell prompt da info . Di default è in forma :
username@hostname:current_directory
I
Agendo come root avra forma:
root@kali:current_directory

Puoi cambiarlo agendo sulla variabile  PS1. 
PS1  has a set of placeholders for info you want display on prompt like:
\u The name of the current user
\h The hostname
\W The base name of the current working directory

This is very useful if you  have shells on multiple systems or are logged on as multiple accounts. 
By setting different \u and \h values for different shells or accounts, you can tell at a glance who you are and what your current system is.

Example: 
kali >PS1="World's Best Hacker: #"

World's Best Hacker: #
Now, every time you use this terminal, you’ll be reminded that you are
the “World’s Best Hacker.”
But any subsequent terminal you open will still have the default prompt, because  PS1  holds
values for your terminal session  until you export a variable
with 
_kali > export PS1_


If you really like this new command prompt
and want to see it in every terminal, you need to export it, like so:
kali >export PS1
This will make the change permanent across all sessions.
How about a little more fun? Say you really want your terminal to look
like a Windows cmd prompt. In this case, you could change the prompt
name to C: and keep the \w to have the prompt show your current
directory, as shown in Listing 7-2.
kali >export PS1='C:\w> '
C:/tmp>
Listing 7-2: Changing the prompt and showing the current directory
Having your prompt show your current directory can be generally
useful, particularly to a beginner, so it’s something to consider when you
change your PS1 variable.
Changing Your PATH
One of the most important variables in your environment is your PATH
variable, which controls where on your system your shell will look for
commands you enter, such as cd, ls, and echo. Most commands are located
in the sbin or bin subdirectory, like /usr/local/sbin or usr/local/bin. If the
bash shell doesn’t find the command in one of the directories in your PATH
variable, it will return the error command not found, even if that command does
exist in a directory not in your PATH.
You can find out which directories are stored in your PATH variable by
using echo on its contents, like so:
kali >echo $PATH
/usr/local/sbin:usr/local/bin:/usr/sbin:/sbin/bin
These are the directories where your terminal will search for any
command. When you enter ls, for example, the system knows to look in
each of these directories for the ls command, and when it finds ls, the
system executes it.
Each directory is separated by a colon (:), and don’t forget to add the $
content symbol to PATH.
Adding to the PATH Variable
You can probably see why it’s important to know what is in your PATH
variable: if you downloaded and installed a new tool—let’s say
newhackingtool—into the /root/newhackingtool directory, you could only use
commands from that tool when you’re in that directory because that
directory is not in the PATH variable. Every time you wanted to use that
tool, you would first have to navigate to /root/newhackingtool, which is a
bit inconvenient if you want to use the tool often.
To be able to use this new tool from any directory, you need to add the
directory holding this tool to your PATH variable.
To add newhackingtool to your PATH variable, enter the following:
kali >PATH=$PATH:/root/newhackingtool
This assigns the original PATH variable plus the /root/newhackingtool
directory to the new PATH variable, so the variable contains everything it
did before, plus the new tool directory.
If you examine the contents of the PATH variable again, you should see
that this directory has been appended to the end of PATH, as shown here:
kali >echo $PATH
/usr/local/sbin:usr/local/bin:/usr/sbin:/sbin/bin:/root/newhackingtool
Now you can execute newhackingtool applications from anywhere on your
system, rather than having to navigate to its directory. The bash shell will
look in all directories listed for your new tool!
NOTE
Adding to PATH can be a useful technique for directories you use often, but
be careful not to add too many directories to your PATH variable. Because
the system will have to search through each and every directory in PATH to
find commands, adding a lot of directories could slow down your terminal
and your hacking.
How Not to Add to the PATH Variable
One mistake commonly made by new Linux users is assigning a new
directory, such as /root/newhackingtool, directly to the PATH variable in this
way:
kali >PATH=/root/newhackingtool
kali >echo $PATH
/root/newhackingtool
If you use this command, your PATH variable will only contain the /root/
newhackingtool directory and no longer contain the system binaries
directories such as /bin, /sbin, and others that hold critical commands.
When you then go to use any of the system commands, you’ll receive the
error command not found, as shown next, unless you first navigate to the system
binaries directory when you execute the command:
kali >cd
bash: cd: command not found
Remember that you want to append to the PATH variable, not replace it. If
you’re in doubt, save the contents of the variable somewhere before you
modify it.
Creating a User-Defined Variable
You can create your own custom, user-defined variables in Linux by
simply assigning a value to a new variable that you name. This may be
useful when you are doing some more advanced shell scripting or find
you’re often using a long command that you get tired of typing over and
over.
The syntax is straightforward: enter the name of your variable,
followed by the assignment symbol (=), and then the value to put in the
variable, as shown here:
kali >MYNEWVARIABLE="Hacking is the most valuable skill set in the 21st century"
This assigns a string to the variable MYNEWVARIABLE. To see the value in that
variable, use the echo command and the $ content symbol with the variable
name, as we did earlier:
kali >echo $MYNEWVARIABLE
Hacking is the most valuable skill set in the 21st century
Just like our system environment variables, user-defined variables must
be exported to persist to new sessions.
If you want to delete this new variable, or any variable, use the unset
command. Always think before deleting a system variable, though,
because your system will probably operate much differently afterward.
kali >unset MYNEWVARIABLE
kali >echo $MYNEWVARIABLE
kali >
As you can see, when you enter unset MYNEWVARIABLE, you delete the
variable along with its value. If you use echo on that same variable, Linux
will now return a blank line.
Summary
You might find environment variables foreign, but it’s worth getting to
know them. They control how your working environment in Linux looks,
acts, and feels. You can manage these variables to tailor your environment
to your needs by changing them, exporting them, and even creating your
own. In some cases, they may be useful for covering your tracks as a
hacker.
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