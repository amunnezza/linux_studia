
(kali㉿kali)-[~/Documents]
└─*$ sudo nl    /etc/snort/snort.conf | grep output* 
    33  #  6) Configure output plugins
   445  # Step #6: Configure output plugins
   450  # output unified2: filename merged.log, limit 128, nostamp, mpls_event_types, vlan_event_types
   451  output unified2: filename snort.log, limit 128, nostamp, mpls_event_types, vlan_event_types
   453  # output alert_unified2: filename snort.alert, limit 128, nostamp
   454  # output log_unified2: filename snort.log, limit 128, nostamp 
   456  # output alert_syslog: LOG_AUTH LOG_ALERT
   458  # output log_tcpdump: tcpdump.log
