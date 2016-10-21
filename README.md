# Projekt
Ročníkový projekt IT4 2016

IPv4 + IPv6 security

Multi area ospf
ospfv3 + security

manualove stranky

Projekt bude zpracován v následujících 3 měsících. V zásadě jde o to dozvědět se více o zabezpečení daných sítí,
a jak fungují. První měsíc během učení na CCNA 2 budou zpracovány první 2 části, což je bezpečnost IPv4 a IPv6. V říjnu
budu pracovat na Multi area ospf a ospfv3 + security. V listopadu začnu s prezentací a pokud zbyde čas, tak vytvořím i
manuálové stránky.

Intermediate System to Intermediate System(IS-IS)

Popis:
IS-IS je IGP směrovací protocol sloužící pro výměnu směrovacích informací v rámci administrativní domény nebo sítě.
IS-IS je protokol pro výměnu směrovacích informací založený na stavu linek, který informace o stavu linek šíří v síti
routerů spolehlivě záplavovým způsobem. Každý IS-IS router si nezávisle vytváří informace o topologii sítě na základě
shromažďování informací z ostatních routeru. Stejně jako protokol OSPF používá IS-IS algoritmus pro výpočet
nejlepší cesty sítí. Router pak používá získané informace pro směrování paketů nebo datagramů po vypočítané ideální cestě
sítí k cílovému uzlu.IS-IS bývá označován za standard sítě velkých poskytovatelů Internetu.

Historie:
Protokol IS-IS vyvinula firma Digital Equipment Corporation pro rodinu protokolů DECnet Fáze V. V roce 1992 byl
standardizován Mezinárodní organizací pro normalizaci jako ISO 10589 pro komunikaci mezi síťovými zařízeními označovanými v
terminologii ISO jako Intermediate Systems (jako protiklad ke koncovým neboli hostitelským systémům). Účelem IS-IS bylo
umožnit směrování datagramů OSI protokolu CLNS. IS-IS byl vyvíjen přibližně ve stejné době, kdy Internet Engineering Task
Force (IETF) vytvářel podobný protokol nazývaný OSPF.
Později byl IS-IS rozšířen pro směrování datagramů v Internet Protocol (IP), protokol síťové vrstvy sítě Internet.

Porovnání s OSPF:
Zatím co OSPF komunikuje s síťovou vrstvou, tak IS-IS komunikuje s linkovou vrstvou.
IS-IS se od OSPF odlišuje způsobem definování oblastí i směrováním mezi nimi. 
IS-IS rozlišuje dvě úrovně routerů:

routery úrovně 1 (anglicky Level 1), které pracují v rámci oblasti (anglicky intra-area);
routery úrovně 2 (anglicky Level 2) pracují mezi oblastmi (anglicky inter-area);
routery úrovně 1-2 (anglicky Level 1-2), které pracují v rámci oblasti i mezi oblastmi.

Routery úrovně 2 směrují pakety mezi oblastmi a mohou vytvářet relace pouze s jinými routeri úrovně 2. Routery úrovně
1 si vyměňují směrovací informace pouze mezi sebou. Obdobně routery úrovně 2 si vyměňují informace pouze s jinými
routery úrovně 2. Routery úrovně 1-2 si vyměňují informace s oběma úrovněmi a používají se pro propojení routerů
úrovně 1 s routery úrovně 2.

Oblasti v OSPF jsou vymezeny na rozhraních tak, že hraniční router oblasti (anglicky area border router, ABR) patří do
dvou nebo více oblastí současně, takže hranice mezi oblastmi tvoří routery ABR; v IS-IS jsou hranice oblastí v mezi
routery úrovně 2 nebo úrovně 1-2, takže každý IS-IS router patří pouze do jediné oblasti.

IS-IS nevyžaduje, aby Area 0 (oblast nula) byla páteřní oblastí, kterou musí procházet veškerý provoz mezi oblastmi.
Logický pohled je, že OSPF vytváří strukturu podobnou pavučině nebo hvězdicové topologii, ve které jsou všechny oblasti
připojené přímo na oblast 0, zatímco IS-IS vytváří logickou topologii s páteřní sítí tvořenou routeri úrovně 2, a větvemi
routerů úrovně 1-2 a úrovně 1, které tvoří jednotlivé oblasti.

IS-IS se od OSPF odlišuje také metodou, jak v síti rozšiřuje spolehlivě informace o topologii a jejích změnách. Základní
koncepty jsou však podobné.

OSPF má větší sadu rozšíření a nepovinných vlastností zadaný v protokol Standardy. IS-IS je však snáze rozšiřitelný: jeho
používání type-length-value parametrů umožňuje implementovat podporu pro nové techniky bez změn protokolu. Například pro
podporu IPv6 byl protokol IS-IS pouze rozšířen o několik nových TLV, zatímco pro OSPF bylo nutné vydat nový protokol draft
(OSPFv3). Kromě toho je IS-IS méně „upovídaný“ a lépe se škáluje, takže může podporovat větší sítě. Při použití stejné
množiny prostředků může IS-IS podporovat více routerů v oblasti než OSPF. To přispělo k používání protokolu IS-IS jako
protokolu pro poskytovatele Internetu.

Routing Information Protocol(RIP)

popis:
RIP je směrovací protokol typu distance-vector (vektor vzdálenosti) využívající Bellmanův-Fordův algoritmus pro určení nejkratší cesty v síti. Metrikou směrování je počet skoků k cílové síti (hop count). Jako ochrana proti směrovacím smyčkám je implementovaný omezený počet směrovačů (hopů) v cestě k cíli, maximální možný počet hopů je 15. Tento limit ovšem také omezuje velikost sítí ve kterých lze RIP použít (16 hopů je bráno jako nekonečná vzdálenost a používá se k označení nepřístupných, nepoužitelných směrovacích tras).
Původně každý router s RIP vysílal aktualizované směrovací tabulky v intervalu 30 sekund. To z počátku nepředstavovalo žádný problém, jelikož směrovací tabulky nebyly tak rozsáhlé, aby se to nějak výrazněji projevilo na síťovém provozu. Vzhledem k růstu sítí (a tudíž i směrovacích tabulek) se ale toto řešení ukázalo jako nevhodné, jelikož každých 30 sekund by byla síť zahlcena velkým množstvím dat. Moderní implementace RIP toto řeší pomocí různých metod nastavujících časové intervaly každého routeru zvlášť, aby byla data rozprostřena v čase, a nedocházelo nárazově k velkým tokům dat.
V dnešních sítích se již RIP nepovažuje za dobrou volbu, jelikož čas potřebný ke konvergenci, či rozšiřitelnost, zaostávají za ostatními protokoly jako EIGRP, OSPF, nebo IS-IS. Navíc (bez použití RIP-MTI algoritmu) je kvůli omezenému počtu hopů velmi omezená velikost sítě ve které lze RIP nasadit. Naproti tomu je ale RIP snáze konfigurovatelný než ostatní protokoly.

RIP používá User Datagram Protocol (UDP) jako jeho transportním protokolem, a je přiřazena rezervovaný číslo portu 520.
Počet hop nemůže překročit 15 nebo trasy bude vynechána.Aktualizuje se každých 30 sekund.RIPv1 používá broadcast a RIPv2 multicast.

------------------------------------------------------rip to ospf---------------------------------------------------------------

http://www.samuraj-cz.com/clanek/cisco-routing-4-is-is-intermediate-system-to-intermediate-system/
http://www.routeralley.com/guides/rip.pdf
https://en.wikipedia.org/wiki/Routing_Information_Protocol
http://www.cisco.com/c/en/us/td/docs/ios/12_2/ip/configuration/guide/fipr_c/1cfrip.pdf
https://www.nada.kth.se/kurser/kth/2D1490/04/lectures/rip.pdf
http://docwiki.cisco.com/wiki/Routing_Information_Protocol
http://www.cs.cmu.edu/~./tungfai/Documents/PacketSwitching/SRIP.pdf
http://nptel.ac.in/courses/106105080/pdf/M7L2.pdf
http://web.cecs.pdx.edu/~jrb/routing/lectures/pdfs/RIP.pdf

--------------------------------------------------------------------------------------------------------------------------------

EIGRP - Enhanced Interior Gateway Routing Protocol
Vlastnosti EIGRP
proprietálním Cisco protokol, rozšíření staršího IGRP, jedná se o rozšířený (Advanced) Distance-Vector Routing Protocol, obsahuje i některé vlastnosti z link-state routing protokolu
používá DUAL algoritmus - Diffusing Update based algorithm
proti IGRP - rychlejší konvergence, větší rozšiřitelnost, smyčky jsou téměř vyloučeny (díky DUAL algoritmu) - zasílá pouze změny, neperiodicky
jedná se o classless protokol, používá CIDR a VLSM (variable length subnet masks) - jako masku zasílá délku prefixu pro každý cílový subnet
sestavuje vztahy se sousedy zvané sousedství (adjacency), sousedy objevuje pomocí Hello paketů, které se zasílají každých 5s na rychlých a 60s na pomalých linkách
aby dva routery mohly být sousedy, tak musí být členy stejného AS (Autonomous system) a mít stejné K values (konstanty pro výpočet metriky), také stejná verze EIGRP (zatím se nepoužívá), interface na stejném subnetu, stejný MD5 hash
defaultně používá autosumarizaci přes classful hranice - zajišťuje, aby routovací tabulky byly co nejvíce kompaktní, můžeme vypnout no auto-summary, to je třeba v případě, kdy máme nespojitý adresní prostor (při sumarizaci by se zahrnuly i adresy, které jsou mimo naši síť)
můžeme použít manuální sumarizaci per interface, jako cíl (destination) se nastaví Null0
podporuje IP, IPv6, IPX, AppleTalk
maximálně zabere (v defaultním nastavení) 50% propustnosti interfacu (údaj získává z bandwidth)
metrika je pomocí 32 bitových hodnot, většinou se používá pouze šířka pásma a delay
metric = ([(K1 * bandwidth) + [(K2 * bandwidth) ÷ (256 - load)] + (K3 * delay)] * [K5 ÷ (reliability + K4)]) * 256 = cca = (bandwith + delay) * 256
pokud router nemá žádný feasible successor, tak se přepne do aktivního stavu a dotáže se sousedů
Stuck In Active (SIA) - stav, kdy je cesta v aktivním stavu, router odešle Query a v určitém stavu neobdrží odpověď, v tom případě EIGRP vyřadí tyto sousedy
routovací tabulky (update směrovací informace) se předávají pomocí multicastu na 224.0.0.10, pokud je to možné, jinak se použije unicast (opakování nepotvrzeného updatu, rozhranní bez podpory multicastu, ručně zadaní sousedé)
nestejnoměrné vyvažování zátěže (unequal cost path load balancing) - používá proměnnou variance, standardně se zvolí cesta s nejmenší metrikou (FD), pokud je takových cest více (mají stejné FD), tak se použije stejnoměrné rozvažování; pokud zadáme variance, tak se použijí všechny cesty, které mají metriku menší než variance*minimální metrika do cíle (metrika <= variance*FD). Použijí se ale pouze cesty, které jsou feasible successor, tedy pro které platí RD<FD (=cesta od souseda do cíle je menší než nejkratší cesta).

Základní termíny EIGRP
Successor - primární routa k cíli, ukládá se do routovací tabulky, může být více succesorů ke stejnému cíli
Feasible Successor - záložní cesta (backup route), ukládá se do tabulky topologie, může být více feasible succesorů ke stejnému cíli, její RD je menší než FD současné nejlepší cesty
Reported Distance (RD) - nebo také Advertised Distance (AD), je nejnižší celková metrika (vzdálenost) podél cesty do cílové sítě (přes succesory) zaslaná sousedem
Feasible Distance (FD) - je RD + cena k dosažení souseda, který zaslal RD
Feasibility Condition (FC) - je dostačující podmínka k dosažení sítě bez smyček, používá se při volbě succesora a feasible succesora, říká, že pokud je RD je vetsi nez FD pro určitý cíl, tak leží na cestě bez smyček

Pakety posílané v EIGRP
Hello - multicast, zasílání nespolehlivě (nevyžaduje potvrzování), objevování sousedů (discover), identifikace nefunkčních routerů, posílá (interval) se každých 5s na rychlých linkách nebo každých 60s, hold time pro hello paket je 3 x hello interval
Acknowledgement - unicast, nespolehlivě, hello bez dat s číslem potvrzení
Query - multicast, doručování spolehlivě, zasílá se při přepnutí do aktivního stavu
Reply - unicast, doručování spolehlivě, odpověď na query
Update - multicast, doručování spolehlivě (reliably), zprostředkovává dostupnost, soused si pomocí nich sestaví topology table

Tabulky pro EIGRP
routovací (routing) - nejlepší routy do destinací
topologie (topology) - routovací záznamy do všech destinací
sousedé (neighbors) - informace o sousedních routerech (adjacent)

používá se pro topologii Hub and Spoke (model kola - střed kola a paprsky, obdoba topologie hvězda)
jako stub se konfigurují pouze remote routers (spoke)
jako sousedi stub routeru by měli být pouze EIGRP hub routers (distribution)
snižuje využití zdrojů, zvyšuje síťovou stabilitu a zjednodušuje konfiguraci stub routeru
Stub router směruje pakety pouze do sítě, kterou explicitně zveřejnil, proto mu Hub router neposílá Query
stub router oznamuje (advertised) pouze summary a connected routes
neptáme se stub routeru na jich routy

EIGRP History

Before EIGRP hit our scenes we had IGRP, Interior Gatway Routing Protocol.Cisco developed IGRP in the mid-1980s as an answer to the limitations of RIP, the most significant of which are the hop count metric and the 15-hop network size. IGRP calculated a composite metric from a variety of route variables and provided “knobs” for weighting the variables to reflect the specific characteristics and needs of the network. Although hop count is not one of these variables, IGRP did track hop count, and could be implemented on networks of up to 255 hops in diameter.

Advantages that IGRP presented over RIP;

Unequal-cost load sharing
An update period three times longer than RIP’s
A more efficient update packet format

dalsi informace - dale roztridit
Key capabilities that distinguish EIGRP from other routing protocols include fast convergence, support for variable-length subnet mask, support for partial updates, and support for multiple network layer protocols.
A router running EIGRP stores all its neighbors routing tables so that it can quickly adapt to alternate routes. If no appropriate route exists, EIGRP queries its neighbors to discover an alternate route. These queries propagate until an alternate route is found.
Its support for variable-length subnet masks permits routes to be automatically summarized on a network number boundary. In addition, EIGRP can be configured to summarize on any bit boundary at any interface.
EIGRP does not make periodic updates. Instead, it sends partial updates only when the metric for a route changes. Propagation of partial updates is automatically bounded so that only those routers that need the information are updated. As a result of these two capabilities, EIGRP consumes significantly less bandwidth than IGRP.
EIGRP includes support for AppleTalk, IP, and Novell NetWare. The AppleTalk implementation redistributes routes learned from the Routing Table Maintenance Protocol (RTMP). The IP implementation redistributes routes learned from OSPF, Routing Information Protocol (RIP), Intermediate System-to-Intermediate System (IS-IS), Exterior Gateway Protocol (EGP), or Border Gateway Protocol (BGP). The Novell implementation redistributes routes learned from Novell RIP or Service Advertisement Protocol (SAP).

http://www.samuraj-cz.com/clanek/cisco-routing-2-eigrp-enhanced-interior-gateway-routing-protocol/ cz
http://ericleahy.com/index.php/eigrp-part-one/ en
http://docwiki.cisco.com/wiki/Enhanced_Interior_Gateway_Routing_Protocol en

--------------------------------------------------------------------------------------------------------------------------------

OSPF 


zdroje:
http://www.cisco.com/en/US/products/ps6599/products_white_paper09186a00800a3e6f.shtml
https://cs.wikipedia.org/wiki/Intermediate_System_to_Intermediate_System
http://www.ciscopress.com/articles/article.asp?p=26850
http://www.samuraj-cz.com/clanek/cisco-routing-4-is-is-intermediate-system-to-intermediate-system/
http://wh.cs.vsb.cz/mil051/index.php/Sm%C4%9Brovac%C3%AD_protokol_IS-IS_(Intermediate_System-t
-Intermediate_System_Protocol)
https://cs.wikipedia.org/wiki/Interior_gateway_protocol
https://cs.wikipedia.org/wiki/DECnet
http://www.slideshare.net/shaileshpachori/master-all-home

RIP, OSPF, OLSRD, EIGRP

