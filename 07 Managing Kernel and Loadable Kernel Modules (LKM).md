Capitolo 15 di Linux  -- Occupy the web

#### What is the kernel ?
Any O.S. ha almeno due parti:
KERNEL : 
- Accesso privilegiato al sistem
- Controlla tutto quello che fà il S.O.
	- Manage memory
	- control CPU
	- ECC. ECC. 
USER LAND ( TUTTO IL RESTO )

##### Kernel is monolitick
But kernel can need an update (e.g. USB o BLUETOOTH managment) e in passato si doveva ricompilare il kernel.
Ora invece meccanismo di Loadable Kernel Module ovvero **LKM**.
Ovvero aggiungere dei moduli a richiesta se necessari. 
(nota che moduli hanno necessita di Low Level Access e quindi possono dare origine ad attacchi molto gravi - ROOTKIT)

##### **Gestione del kernel e dei moduli**
_root > uname -a_  ---> per sapere il kernel in uso 
_root> cat /proc/version_ ---> piu informazioni
all this to gather info on kernel

##### Tune the kernel
Usa sysctl ---> Cambi effettuati permangono fino al reboot
Per renderli permanenti cambia /etc/sysctl.conf (CAUTELA!!)

Comando utile è 
_root > sysctl -a | less_
per analizzare. 
Per esempio analizziamo ipv4 e si vede net.ipv4.ip-forward=0 ovvero non fa forward per default. 
Come hacker se voglio avere invece il forward basta cambiarlo a 1 (fa forward)
Da un punto di vista difensivo si puo ad esempio disabilitare ICMP (non risponde a ping)

**Manage the module**
Esistono due modi:
_root >lsmod_ fornisce i moduli attivi
_root> insmod_ per inserire moduli
_root>rmmod_ per rimuovere i moduli
_root> modinfo <<nome modulo>>_ da informazioni sul modulo 
