### Skillnader i throughput

* Mängden trafik som går genom nätverket kan påverka
* Typen av trafik som går genom nätverket
* Fördröjningar beroende på antal enheter trafiken ska gå genom

### Topologier

![Topologi](https://www.ccna7.com/wp-content/uploads/2015/08/i274590v1n1_274590-1.png)

Om A ska skicka ett IP-paket till B används BB:BB:BB:BB:BB:BB som mottagare i paketet som skickas från A. Alltså default gateway.

![Topologi](https://lh3.googleusercontent.com/-wZpSomhBlVY/UvwMKzymWWI/AAAAAAAAAk4/ht_TFhdp2uA/w667-h317-no/25-final-ccna2.png)

Här används en `outbound` acl på `R1 G0/1.2*` för att blockera VLAN 20 att komma åt skrivaren P1. Man använder alltså den routern som är närmst mottagaren (skrivaren) på den sida som är närmst avsändaren (VLAN 20) för att blockera.

### Epost

De vanligaste protokollen är IMAP, SMTP, POP3

### DHCP - Dynamic Host Configuration Protocol

Ger möjlighet att ge datorer nätverksinformation och tilldela IP-adresser dynamiskt. 

1. Dator: DHCP Discover (Broadcast) - "Jag skulle vilja ha en adress"
2. Server: DHCP Offer (Unicast) - "Jag är en DHCP-server, här är adressen jag kan ge dig, domännamn du ska använda och hur länge du får använda adressen"
3. Dator: DHCP Request (Broadcast) - "Jag accepterar adressen"
4. Server: DHCP Ack (Unicast) - "Jag förstår att du accepterar adressen"

DHCP-protokollet för datorn använder UDP på source-port 68 och destination-port 67. Om det skickas från servern används UDP source-port 67 och destination-port 68.

### DNS - Domain Name System

Översätter en address så som www.google.com till en IP-adress. För att se vilken IP-adress som tillhör domännamnet kan kommandot `nslookup` användas.

### NAT - Network Address Translation

Gör det möjligt att ansluta många datorer till en internetanslutning med en eller flera IP-adresser. NAT kan användas så att varje intern IP-adress motsvarar en extern IP-adress i den mån det är möjligt. NAT används vanligtvis mellan privata nät och internet.

NAT64 är ett sätt att översätta IPv4-trafik till IPv6.

### PAT - Port Address Translation

Gör det möjligt att ansluta många datorer till en internetanslutning med en IP-adress. PAT används genom att översätta paket från det interna nätverket till exempelvis Internet. På vägen översätts avsändarens IP-adress till routerns. En specifik port tilldelas så att routern kan hålla koll på vilken ursprunglig avsändare som bör mottaga ett paket när det väl når routern från Internet.

### ARP - Address Resolution Protocol

ARP är ett kommunikationsprotoll som kopplar samman en IP-adress med en MAC-adress. ARP är en förbindelse mellan lager 3 (nätverk) och lager 2 (datalänk).

För kommunikation i lager 2 (datalänk) är alla noder åtkomliga genom MAC-adresser. För att kunna använda logiska (IP-) adresser i nätverkslagret (lager 3) så översätts IP-adresser till MAC-adresser och skickas vidare nedåt mot lager 2 (datalänk).

En ARP-förfrågan frågar nätverket "Vem har IP-adressen x.x.x.x?" genom en broadcast på lager 2 (datalänk) med den egna nodens MAC-adress som avsändare och FF:FF:FF:FF:FF:FF (broadcast). Meddelandet når alla enheter och den som har IP-adressen x.x.x.x svarar med en unicast tillbaka till den ursprungliga avsändaren.

Alla sådana förfrågningar läggs till i en tabell.

Om en router tar mot en ARP-förfrågan och inser att hosten ligger i ett annat nätverk så svarar routern med sin egen MAC-adress.

### LLC - Logical Link Control

Arbetar på lager 2 - datalänklagret. Lagret fungerar som felrättning och länkkontroll.

### MAC - Media Access Control

Arbetar på lager 2 - datalänklagret. Lagret styr hur nätverksnoder får åtkomst till OSI-modellens fysiska (media-) skikt. 

Alla nätverksinterface har en unik adress - en MAC-adress. MAC-adressen används vid kommunikaton inom nätverket och sägs tillhöra lager 2 - datalänklagret. Mac lägger till en header och trailer för att skapa en lager 2 PDU.



Adressen kan användas för filtrering av enheter på en switch för att blockera vissa enheter eller att låsa en port för en specifik enhet.

En MAC-adress som börjar med `01-00-5E` är en multicast

### Ethernet

Ethernet arbetar i datalänk-lagret (lager 2) och det fysiska lagret (lager 1). Ethernet förlitar sig på LLC och MAC. MAC tar hand om att kapsla in datan. Kapsuleringen bygger upp framen med adressering och feldektetering. LLC tar hand om flödeskontroll.

STP (Spanning tree protocol) används för att inte loopar ska bildas i nätverket även om bryggade nätverk har loopar. Tillåter även redundanta bryggor. Protokollet ser till att det endast finns en väg mellan två noder. STP jobbar på lager 2 (datalänk).

### ACL - Access Control List

En ACL kan användas för att reglera vilka hosts eller nätverk som ska kunna tillåtas eller nekas använda tjänsten. Arbetar på lager 3 - nätverkslagret. 

### OSI - nätverkslagret

* Routar paket till destinationen
* Enkapsulerar PDUs (Packet Data Unit) från transportlagret

### IP

IP ligger på OSI lager 3 - nätverkslagret.

* 192.168.0.0/16 är reserverat för privat bruk
* 10.0.0.0/8 är reserverat för privat bruk
* 172.16.0.0/12 är reserverat för privat bruk
* FE80::/10 är en range av link-local-adresser som kan tilldelas interface
* IPv6 använder link-local-adressen av grannar som next-hop för dynamisk routing

För att konfigurera en statisk IPv6 routing som enbart refererar nätverk mellan `2001:db8:cafe::/58` och `2001:db8:cafe:c0::/58` kan `ipv6 route 2001:db8:cafe::/56 S0/0/0`  användas.

##### IPv6

`2001:DB8::BAF:3F57:FE94` är en global unicast

`FF02::1` är en all node unicast

`::1` är en loopback

`FF02::1:FFAE:F85F` är en solicited node multicast

`::/0` används när en statisk route konfigureras

SLAC är ett alternativ till DHCPv6

`2001:0DB8:0000:1470:0000:0000:0000:0200` kan förkortas `2001:DB8:0:1470::200` d.v.s inledande nollor skippas. Man kan använda `::` för att fylla ut nollor så lång det går, men bara en gång per adress. Den andra gången måste exempelvis `:0:` användas.

IPv4 kan skickas genom IPv6 genom tunneling. IPv6 kan kommunicera med IPv4 via översättning (translation). IPv4 och IPv6 kan finnas på samma nätverk via dual stack.

##### IPv4

`169.254.1.5` är en link-local-adress

`198.133.219.2` är en public adress

`198.133.219.2` är en experimentiell adress

`127.0.0.1` är en loopback-adress

### Routing

* Vid link-state routing används kostnaden av länken, typ av länk och router interface IP-adress och nätmask
* Link-state routing medför att routrar kan skicka ut uppdateringar vid föränding och att de kan skapa en topologi av nätverket

### Troubleshooting

* Kan man pinga en IP-adress men inte dess domännamn används nslookup för att se om man kan använda DNS

![Topologi](https://ccnav6.com/wp-content/uploads/2017/07/i215789v1n3_Item-215789.jpg)

PC1 kan inte få en IPv4-address. Detta då kommandot `ip helper-address` kallades på fel interface (borde varit G0/0)

### CLIn

```
D   172.16.0.0/22 [90/2172416] via 172.16.4.1, 00:13:47, Serial0/0/1
C   172.16.4.0/30 is directly connected, Serial0/0/1
C   172.16.4.64/26 is directly connected, FastEthernet0/0
D   172.16.100.0/30 [90/2681856] via 172.16.4.1, 00:13:47, Serial0/0/1
D   172.16.100.64/26 [90/2684416] via 172.16.4.1, 00:13:47, Serial0/0/1
D*  0.0.0.0/0 [90/7801856] via 172.16.4.1, 00:13:47, Serial0/0/1
```

Denna utmatning visar att en annan router i samma orginisation gav default route genom att använda ett dynamiskt routing-protokoll

### NAT

* Ett problem med NAT är att det inte finns någon end-to-end-adress

### OSI

![OSI](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/OSI_Model_v1.svg/langsv-476px-OSI_Model_v1.svg.png)

| Lager | Namn         | Beskrivning                              |
| :---- | ------------ | ---------------------------------------- |
| 1     | Fysiskt      | Den fysiska länken - fiberoptik, elektrisk kabel, trådlös. Ethernet, RJ45 o.s.v. |
| 2     | Datalänk     | Node-to-node data-transfer. MAC kontrollerar hur enheter får skicka data. Logical link control (LLC) enkapsulerar nätverksprotokoll. LLC sköter även felkontroll och frame-synkronisering. LLC sköter också identifieringen av vilket nätverkslager-protokoll som ska användas. PPP (point-to-point protocol), Frame Relay. Här kapsuleras den fysiska adressen. Skickar Maximum Transmission Unit (MTUn) till lager 3 |
| 3     | Nätverk      | Sköter överförning av data av en variabel längd (datagram) från en nod till en annan. Sköter packet forwarding och routing till närliggande routrar. Här ligger IP (logisk addressering). Här kapsuleras IP-adressen |
| 4     | Transport    | Sköter host-to-host-kommunikation. Hanterar flow-control, multiplexing, segmentering och pålitlighet. Här ligger TCP och UDP (sändning, mottagning och ankomstkontroll). Här kapsuleras port-adressen |
| 5     | Session      | Sköter anslutning och bortkoppling mellan datorer. Full-duplex, half-duplex och simplex. Hjälper TCP med session-kontroll |
| 6     | Presentation | Översätter data mellan olika nätverksformat så att en applikation kan tolka den. XML, ASCII, JPEG o.s.v. Kryptering/dekryptering |
| 7     | Applikation  | Närmst användaren. HTTP, SNPM, Telnet    |

### TCP - Transmission Control Protocol

Ligger på lager 4 - transport. TCP sköter kontroll av segment av data för att se till att de kommer fram. 

TCP tar mot en ström av data, delar upp den i delar och lägger till TCP-headern för att skapa ett TCP-segment. TCP-segmentet kapsuleras in i ett IP-datagram och skickas vidare.

* TCP är pålitligt och ingen tanke behövs lägga på huruvida ett paket kommer fram eller ej
* TCP är connection-oriented. En anslutning måste upprättas innan överförning av data
* TCP är stream-baserat. Data skickas från en applikation utan en struktur
* Varje TCP-paket som tas mot tillkännages av mottagaren så att avsändaren vet att det kom fram
* Varje paket skickas i en sekvens. Kommer ett paket bort frågar mottagaren efter paketet och avsändaren skickar om paketet - ingen data kommer bort
* Flow-control används genom att storleken på paketet som skickas justeras efter hur snabbt mottagaren kan ta mot paket. Om paket plötsligt börjar tappas halvvägs så sänks storleken och hastigheten
* En låg overhead
* Snabb överförning
* Kan skicka små till stora paket (flera gigabytes)
* Används då överförning av data måste vara pålitlig - så som HTTP, FTP, DNS, SMTP, POP, IMAP etc.

Window size refererar till mängden data som kan skickas innan en ACK krävs.

##### TCP/IP



### UDP - User Datagram Protocol

Ligger på lager 4 - transport. UDP utför ingen kontroll för att se om data har tagits mot men är snabbare än TCP.

UDP använder en enkel anslutningslös kommunikation med minimalt av protokoll. UDP använder checksums för kontroll av integritet men har ingen handskakningsprocedur som TCP.

* UDP är ett enkelt protokoll med hög hastighet som tillåter applikationer att skicka data, men inte mycket mer
* UDP använder ingen anslutning utan skickar data även om ingen lyssnar
* UDP är meddelandebasserat - data skickas i paket av applikationen
* UDP är ett s.k. best-effort-protokoll där data skickas i den mån det är möjligt. Mottagaren tillkännager inte mottagna paket.
* Om data tappas bort vet UDP inte om det och skickar därför inte om datan
* Ingen flow-control uträttas
* UDP har en väldigt liten overhead
* UDP kan skicka data väldigt snabbt
* UDP klarar av små till något större paket (några hundra megabytes)
* Används av applikationer där överförningshastighet är viktigare än fullständighet av datan och där datan som skickas är liten eller där multicast/broadcast används
* Används till DNS, HCP, TFTP, RIP etc.

### PPP (point-to-point protocol)

PPP arbetar på datalänk-lagret (lager 2) och används för att skapa en direkt anslutning mellan två noder utan någon anslutning till en switch eller router som mellanhand. PPP erbjuder autentisering, krypterad överförning och komprimering.



