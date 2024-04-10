

Every OS have two major component.

First is the **Kernel**
The other part is **userland**

Kernel is a privileged part and is the coordinator of other part to interact each other.

#### Linux kernel
By design is **monolithic** but have option to add **module** for function addiction.

#### Why modules.
Often kernel need update (eg. driver) to work properly but to avoid recompilation Linux use the **LKM** (Loadable Kernel Module) system where you add module as addiction to Monolithic kernel. 

#### Comandi

*kali > uname -a* 
*kali > cat /proc/version** 

Both give info on kernel like 
```sh
Linux version 6.6.9-amd64 (devel@kali.org) (gcc-13 (Debian 13.2.0-9) 13.2.0, GNU ld (GNU Binutils for Debian) 2.41.50.20231227) #1 SMP PREEMPT_DYNAMIC Kali 6.6.9-1kali1 (2024-01-08)

```
##### Gestione Moduli 
###### Moduli presenti
*kali > sysctl -a* 
restituisce centinaia di parametri usati per coordinare i moduli.
conviene usare qualcosa del tipo 
*kali > sysctl -a | less* 
per poi eventualmente usare i metodi di ricerca di less (ricorda ad esempio che in less è interattivo e puoi usare */ParolaChiave* per effetuare ricerca sull'output)

###### Modificare comportamento moduli
sysctl viene configurato da sysctl.conf e quindi il comportamento di sysctl si puo modificare con (fa esempio di voler abilitare ipv4.portformarding per far ritrasmettere i pacchetti come desiderato da un hacker) 
- modifiche direttemente su sysctl.conf (nell'esempio poni la voce net.ipv4.ipforward = 1 )
- modifica (SOLO PER LA SESSIONE)usando direttamente sysctl (usi il comando kali> sysctl -w net.ipv4.ip-forward=1 )
Altro esempio se per sicurezza vuoi disabilitare ICMP (non risponde piu al ping) puoi cambiare la voce net.ipv4.icmp-echo-ignore-all=1 con i modi visti sopra)
###### Gestione moduli (inserire )
  Esistono due metodi uno basato su una suite *insmod* e l'altra piu moderna usando *modprobe*. 
Usando la suite insmode per avere informazioni sui moduli puoi usare 
*kali > lsmod*  ( da lista dei moduli ) unito a  *kali > modinfo nomeModulo* il secondo da molte info tra qui le dipendenze. 
La suite comprende anche i comandi *insmod* e *rmmod* che sono imperfetti perchè NON GESTISCONO dipendenze tra i moduli e togli quello sbagliato ottieni come minimo un sistema instabile. 

Si preferisce quindi usare ***modprobe***
*kali > modprobe -a NomeModulo*  (add module)
*kali > modprobe -r NomeModulo*  (remove module)
**che hanno il grosso vantaggio di gestire le dipendenze**


EXERCISES  
1. Check the version of your kernel. 
2. List the modules in your kernel. 
3. Enable IP forwarding with a sysctlcommand. 
4. Edit your /etc/sysctl.conf file to enable IP forwarding. Now, disable IP forwarding. 
5. Select one kernel module and learn more about it using modinfo
