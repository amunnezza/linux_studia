**Network analysis crucial**

*root> ifconfig*
risultato sarà:
	<nomeInterface> <HWAddress - MAC> <InternetAddress IP> <Broadcast> <Mask>
Con queste info inizi a manipolare Network.

**root> iwconfig**
Per reti wireless
		wlan  (IEEE802.11)  (ESSID) (MODE:   )   (Not Associated)     (TXPower in db)
More info on [[14 Undenstanding and inspecting wireless Networks]] 


#### CHANGING NETWORK INFORMATION
Useful skill ---> spoofing (changing IP address)

root> ifconfig eth0  NEW.IP.ADDRESS network__.___.___.__broadcast __.__.__.__

#### CHANGING MAC ADDRESS
*> ifconfig eth0 down*
*> ifconfig eth0 hw 00.11.22.33.44.55*
*> ifconfig eth0 up*

#### Assigninign new address from DHCP
*> dhclient eth0* 
Manda una richiesta con DHCP discover e riceve un offerta con DHCP offer. 
___________
#### Manipulating DNS 
Approfondimento su DNS si trova in [[DNS Tutorial part - DNS basics – DNS monitor]]

Analisi di DNS si puo fare con il comando 
_root> dig nomeDominio.com ns_
che fornisce molte info ad esempio IP del server 
Esiste anche per server mail con il comando simile 
_root> dig nomeDominio.com mx_

In generale in linux can check resolve.conf per vedere i nameserver e eventualmente aggiungere altri (es add nameserver 8.8.8.8 )

