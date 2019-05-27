#  Cisco Tenta 2

## Del 3

### Chapter 1 - LAN design

### Chapter 2 - Scaling VLAN's

### Chapter 3 - STP

### Chapter 4 - EtherChannel and HSRP

### Chapter 5 - Dynamic routing

### Chapter 6 - EIGRP

### Chapter 7 - EIGRP tuning and troubleshooting

### Chapter 8 - Singelarea OSPF

### Chapter 9 - Multiarea OSPF

### Chapter 10 - OSPF tuning and troubleshooting



## Del 4

### Chapter 1 - WAN concepts

### Chapter 2 - Point-to-point connections

### Chapter 3 - Branch connections

### Chapter 4 - Access control lists (ACL)

### Chapter 5 - Network security and monitoring

### Chapter 6 - Quality of service (QoS)

### Chapter 7 - Network evolution

### Chapter 8 - Network troubleshooting



## Frågor ifrån tentor

1. **What is a drawback of "OSPF multi-access" network? Describe the method for mitigating this issue.** 

   OSPF multi-access använder mycket cpu kraft ifall netverks layouten är stor eller fel. Det kan förebyggas genom att använda EIGRIP.

   

2. **What are two methods to make the OSPF routing protocol more secure?**

   Use SHA or MD5 authetication

   Use the passive-interface command on LAN interfaces that are connected only to end-user devices.

   

3. **What are two features of OSPF "Inter-area route summarization"?**

   Routes within an area are summarized by the ABR.

   ABRs advertise the summarized routes into the backbone.

   

4. **What are the types of OSPF router?**

   Internal routers

   Area bound routers

   Autonomous system boundary routers

   Backbone routers

   

5. **One common tuning method with EIGRP is using Automatic Summarization. Explain how the method works and describe one advantage and one disadvantage**

   Det fungerar så routrarna automatiskt summerar sina routings table till sammma tabell. Så deras routing tables kommer vara identiska. 

   En nackdel är att detta skapar förvirring i nätverket. Då routrarna skickar ut samma information till varandra.

   En fördel är att det använder lite arbetskraft då antalet poster är mindre.

   

6. **What are the main components of PPP?**

   A method for encapsulating multi-protocol datagrams.

   A Link Control Protocol (LCP) for establishing, configuring, and testing the data-link connection.

   A family of Network Control Protocols (NCPs) for establishing and configuring different network-layer protocols.

   

7. **Describe the benefits of VPNs**

   Spara pengar - Det är ett billigt sätt att koppla ihop företaget på. Antingen genom site-to-site vpn för att koppla ihop två locationer/byggnader. Eller för att koppla upp anstälda till nätverket.

   Skalbarhet - Det är lätt att skala. Ansluta fler enheter till nätverket är lätt.

   Kompabilitet - Fungerar för alla enheter. Mobiler, laptops, datorer, routrar.

   Säkert - Det är säkert för det använder kryptering 

   

8. **Describe the operation of the Spanning Tree Algorithm**

   Spanning Tree Algorithm ser till så att det inte sker några loopar i nätverks topologin.

   Lättast förklarat med bild.

   ![Skärmavbild 2019-01-14 kl. 12.05.27](/Users/Marcus/Documents/Skola/Cisco ET1488/Skärmavbild 2019-01-14 kl. 12.05.27.png)

   Om en länk går sönder. Kan den själv dirigera om trafiken. Det som händer är att den blockerade länken öppnas.

   ![Skärmavbild 2019-01-14 kl. 12.05.54](/Users/Marcus/Documents/Skola/Cisco ET1488/Skärmavbild 2019-01-14 kl. 12.05.54.png)

   

9. **Describe the SNMP message types**

   |   Get    | Hämta ett värde ifrån en variable      |
   | :------: | -------------------------------------- |
   | Get-next | Hämta nästa värde i PDU                |
   |   Set    | Spara ett värde i en specifik variable |
   |   Trap   | Genererar alarm                        |

   

10. **Name which devices are responsible to generate the SNMP messages**

  Manages är ansvarig för get, get-next och set meddelanden

  Agent är ansvarig för att generera trap meddelanden

  

    

11. **Explain how MAC database instabillity can occur for Ethernet frames?**

    Det är när kopior av samma frame blir levererad till flera portar på en switch. Det får switches att använda onlödigt mycket resurser. STP förebygger detta problemet.

    

12. **Describe five different WAN access services for private and/or business use**

    Satelit

    Telephone line

    Coaxial cable

    Wireless

    Leased line

    

13. **Describe the purpose of Cisco VTP protocol and the DTP protocol. Also describe one major advantage and one major disadvantage with VTP**

    VTP är ett cisco protokoll och används av cisco switchar. Det gör det simpelt att lägga till nya vlan i nätverket. Tänk ett nätverk med 100 switchar. Då måste man gå till varje switch och manuellt lägga till det nya vlan. Med VTP behöver du bara göra det på en switch. Sedan kommer den att dela informationene till de andra switcharna.

    Dynamic Trunking Protocol (DTP) tillåter portar att automatisk negotiera trunking mellan switcharna.

    En stor fördel som VTP har är att det minska felaktiga konfigurationer.

    VTP 1 och 2 har inte stöd för extended vlan

    

14. **What is the purpose of generating network traffic with SLA**

    Det är för att övervaka nätverket och  testa jitter, latency eller packet loss i nätverket med mera. 

    

15. **Describe how Extended ACLs provide greater degree of control than standard ACLs**

    Standard ACL kan bara filtrera på source address, Extended kan filtrera på source, destination address också protocol och port nummer även filtrera på udp och tcp.

    Standard sätts nära destinationen, extended sätts nära källan.

    

16. **Describe the difference of virtualization with type 1 hypervisors and type 2 hypervisors**

    Hypervisor 1![Skärmavbild 2019-01-16 kl. 09.53.56](/Users/Marcus/Documents/Skola/Cisco ET1488/Skärmavbild 2019-01-16 kl. 09.53.56.png)

    Hypervisor 2 ![Skärmavbild 2019-01-16 kl. 09.54.05](/Users/Marcus/Documents/Skola/Cisco ET1488/Skärmavbild 2019-01-16 kl. 09.54.05.png)

    

17. **Describe how video traffic is affected by poor QoS**

    Utan QoS blir Video kvaliten sämre. Bilden blir blurrig eller i slowmotion. Ljudet kan också bli ur synk med videon. Video trafikär väligt ojämn. Det är asvårt att förutse. Därför behövs bra QoS som kan prioritera video trafiken. 

    

18. **Describe also why congestion occurs in a network**

       

       

Congestion kan uppstå när många enheter komunicerar med tillexempel en router. Det som händer då är att all data ifrån enheterna ska ut på en lina. Då blir det stop. 

Det kan ockås ske när ett stort data paket ska skickas. Då kan de förhinda att små paket skickas inom rimlig tid.



1. What are three features of EIGRP?

   ​	

   * establishes neighbor adjacencies
   * uses the Reliable Transport Protocol
   * Suports equal and unequal cost load balancing 