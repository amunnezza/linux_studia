---
created: 2024-04-06T11:43:16 (UTC +02:00)
tags: []
source: https://dnsmonitor.com/knowledge-base/dns-tutorials/dns-tutorial-1-the-basics/
author: Authoritative DNS
---

# DNS Tutorial part 1 - DNS basics – DNS monitor
To build the Internet was quite an achievement by many smart people! There are a lot of of intriguing and interesting stories about how the Internet was developed and how the process of the Domain name system came to be. The history spans over decades before the first functional DNS system saw the light of day at UC Berkeley back in 1984. See the historic link on the [links page](https://dnsmonitor.com/dns-related-links/) for further and more in-depth reading.

In short, the DNS and the domain name system were developed to come to terms with existing and developing problems that might have slowed or halted the development and growth of the Internet. The Domain name system is a set of rules of how the Internet names are hierarchically organised and how they work and interact.  
The DNS is designed with the domain name system in mind. Form the start, the DNS were developed to be both fast and resilient. The architects succeeded with their intentions!

### The Internet domain name space

The _domain name_ is an identification string that defines a realm of administrative autonomy, authority or control within the Internet. A tiny part of the domain name space is illustrated in this picture and has the shape of an upside down tree with the _root domain_ on top. A domain name consist of one or more parts, called labels, delimited by dots, such as **example.com.** 
The hierarchy of domains descends from the right to the left label in the name, each label to the left specifies a subdomain to the domain to the right. The full domain name may not exceed 253 characters in length.
![[domain_name_tree_.webp]]
Below the root domain are the _Top level domains_. They are distinguished into the following six groups:

- Infrastructure top level domains (ARPA)
- Generic top level domains (gTLD)
- Restricted generic top level domains (grTLD)
- Sponsored top level domains (sTLD)
- Country code top level domains (ccTLD)
- Test top level domains (tTLD)

Below the Top level domains are the _2nd level domains_. This is where most domain names are registered.  
Today, [ICANN, the Internet Corporation for Assigned Names and Numbers](https://www.icann.org/), manages the top-level development and architecture of the Internet domain name space. It authorises domain name registrars, through which domain names may be registered and reassigned.

## Domains and zones

Working with DNS, you will come across the notions of _domains_ and _zones_. It might be a bit confusing, since to the naked eye, they appear to be the same. But there are differences:

- A _domain_ defines the whole namespace from a certain point of origin (picture 1 and 2)
- In essence, a _zone_ is a technical and administrative boundary within a _domain_ for which individual DNS servers are responsible (picture 3)
- If there are no _subdomains_ delegated from a _zone_, the _zone_ and the _domain_ is virtually the same (picture 4)
- A _zone_ contains exactly one SOA record describing the general properties of the zone and any number of other DNS records. We will talk more about DNS records later on.
![[1_domain_definition.webp]]

![[2_domain_definition.webp]]
![[3_zone_definition.webp]]

![[4_domain_and_zone_definition.webp]]



## DNS building blocks
The DNS infrastructure is made up of two distinctive entities; _authoritative name servers_ and _iterative resolvers_.

An _authoritative name servers_ hold the data for its assigned domains as well as information about delegated domains or subdomains. The delegation information held by the name servers are imperative for the domain name system to work. An authoritative name server will only respond to queries about its authoritative data.

_Iterative resolvers_ are entities that has no data on its own but are designed to look up the data they're  queried for. The iterative resolvers have only information about where to start its iteration. As a resolver processes queries by iteration it "learns" information to be able to cut corners to speed up the iteration process, this is known as caching.

## Authoritative DNS

An _authoritative DNS_ contain zone files for the domains and zones it is responsible for and replies to queries about those domains.

In order to make the DNS and domain hierarchy work, authoritative DNS servers serving the different domain levels need to have an intimate relationship. This relationship is called _parent_ and _child_, where the _parent_ are the DNS servers delegating the subdomain and the DNS servers receiving the delegation are the _children_. The DNS records that make this possible are called _delegation records_ or _NS records_.

![[auth_dns_1.webp]]
Take note that the NS records in the example above are identical in both parent and child. This is important to assure that the name servers will be reached when resolvers perform their iteration and to avoid unnecessary name lookups. A subdomain should never be delegated to less than two DNS servers to maintain a decent amount of resiliency for the delegated domain.

The domain **example.com** is served by two name servers. These are the only two name servers that hold the authoritative data for that domain. Should both of them fail, no data for the **`example.com`** domain would be available including any delegated subdomains.

## DNS resolver and the iteration process

The counterpart to the authoritative DNS is the iterative resolver. The iterative resolver performs name lookups on requests from its clients using an iteration process which queries the different authoritative name servers.

In order for an iterative resolver to work it needs information about where to start its iteration process. That information is found at the [IANA website](https://www.iana.org/) and is called [Root Hints](https://www.iana.org/domains/root/files) and contains names and IP addresses to all authoritative root name servers.

The iteration for all queries start at the domain root, which is the common denominator of all domain names and DNS records. In the pictures below we have illustrated how a name iteration is performed and how the end result is returned to the client.



![[resolver_1.webp]]
In the picture above we introduce something called a stub resolver. The stub resolver is nothing more than a resolver that lacks the iterative capabilities and can only be configured to know where to direct its queries to. A stub resolver can be found in virtually all Internet aware hosts.

1. The stub resolver queries its configured iterative resolver to find out the IPv4 address to the host **`www.example.com.`**
2. The iterative resolver don't know the answer so it begins an iteration process to find the answer to the query. The iterative resolver query one of the root name servers for the IPv4 address to **`www.example.com.`**
3. The root name server doesn't know the correct answer to this query since it only servers the root zone. What it does is to give a little help on the way. It does know which name servers that are authoritative for the **`.com`** domain. The query reply contains referral records to the authoritative name servers for the **`.com`** domain. This is called a referral response.
4. The iterative resolver repeats the same query but thanks to the referral response i just received it directs the query to one of the authoritative name servers for the **`.com`** domain.
5. The **`.com`** name server, like the root name server in the last query, doesn't know the correct answer either. It does know however, which name servers are authoritative for the **`example.com.`** domain and encloses that knowledge in a referral reply.
6. Once again, the resolver send the same query to the **`example.com.`** name servers.
7. This time around, the **`example.com.`** name servers knows the answer to the query and return a reply with the requested information.
8. The iterative resolver have successfully found the requested reply and return the answer to the stub resolver and closes the iteration process.

## Cache
To increase the speed of the iteration process a resolver will cache each answer and each referral it receives. Instead of repeating the whole process, each resolver will cut corners and use the cached information whenever it gets another query.

In the example illustration above the iterative resolver will cache the referral information as well as the query response. The stub resolver will cache the query response. This caching will result in less DNS queries and improve the overall performance of name lookups. The stub resolver will not ask the iterative resolver again for `**www.example.com**` since it already have the answer in its own cache. All other queries will be sent to the iterative resolver.

Since the iterative resolver now knows which name servers are authoritative for the **`.com`** domain it can go straight to the **`.com`** name servers when receiving a query for another **`.com`** domain like **`acme.com`** If a query for another host record in the **`example.com`** domain would be received it can go straight to the **`example.com`** name servers.

The cached information will remain in cache as long as each individual resource record allows it to. Every DNS resource record set contains a _TTL_, Time To Live, which dictates how long the record is allowed to be cached before it should be discarded.
## DNS resource records
  
The terminology used for DNS resource records (RR) is explained below:

**owner-name           ttl        class   type   type-specific data**  
www.example.com.   14400   IN       A        93.184.216.34

**owner-name**  
Also known as label or left-hand name. The owner-name can't contain members outside the zone.

**ttl**  
Time to live in seconds for this individual record. The TTL sets how long this record may be cached by a resolver.

**class**  
Defines protocol family. The default value is IN. The classes HS, Hesiod and CH, Chaos are both historical MIT protocols and are not used today.

**type**  
Determines the value of the **`type-specific data`** field.

**type-specific data**  
The data content in this field is determined by the **`type`** and **`class`** values.

## Common resource record types

This is an introduction of the most frequently used DNS resource record types you will find in zone files throughout the Internet, including examples of how they look and what they do. If no other RFC is referred to, the resource record types are defined in [RFC 1035](https://tools.ietf.org/html/rfc1035).

**SOA**  
**example.com. 3600 IN SOA sns.dns.icann.org. noc.dns.icann.org. 2018100718 7200 3600 1209600 3600**  
As described earlier every zone file contains exactly one SOA record. SOA is short for Start Of Authority and contains definitions about the zone file itself.  
The type-specific data must have the following fields in this order:

-   Master Name (MNAME). A name server name that is referred to as the Master or data point of origin.
-   Contact information (RNAME). Defines the email address to the responsible person of the zon. The first "." is replaced by the "@" to complete an email address.
-   Serial number. Displays the version of the zone file. Used by slave servers to identify changes in the zone content.
-   Refresh. Modern DNS master servers usually send notify messages when the zone content is updated. If a slave server haven't heard from its master they use this value to decide how often to check for updates.
-   Retry. If a slave server can't reach its master it will use this value as the interval to try the request again.
-   Expire. This timer value is used when a slave server can't reach its master for the duration of the expiry timer. After that the zone content in the slave can no longer count as valid and the slave server will stop responding to queries with its zone data and instead use a SERVFAIL response.
-   DNS NCACHE, Negative cache of DNS queries. This is a TTL value that define how long a NXDOMAIN (non-existent domain) answers should be cached by a resolver. In [RFC 2308](https://tools.ietf.org/html/rfc2308) this field were redefined from its original definition as a TTL for the whole zone.

**NS**  
**example.com. 86400 IN NS a.iana-servers.net.   86400 IN NS b.iana-servers.net.**  
The NS record type defines the authoritative name servers for the domain defined in the owner-name field. There are usually more than one NS record in a zone file. The type-specific data field must contain a host name.

**A**  
**`www.example.com. 86400 IN A 93.184.216.34`**  
IPv4 address record type. The type-specific field contains the IPv4 address for the host name specified in the owner-name field.

**AAAA**  
**`www.example.com. 86400 IN AAAA 2606:2800:220:1:248:1893:25c8:1946`**  
IPv6 address record type. The type-specific field contains the IPv6 address for the host name specified in the owner-name field. The AAAA record type were defined in [RFC 3596](https://tools.ietf.org/html/rfc3596).

**CNAME**  
**`alias.example.com. 86400 IN CNAME www.example.com.`**  
The CNAME rRR type is used for alias of one name to another. This record type should be used when a host need more than one name instead of adding additional A or AAAA records.

**MX**  
**`example.com. 86400 IN MX 10 mail.example.com.   86400 IN MX 20 backup-mail.example.com.`**  
The Mail Exchanger record type routes mail to the domain. The type-specific fields are the preference and the mail host for that preference. The lowest preference value will be the primary mail host.

**TXT**  
**`example.com. 86400 IN TXT "The example domain is used as an example"   example.com. 86400 IN TXT "v=spf1 -all"`**  
The TXT record type was originally intended for human readable text. Since the early 1990's, this record is mostly used by machine-readable data like the Sender Policy Framework and other arbitrary string attributes described in [RFC 1464](https://tools.ietf.org/html/rfc1464).

**SPF**  
**`example.com. 86400 IN SPF "v=spf1 -all"   example.com. 86400 IN TXT "v=spf1 -all"`**  
The SPF record type defines the servers which are authorized to send mail for the domain. Take note of the identical TXT record type! Not all MTA's (Mail Transfer Agents or mail servers) have implemented the SPF record type. The SPF record type were defined in [RFC 4408](https://tools.ietf.org/html/rfc4408).

**SRV**  
**`_sip._tcp.example.com. 86400 IN SRV 10 60 5060 bigbox.example.com.   86400 IN SRV 10 20 5060 smallbox.example.com.`**  
The SRV record type allows for definition of services available in a zone, for example, ldap, http, zip and many more. The type-specific field must contain priority, weight, port and target. The SRV record type were defined in [RFC 2782](https://tools.ietf.org/html/rfc2782).

**PTR**  
**`34.216.184.93.in-addr.arpa. 86400 IN PTR www.example.com.`**  
The pointer record type is used as a reverse mapping of an IP address to its hostname. The PTR record type is used in the **`arpa`** domain.

A complete list of current, experimental and obsolete DNS resource record types can be found on [Wikipedia](https://en.wikipedia.org/wiki/List_of_DNS_record_types). We will introduce additional RR types when we introduce the DNS security extension, DNSSEC later in this tutorial.

## Resource record sets
A _resource record set_ is a grouping of two or more DNS resource records of the same type and with the same owner-name.  
Below are a few examples of DNS resource record sets. You have seen them before in this tutorial but perhaps not reflected about them.

**`example.com. 86400 IN NS a.iana-servers.net.   86400 IN NS b.iana-servers.net.`**

or

**`example.com. 21599 IN MX 10 alt3.aspmx.l.google.com.   example.com. 21599 IN MX 1 aspmx.l.google.com.   example.com. 21599 IN MX 5 alt1.aspmx.l.google.com.   example.com. 21599 IN MX 10 alt4.aspmx.l.google.com.   example.com. 21599 IN MX 5 alt2.aspmx.l.google.com.`**

and

**`_sip._tcp.example.com. 86400 IN SRV 10 60 5060 bigbox.example.com.   86400 IN SRV 10 20 5060 smallbox.example.com.`**
## Authoritative DNS Master & Slave

An established and common way to set up authoritative DNS servers is to configure one server as master and the rest of the servers as slaves. This setup allows for easy administration where the updates to the zone files are performed on the master server which in turn make the new zone file available to the slaves.  
The slave servers picks up the zone files from the master server by zone transfers, either by periodically checking in to the master server using the SOA refresh timer or by way of a notification sent by the master server.  
The DNS servers make no distinction to its zone data whether they are configured as master or slave, The zone data is identical as long as all slave servers are correctly updated.

# DNS Tutorial part 2

## DNS infrastructure

In part one of our DNS tutorial we described how the the domain name space looked and worked. We described how everything is connected with delegation records in parent zones pointing resolvers to their next step on their journey to find the servers authoritative for a specific zone.

In this part we will take a look at the DNS infrastructure, and especially the authoritative DNS where we keep our domains and how they work.

## Terminology

**Master**

The zone content is edited on the Master DNS and is from where the zone content is distributed. A Master, also known as "Primary" can respond to non-recursive DNS queries.

**Slave**

A Slave server holds an exact replica of the Masters zone data. The Slave servers obtain the zone replica by means of zone transfer. Slave Servers are also known by the term "Secondary".

**Stealth**

A stealth server is a DNS Master or Slave server that is not listed in the zones NS or SOA resource records. This way the server will not be found by DNS resolvers and will not receive any queries unless they are artificially directed to the stealth server.

**Notify**

A notify message is sent to the Slave servers as soon as new zone content is available on the Master. This happens when an administrator have updated the zone content, a dynamic record has been updated (this include resource record signatures and public keys for a DNSSEC signed zoned).

**AXFR**

Asynchronous zone transfer is a zone transfer protocol where the full zone content is transfered from a Master to a Slave. A zone transfer is initiated from the Slave servers, usually after receiving a Notify message.

**IXFR**

Incremental zone transfer is a zone transfer protocol where only the updated records are transfered. Otherwise the work identical to an AXFR.

**SOA Serial**

The serial number for the zone is stored in the SOA resource record and is used by the Slave servers to determin if a one transfer is needed or not.

**DNS views**

An "easy" way to separate DNS responses based on query source address. Common examples are Indernal view, DMZ view and External view.

Back when the DNS were created (the good ol' days) the terms "Primary" and "Secondary" were used but were abandoned due to its misleading and misunderstood names. A common misconception was that a "Secondary" DNS server had old data and some people would only query "Primary" DNS servers. "Primary" was replaced by "Master" and "Secondary" were replaced by "Slave" to limit unnecessary confusion. Lately due to political reasons the terms "Primary" and "Secondary" has once again become popular...

## Building DNS infrastructure

DNS infrastructure in its essential parts are very straight forward. We will start with the bare minimum and work our way forward from there. But let's establish a couple of fundamental security guidelines:

- Always, as a security minimum, make sure that traffic from the Internet only are able to reach your DNS servers on application port 53, both over UDP and TCP.
- Always make sure the servers have the correct time, or at least keep the DNS servers on the same time if correct time is unachievable.

We will not go into specific configuration statements for certain types of DNS software but the configuration suggested should be available, one way or the other, from all major DNS vendors.

### Basic DNS setup

This is a basic setup with a Master DNS, from where we edit our zone files, and two Slave DNS servers. The Master and Slave servers are all listed in the NS resource records. The DNS protocol scrambles the order of the DNS servers in every query response which makes sure the query load on each authoritative DNS server is fairly equal.

This is an infrastructure that is quite easy to maintain but has a few drawbacks. The main drawback is that the Master DNS is equally exposed to the Internet as the Slave DNS servers are, and since the Master DNS is the source of origin for our domains we might want to increase security for it a bit.

|                          |                                                                                                                                                                                          |
|:------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| ![[dns_classic-01.webp]] | _Example 1_  <br>**NS RR set:**  <br>example.com.   IN    NS    dns1  <br>example.com.   IN    NS    dns2  <br>example.com.   IN    NS    dns3  <br>   <br>**SOA Master name:** **dns1** |






### Hidden Master

By excluding the Masters name from the NS resource records we create a "Hidden Master" configuration. By placing the Master DNS behind a firewall (illustrated in the picture below by the red dotted line) and set up rules that only allows DNS traffic to the Master from each of it Slaves we increase the security and lower the exposure to the Master.

Note that the Master DNS is still visible in the SOA resource record by the Master Name.
 |

|              Fig. 1              |                                                                        Fig. 2                                                                         |
| :------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------: |
| ![[dns_hidden_master-01-1.webp]] | _Example 2_  <br>**NS RR set:**  <br>example.com.   IN    NS    dns2  <br>example.com.   IN    NS    dns3  <br>   <br>**SOA Master name:** `**dns1**` |

|                                                                                                                                                                                                                                                                                                                                                                          |                                                                                                                                                   |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |:------------------------------------------------------------------------------------------------------------------------------------------------- |
| To completely hide the DNS Master from Internet exposure we will need to replace the SOA Master name with one of the Slave servers, as shown in Example 3.<br>This will hide the Master (who still need a host record) but it will create a new problem that may need to be dealt with: Dynamic DNS update requests. We will circle back to that later in this tutorial. | _Example 3_  <br>**NS RR set:**  <br>example.com. IN    NS    dns2  <br>example.com. IN NS    dns3  <br>   <br>**SOA Master name:** `**dns2**<br> |


## Designs with multiple masters

Multiple Masters are usually implemented to increase resiliency. The downside is that in many circumstances the also add complexity. This can be a tricky situation to solve because when complexity increases usually a degradation of security follows.

Below are a few successful design where multiple masters are used.

### Microsoft AD

As far as Multi-master concepts go the Microsoft AD is by far the most implemented multi master DNS concept out there. Microsoft DNS servers  are rarely seen on the Internet though. Microsoft defaults a DNS server on each Domain Controller (you can opt out if you wish), using AD synchronisation instead of zone transfers to keep every master DNS in sync. As you probably know, edits to any Domain Controller is immediately replicated to all other DC's. Take a note that in a Microsoft DNS implementation there are no real Slave servers.

In most implementations the multiple masters also serve as recursive resolvers.
![[dns_ms-01.webp]]

**NS RR set:**  
`ad.example.com.   IN    NS    dc1  
ad.example.com.   IN    NS    dc2  
ad.example.com.   IN    NS    dc3`  
   
**SOA Master name:** `**dc1/dc2/dc3**` depending on which DNS responding to the query.

### A simple Multi master concept

The easiest approach with a multi master concept is to have two identical master servers which keep in sync by an "out of band" protocol. Most of these instances use a database backend to enable editing on both master servers simultaneously. Both of these servers can be used by the slaves to transfer the zones.
![[dns_multi_master_simple-01.webp]]

**NS RR set:**  
`example.com.   IN    NS    dns2  
example.com.   IN    NS    dns3`  
   
**SOA Master name:** `**dns0/dns1**` depending on setup.

# A more complex Multi master concept

The DNS community have always recommended to distribute public name servers across multiple AS (Autonomous Systems). When outsourcing the DNS service, chance are that the service provider only reside inside a single AS why it has become prudent to use two or more DNS service providers. Since a service provider provide its own master accompanied by  its own slaves, you will end up with a multi master/multi slave infrastructure. In this type of setup, the different master/slave infrastructures operate independent of each other and provide a high degree of availability but with an increased complexity keeping the different infrastructures in sync.

Since the two (or more) infrastructures operates independently, the SOA serial numbers will probably differ between the infrastructures.


![[dns_multi_master_complex-01-1.webp]]


**NS RR set:**  
`example.com.   IN    NS    dns1  
example.com.   IN    NS    dns2  
example.com.   IN    NS    dns3  
example.com.   IN    NS    dns5  
example.com.   IN    NS    dns6`  
   
**SOA Master name (A):** _**dns0**_ 
**SOA Master name** **(B):** _**dns4**_.


