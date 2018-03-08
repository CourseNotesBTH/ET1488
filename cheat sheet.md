IOS är åtkomligt från antingen __konsolporten__, __SSH__ eller __Telnet__. Vi föredrar att använda __SSH__.

För enkelhetens skull använder vi lösenorden _cisco_ eller _class_. __OBS! Endast under laboration!__

## Tillgängliga kommandon

| Syntax        | Beskrivning                              |
| ------------- | ---------------------------------------- |
| __fetstil__   | Kommandon och nyckelord som ska skrivas in precis som det visas |
| _kursiv stil_ | Argument till vilka värden ska förses    |
| [x]           | Valfritt argument x                      |
| {x}           | Nödvändigt argument x                    |
| [x {y \| z}]  | Nödvändigt argument x som väljs mellan y och z |



| Kommando / beteckning                    | Förklaring                               |
| ---------------------------------------- | ---------------------------------------- |
| _User EXEC Mode_                         | Ett visningsläge med enbart begränsade tillgängliga kommandon. Prompten börjar då med `XXXX>` |
| _Privileged EXEC Mode_                   | Fullständigt privlegium där alla konfigurationskommandon etc. är tillgängliga. Prompten börjar då med `XXXX#` |
| _Interface Mode_                         | Läge för att konfigurera nätverksinterface |
| _Line Mode_                              | Läge för att konfigurera konsol-, Telnet- och SSH-åtkomst |
| __enable__                               | Går från _User EXEC Mode_ till _Privileged EXEC Mode_ |
| __disable__                              | Går från _Privileged EXEC Mode_ till _User EXEC Mode_ |
| __exit__                                 | Går från det nuvarande läget (_Interface Mode_ etc.) till det föregående läget |
| __end__ alt. __^z__                      | Avslutar det globala konfigurationsläget oavsett vilket läge som används för närvarande |
| __configure terminal__                   | Åtkomst till den globala konfigurationen |
| __interface fa0/1__                      | Åtkomst till _Interface Mode_            |
| __description__ {_string_}               | Lägger till en beskrivning till ett interface |
| __ping__ {_ip-address_}                  | Pingar ip-adressen (IPv4 eller IPv6)     |
| __?__                                    | Åtkomst till context-känslig hjälp       |
| __configure__                            | Kan förkortas __conf__ för att det är det enda kommandot som börjar med de bokstäverna. |
| __hostname__ {_name_}                    | Använd den globala konfigurationen och ersätt namnet på _hosten_ |
| __line console 0__                       | Konfigurationsläge för konsolen          |
| __line vty 0 15__                        | Konfigurationsläge för Telnet och SSH (_Virtual Terminal - VTY_). Cisco enheter stöder vanligtvis 16 sådana linor, numrerade 0-15 |
| __password__ {_password_}                | Väljer lösenord för den nuvarande konfigurationen |
| __login__                                | Berätta för enheten till att kräva lösenord |
| __service password-encryption__          | Konfiguration för att använda kryptering på alla lösenord. Använder osäker kryptering, men är mest till för att stå emot _shoulder surfing_ |
| __show running-config__                  | Visar den nuvarande konfigurationen      |
| __show startup-config__                  | Visar konfigurationen som kvarstår på enheten. _running-config_ är enbart den som körs för tillfället och kvarstår inte om den inte sparas |
| __copy running-config startup-config__   | Skriver över den kvarstående konfigurationen med den nuvarande |
| __banner motd__ {_delimiter_} {_message_} | Konfigurerar meddelandet som visar när någon försöker komma åt enheten. Argumentet _delimiter_ kan vara vilket tecken som helst, så länge det inte förekommer i meddelandet _message_ (vanligtvis _#$%^&*_) |
| __enable secret__ {_password_}           | Konfigurerar lösenordet som ska användas för att komma åt den nuvarande konfigurationen |
| __reload__                               | Starta om enheten. Kräver ökade privilegium. Används vanligtvis för att återställa den senast sparade konfigurationen - mata då in __n__ alt. __no__ vid frågan om konfigurationen ska sparas |
| __erase startup-config__                 | Återställ den kvarstående konfigurationen på systemet. Kräver förhöjda privilegium |
| __no shutdown__                          | Starta det nuvarande interfacet (var i interface läge via ex. __interface fa0/0__) |
| __show ip interface brief__              | Visar status av anslutna interfaces. Kräver förhöjda privilegium |
| __ping__ {_ip-address_}                  | Pingar ip-adressen                       |
| __confreg 0x2142__ alt. __confreg 0x2102__ & __reset__ | Återskapa lösenordet                     |
| __no ip domain-lookup__                  | Tillåt inte vissa DNS-lookups            |
| __show version__                         | Visa IOS-version och annan information   |
| __show flash__                           | Visa innehåll i flashet. Används vanligtvis för att kontrollera om något VLAN har skapats på switchen (_vlan.dat_) |
| __delete__ {_file_}                      | Tar bort filen. Används vanligtvis för att ta bort VLANet (__delete vlan.dat__) |
| __show clock__                           | Visa tiden.                              |
| __clock set __ _time_  _month_ _day_  _year_ | Bestäm tiden där _time_ är i formatet hh:mm:ss, _day_ mellan 1-31 och _month_ i formatet _oct_ och _year_ fyrsiffrigt |
| __ip address__ {_ip-address_} {_netmask_} | Sätter ip-adressen statiskt till _ip-address_ och masken till _netmask_ |
| __mdix auto__                            | Slå på auto-läge för MDIX                |
| __show ip arp__                          | Visa ARP-tabellen (vilka IP-adresser som har vilka MAC-adresser) (_arp -a på windows_) |
| __show interface F0/[x{0\|1}]__          | Visa brief om interfacet 1 (_FastEthernet_ mellan switchar). Visar bland annat MAC-adress på switchen |
| __show mac address-table__               | Visa nuvarande kända MAC-adresser. _Fa0/x_ är den nuvarande switchen, _Gi0/x_ står för att porten finns på en annan switch i nätverket |
| __clear mac address-table dynamic__      | Rensa den dynamiska delen av MAC-adresserna |
| __show ip route__                        | Visa routing table                       |
| __show ipv6 route__                      | Läs ovan. Till IPv6                      |
| __clock rate 128000__                    | Konfigurera klockhastighet. Kräver att man är i config-läge för interface Sx/x/x. Om det blir fel, måste den andra änden av kabeln konfigureras. |
| __exec-timeout__ _{n}_                   | Sätter antalet inloggningsförsök för EXEC-läget där _n_ är antalet försök |
| __auto secure__                          | Magi?                                    |
| __show cdp neighbors detail__            | Visar IP-adresser till grannar           |
| __debug ip icmp__                        |                                          |
| __terminal monitor__                     | Låter dig se loggar även om du inte är ansluten via konsolkabel, d.v.s. Telnet och SSH |
| __ip default-gateway__ _{ip}_            | Bestäm default gateway till _ip_ för en switch |
| __show history__                         | Visar kommandohistoriken. Kräver EXEC mode |
| _{command}_ __\|__ _[x{section\|include\|exclude}]_ _{y}_ | Filtrerar. Filtrerar efter en sektion (_section_) som innehåller _y_, eller rader som inkluderar (_include_) _y_ eller rader som inte innehåller (_exclude_) _y_ |
| __logging synchronous__                  | Loggning till konsollen synkroniseras med tangentbordet så det inte kommer i vägen. Bra att ställa in för `line console 0` och `vty 0 15` |
| __ip domain-name__ _name_                | Sätter domännamnet till _name_           |
| __username__ _username_ __privilege__ _x_ __secret__ _password_ | Skapar kontot _username_ med privilegium nivå _v_ (vanligtvis 15) och lösenordet _password_ |
| __transport input ssh__                  | Sätter VTY:n till SSH (istället för telnet) |
| __login local__                          | Tvingar att använda den lokala användardatabasen för att autentisera användaren (läggs till med __username ….__) |
| __crypto key generate rsa modulus__ _x_  | Generera RSA-nycklar på _x_ bitar (Cisco verkar köra på 1024...) |
| __duplex auto__                          | Sätter duplex-läget för interfacet till auto |
| __speed auto__                           | Sätter hastigheten för interfacet till auto |
| __mdix auto__                            | Anpassa automatiskt efter kabeln för interfacet |
| __shutdown__                             | Stäng av interfacet                      |
| __switchport port-security mac-address mac-address…__ | Använd tillåtna statiska MAC-adresser, manuellt |
| __switchport port-security mac-address sticky mac-address__ | Använd dynamiskt lärda MAC-adresser som sparas permanent |
| __switchport mode access__ _[x {access \| trunk}]_ | Väljer läge för porten. _access_ är det vanliga, _trunk_ för en VLAN-trunk |
| __switchport port-security__             | Sätter max tillåtna MAC-adresser som tillåts till 1 och om det överskrids stängs porten av |
| __switchport port-security maximum__ _{x}_ | Antal MAC-adresser som tillåts från porten |
| __switchport port-security violation__   | Ändra vad som händer om säkerhetspolicyn överskrids |
| __switchport port-security mac-address__ _{x}_ | Typ av säkerhetsläge för porten (_sticky_, _dynamic_, _static_) |
| __show port-security interface__ _{interface}_ | Visar en brief om porten (så som max tillåtna MAC-adresser etc.) |
| __show port-security address__           | Visar inlärd MAC-adresser för en specifik port |
| __show vlan brief__                      | En översikt av VLAN-nätverk              |
| __switchport access vlan__ _{id}_        | Tilldela interfacet VLAN _id_            |
| __vlan__ {x}                             | Gå in i konfigurationsläge för VLAN _x_  |
| __no vlan__ _{id}_                       | Ta bort VLAN _id_                        |
| __show vlan name__ _{id}_                | Visa information om VLAN _id_            |
| **login block-for 180 attempts 2 within 30** | Blockera en enhet från att försöka logga in i 180 sekunder om den misslyckas 2 gånger inom 30 sekunder |
| __show ip ssh__                          | Visa SSH-konfiguration                   |
| __ip ssh time-out__ _{x}_                | Sätter timeout för SSH-anslutningen till _x_ (75) sekunder |
| __ip ssh authentication-retries__ _{x}_  | Tillåter max _x_ (2) försök - notera: börjar räkna från 0, d.v.s. 2 innebär tre försök |
| __show ip http server status__           | Visa status för http-server (enbart åtkomligt från VLAN 99 / management) |
| __no ip http server__                    | Stänger av HTTP-varianten för konfigurations-webbplatsen |
| __logging host__ _{ip}_                  | Sätt Syslog-servern till _ip_            |
| __logging trap ?__                       | Visa befintliga Syslog-nivåer            |
| __logging trap__ _{x}_                   | Sätter log-nivån till _x_                |
| __ntp master__ _{x}_                     | Sätter antalet steg från stratum som tillåts |
| __ntp server__ _{ip}_                    | Sätter NTP-server till _ip_ - används för att synkronisera klockan |
| __ntp update-calendar__                  | Uppdaterar från NTP-servern              |
| __ip nat__ _[direction {in\|out}]_       | Sätter riktningen på NAT-en till interfacet |
| __ip nat inside source static__ _{IP 1}_ _{IP 2}_ | Bestämmer vilken intern adress _IP 1_ som ska översättas till den externa adressen _IP 2_ |
| __access-list__ _{x}_ __remark__ _{description}_ | Sätter en beskrivning för ACL:n _x_ (så som 1) |
| __access-list __ _{x}_ __permit__ _{network}_ _{mask}_ | Tillåter nätverk _network_ (nätverksadressen) med nätmasken _mask_ att gå igenom ACL _x_ (så som 1) |
| __access-list__ _{x}_ __deny any__       | Tillåt ingen annan än de tidigare konfigurerade näten att gå igenom filtret |
| __ip access-group__ _{1}_ _[direction{in\|out}]_ | Aktivera ACL:n _x_ (så som 1) på _direction_ (in-/ut-gående) trafik på det nuvarande interfacet |
| __router rip__                           | Aktivera dynamisk routing med RIP-protokollet. Kalla direkt efter __version 2__ för att aktivera den nyare versionen |
| __network__ _{network}_                  | I konfigurationsläget för RIP-protokollet. Lägger till nätverket _network_ (nätverksadress) |
| __ip helper-address__ _{ip}_             | Dirigerar om alla DHCP-förfrågningar till interfacet till _ip_ |
| __ip dhcp exclude-address__ _{ip}_ _[ip2]_ _[ip3]_... | Tar bort adresserna från IP-poolen. Bra för adresser så som routerns och switchens |
| __ip dhcp pool__ _{name}_                | Går in i konfigurationsläge för DHCP     |
| __network__ _{network}_ _{mask}_         | I konfigurationsläget för DHCP. Bestämmer nätverksadressen (_network_) och nätmasken (_mask_) att använda |
| __default-router__ _{ip}_                | I konfigurationsläget för DHCP. Bestämmer default-gateway som ska användas |
| __dns-server__ _{ip}_ _[ip2]_            | I konfigurationsläget för DHCP. Bestämer IP-adresser som ska användas till DNS |
| __domain-name__ _{name}_                 | I konfigurationsläget för DHCP. Tilldelar domännamnet så som CCNA-lab.com |
| __lease__ {x}                            | I konfigurationsläget för DHCP. Delar ut adresser som håller i två dagar. Default är att de håller för evigt |
| __terminal length 0__                    | Sätter terminalens längd till "oändligheten" så att exempelvis`show running-config` matar ut hela konfigurationen utan att skriva ut `- -More- -`. |



| Kortkommandon    | Beskrivning                              |
| ---------------- | ---------------------------------------- |
| __Pil upp__      | Används för att skrolla nedåt i exempelvis kommando-historiken |
| __Pil ned__      | Används för att skrolla uppåt i exempelvis kommando-historiken |
| __Tab__          | Fyller i resten av ett delvis ifyllt kommando |
| __CTRL-A__       | Flytta pekaren till början av raden      |
| __CTRL-E__       | Flytta pekaren till slutet av raden      |
| __CTRL-R__       | Visar raden på nytt                      |
| __CTRL-Z__       | Avslutar konfigurationsläget och går tillbaka till _User EXEC Mode_ |
| __CTRL-C__       | Avslutar konfigurationsläget och avslutar det nuvarande kommandot |
| __CTRL-SHIFT-6__ | Skickar en _interrupt_-signal till det nuvarande kommandot, exempelvis __ping__ |

Filtermöjligheten:

`|` (pipe) kan användas för att filtrera - likt grep. Det går att lägga till antingen `section`, `include` eller `exclude` efter `|` för att filtrera en sektion o.s.v.

## Betydelse av ljussignaler

Det går att felsöka systemet genom att kontrollera LED-lamporna vid portarna:

- Av - ingen länk
- Grönt - länk ansluten
- Blinkande grönt - aktiv data-överförning
- Blinkande grönt och oranget - länk-fel
- Oranget - porten skickar inte data. Vanligt de första 30 sekunderna efter anslutning
- Blinkande oranget - porten är blockad för att stoppa en _switch-loop_

## Grundinställning av switch / router

Anslut till enheten via konsol-kabel.

##### Töm enheten

```
# Höj privilegium
Switch> enable

# Rensa konfigurationen
Switch# erase startup-config

# Se om några VLAN har skapats (vlan.dat)
Switch# show flash

# Ta i sådant fall bort dem
Switch# delete vlan.dat

# Starta om
Switch# reload
```

##### Konfigurera hostname och lösenord

```
# Höj privilegium
Switch> enable

# Gå till global config mode
Switch# configure terminal

# Sätt hostname till S1
Swich(config)# hostname S1

# Lösenordsskydda privileged EXEC mode
S1(config)# enable secret class
```

#####Konfigurera console

```
# Gå till console config mode
S1(config)# line console 0

# Lösenordsskydda åtkomst över konsollen
S1(config-line)# password cisco

# Aktivera synkron loggning
S1(config-line)# logging synchronous

# Aktivera lösenordet
S1(config-line)# login
```

##### Konfigurera VTY (Telnet)

```
# Gå till vty config mode (telnet)
S1(config-line)# line vty 0 15

# Lösenordsskydda åtkomst över vty
S1(config-line)# password cisco

# Aktivera synkron loggning
S1(config-line)# logging synchronous

# Aktivera lösenordet
S1(config-line)# login
```

##### Konfigurera SSH

```
# Gå tillbaka till det globala konfigurationsläget
S1(config-line)# exit

# Bestäm domännamnet för enheten - tvingat
S1(config)# ip domain-name CCNA-lab.com
# Konfigurera inloggning med användare admin och lösenord cisco
S1(config)# username admin privilege 15 secret cisco
S1(config)# line vty 0 4
S1(config-line)# transport input ssh
S1(config-line)# login local
S1(config-line)# exit
S1(config)# ip ssh version 2
S1(config)# crypto key generate rsa modulus 1024
# Tillåt anslutningsförsök i 75 sekunder
S1(config)# ip ssh time-out 75
# Tillåt 2+1 inloggningsförsök innan anslutningen stängs
S1(config)# ip ssh authentication-retries 2
```

##### Konfigurera sensible defaults 

```
# Slå på kryptering av lösenord i sparade konfigurationer
S1(config)# service password-encryption

# Sätt ett meddelande som visas vid åtkomst
S1(config)# banner motd # Unauthorized access is not allowed#

# Om router, tillåt inte DNS
R1(config)# no ip domain-lookup
```

##### Konfigurera anslutning mellan switch och router

```
# Gå till config läge för interfacet vlan1 (Switch) alt. F0/1 (Router) alt. S/1/0
S1(config)# interface vlan1
alt.
R1(config)# interface F0/1

# Sätt en beskrivning
S1(config-if)# description Beskrivning

# Sätt IP-adress och nätmask
S1(config-if)# ip address 192.168.1.2 255.255.255.0
alt.
S1(config-if)# ipv6 address 2001:db8:acad:3::1/64

# Om interfacet är en seriell kabel (router, DCE) välj clock rate
R1(config-if)# clock rate 128000
# Om ett felmeddelande uppstår måste den andra änden konfigureras
R2(config-if)# clock rate 128000

# Aktivera interfacet
S1(config-if)# no shutdown

# Gå tillbaka till det globala konfigurationsläget
S1(config-if)# exit

# Bestäm default gateway för switchar
S1(config)# ip default-gateway 192.168.10.1
```

##### Konfigurera management-VLAN (99)

Notera: endast medlemmar i VLAN 99 kommer åt Telnet och SSH

```
# Skapa management VLAN-et
S1(config)# vlan 99

# Tilldela ett namn
S1(config-vlan)# name Management

# Gå tillbaka till det globala konfigurationsläget
S1(config-vlan)# exit

# Konfigurera management-vlanet
S1(config)# interface vlan 99

# Tilldela ip
S1(config-if)# ip address 172.16.99.11 255.255.255.0

# Aktivera interface
S1(config-if)# no shutdown

# För varje enhet som ska använda VLANet:
# Gå till konfigurationsläge för interfacet med anslutningen
S1(config-if)# interface F0/5
# Aktivera interfacet som access
S1(config-if)# switchport mode access
# Tillåt interfacet att använda VLAN till 99 (management)
S1(config-if)# switchport access vlan 99
```

##### Konfigurera VLAN-trunk (Endast för switchar)

Detta görs för varje interface som ska agera trunk. Det vill säga om två Switchar ska kopplas samman görs detta för båda sidor.

```
# Konfigurera valt interface
S1(config-if)# interface interface_id
# Tvinga länken att vara en VLAN-trunk
S1(config-if)# switchport mode trunk
# Specifiera VLAN för otaggade frames där vlan_id är en id för ett VLAN
S1(config-if)# switchport trunk native vlan vlan_id
# Specifiera tillåtna VLAN för trunk-länken där vlan-list är en eller flera VLAN id
S1(config-if)# switchport trunk allowed vlan vlan-list
```

##### Konfigurera AUTO-MDIX

```
S1(config-if)# interface F0/1
S1(config-if)# duplex auto
S1(config-if)# speed auto
S1(config-if)# mdix auto
S1(config-if)# exit
```

##### Konfigurera loopback-interface (router)

```
R1(config)# interface loopback 0
R1(config-if)# ip address 10.0.0.1 255.255.255.0
R1(config-if)# exit
```

##### Konfigurera routing (RIPv2)

Utfärda `network {ip}` för direkt påkopplade nätverk (vanligtvis F0/0 och S0/1/0) (dess nätverksadress). Detta görs för alla routrar.

```
R1(config)# router rip
R1(config-router)# version 2
R1(config-router)# network 192.168.87.192
R1(config-router)# network 192.168.86.0
R1(config-router)# exit
```

##### Konfigurera DHCPv4 (Router)

På router som agerar DHCPv4-server:

```
# Ta bort ett par addresser från adress-poolen (så som routerns)
R1(config)# ip dhcp excluded-address 192.168.0.1 192.168.0.9
# Konfigurera adresspoolen R1G1 (kan ha annat namn)
R1(config)# ip dhcp pool R1G1
# Berätta för enheter vilket nätverk de är på
R1(dhcp-config)# network 192.168.1.0 255.255.255.0
# Berätta för enheter om default-gateway
R1(dhcp-config)# default-router 192.168.1.1
# Berätta för enheter att använda Googles DNS-servrar
R1(dhcp-config)# dns-server 8.8.8.8 8.8.4.4
R1(dhcp-config)# domain-name ccna-lab.com
# Tilldela IP-adresser i 2 dagar
R1(dhcp-config)# lease 2
R1(dhcp-config)# exit
```

På alla andra routrar:

```
# Vidarebefodra alla DHCPv4-förfrågningar till G0/0 till R1
R2(config)# interface G0/0
R2(config)# ip helper-address 192.168.2.254
```

##### Konfigurera ACL (Router)

```
# Konfigurera beskrivning av ACL 1
R1(config)# access-list 1 remark Description
# Tillåt ett nätverk
R1(config)# access-list 1 permit 192.168.10.0 0.0.0.255
# Neka alla andra
R1(config)# access-list 1 deny any

# Konfigurera interface där ACL:n ska vara aktiv
R1(config)# interface F0/1
# Tilldela ACL:n ingående (in) eller utgående (out)
R1(config-if)# ip access-group 1 {direction}
```

##### Konfigurera NAT (Router)

```
# Översätt adresser från IP1 till IP2
R1(config)# ip nat inside source static IP1 IP2

# Konfigurera vad som är internt (inside) (koppling till switch)
R1(config)# interface F0/1
R1(config-if)# ip nat inside

# Konfigurera vad som är externt (outside) (koppling till ISP)
R1(config-if)# interface S0/1/1
R1(config-if)# ip nat outside
```

##### Konfigurera NTP

För routern som ska agera NTP-server

```
# Bestäm den nuvarande tiden
R1# clock set 9:39:00 05 july 2013

R1# configure terminal
# Konfigurera NTP master (antal steg från stratum som tillåts)
R1(config)# ntp master 5
```

För alla andra routrar:

```
# Använd R1 som NTP-server
R2(config)# ntp server 10.1.1.1
# Uppdatera
R2(config)# ntp update-calendar
```

##### Konfigurera Syslog

```
# Skicka loggningsmeddelande till en syslog-server på IPn
R1(config)# logging host 172.16.2.3

# Visa befintliga nivåer av loggning
R1(config)# logging trap ?
# Konfigurera minsta nivå
R1(config)# logging trap 4
```

##### Konfigurera generell säkerhet

```
# Stäng av alla interface som inte används
S1(config)# interface range F0/1, F0/3 - 4
S1(config-if-range)# shutdown
S1(config)# exit

# Stäng av HTTP-varianten av webbsidan
S1(config)# no ip http server

# Lås MAC-adresser för portar (så som router-switch)
S1(config)# interface F0/5
S1(config-if)# shutdown
S1(config-if)# switchport mode access
S1(config-if)# switchport port-security 
S1(config-if)# switchport port-security mac-address xxxx.xxxx.xxxx
# Bestäm maximalt antal tillåtna (x) mac-adresser innan interfacet stängs ned
S1(config-if)# switchport port-security maximum x
S1(config-if)# no shutdown
```

##### Validera konfiguration

```
# Gå tillbaka till det globala konfigurationsläget
S1(config-if)# exit

# Gå tillbaka till USER MODE
S1(config)# exit

# Validera NIC-konfiguration
S1# show ip interfaces brief

# Validera den nuvarande konfigurationen
S1# show running-config

# Validera VLAN-konfiguration
S1# show vlan brief

# Validera port security för använda interface (ersätt F0/1)
S1# show port-security interface F0/1

# Validera att inlärda MAC-adresser för portar
S1# show port-security address

# Validera vilka MAC-adresser som är anslutna just nu
S1# show mac address-table

# Validera vilka adresser som lärts in via ARP
S1# show ip arp

# Validera SSH-konfiguration
S1# show ip ssh

# Validera utlånade IP-adresser
R1# show ip dhcp binding

# Validera DHCP-adresspool
R1# show ip dhcp pool

# Validera DHCP-statistik
R1# show ip dhcp server statistics

# Validera HTTP(S)-serverkonfiguration
S1# show ip http server status

# Validera ACL:er
R1# show access-lists

# Validera NAT
R1# show ip nat translations

# Validera NTP
R1# show ntp associations

# Skriv över den sparade konfigurationen med den nuvarande
S1# copy running-config startup-config

# Ladda om konfigurationen från den nu sparade
S1# reload
```
