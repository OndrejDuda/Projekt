Směrovací informační protokol (RIP)

Historie
Směrovací informační protokol neboli RIP, jak bývá často nazýván, je jedním z nejdéle používaných směrovacích protokolů. RIP si
můžete snadno splést, protože bylo stále více podobných protokolů. Některé z nich používaly i stejné jméno. RIP a nesčetně 
pododobné protokoly byly založeny na stejném algoritmu, který používal vektory pro matematický výpočet zahrnující směrovaní k
indentifikaci nejlepší cesty k cílové adrese. Algoritmus vznikl na akademickém výzkumu v roce 1957.

Směrovací aktualizace

RIP posílá aktualizuje směrovaní zpráv v pravidelných intervalech, a když se změní topologie. Když směrovač dostana zprávu o 
aktualizaci směrovaní, která zahrnute změny ve vstupu, aktualizuje to směrovací (routovací) tabulku, aby odrážela novou trasu. 
Jednotka délky se zvýší o 1 a ten co posílal zprávu zjistí další skos. RIP směrovače provádejí jen nejlepší cestu 
(s nejmenších počtem skoků) k destinaci. Po aktualizaci směrovací tabulky, začne router okamžitě posílat informace ostatním 
routerům v síti, aby změnili délky cest.

RIP - funkce stability
RIP zabraňuje směrovacím skokům pokračujícím do nekonečna zavedením limitu povolených skoků v cestě od toho, kdo je posílá až k 
cíli. Maximální počet skoku je nastaven na 15. Pokud router dostane aktualizací informaci, která obsahuje novinku nebo změnu 
vstupu a zvyšuje hodnotu skoků na 16, počítá to, jakoby počet skoků byl nekonečno a zprávy se stanou nedoručitelné. Kvůli 
stabilitě tohoto protokolu je nastavený limit skoků v síti musí být menší než 16.
RIP obsahuje množství dalších funkcí stability, které často obsahují jiné směrovací protokoly. Tyto funkce byly vytvořeny 
pro zajišťování stability kvůli potencionálně rychlým změnám v síťové topologii. Například, RIP rozdělí část sítě 
a zdržující mechanismus udrží siť dole, dokud nebude úprava provedena, aby se nemnožily nesprávné směrovací informace. 

Popis
RIP je směrovací protokol typu distance-vector (vektor vzdálenosti) využívající Bellmanův-Fordův algoritmus pro určení 
nejkratší cesty v síti. Metrikou směrování je počet skoků k cílové síti (počet skoků). Jako ochrana proti směrovacím smyčkám 
je implementovaný omezený počet směrovačů (hopů) v cestě k cíli, maximální možný počet hopů je 15. Tento limit ovšem také 
omezuje velikost sítí ve kterých lze RIP použít (16 hopů je bráno jako nekonečná vzdálenost a používá se k označení 
nepřístupných, nepoužitelných směrovacích tras).
Původně každý router s RIP vysílal aktualizované směrovací tabulky v intervalu 30 sekund. To z počátku nepředstavovalo žádný 
problém, jelikož směrovací tabulky nebyly tak rozsáhlé, aby se to nějak výrazněji projevilo na síťovém provozu. Vzhledem k 
růstu sítí (a tudíž i směrovacích tabulek) se ale toto řešení ukázalo jako nevhodné, jelikož každých 30 sekund by byla síť 
zahlcena velkým množstvím dat. Moderní implementace RIP toto řeší pomocí různých metod nastavujících časové intervaly každého 
routeru zvlášť, aby byla data rozprostřena v čase, a nedocházelo nárazově k velkým tokům dat.
V dnešních sítích se již RIP nepovažuje za dobrou volbu, jelikož čas potřebný ke konvergenci, či rozšiřitelnost, zaostávají za 
ostatními protokoly jako EIGRP, OSPF, nebo IS-IS. Navíc (bez použití RIP-MTI algoritmu) je kvůli omezenému počtu hopů velmi 
omezená velikost sítě ve které lze RIP nasadit. Naproti tomu je ale RIP snáze konfigurovatelný než ostatní protokoly. 

Ostatní charakteristiky RIP obsahují
• RIP podporuje IP and IPX směrování.
• RIP využívá UDP port 520
• RIP cesty mají administrativní vzdálenost 120.
• RIP maximální počet skoků je 15.

Menčí výcuc
RIP řídí následujícími charakteristikami vzdálenostních vektorů:
• RIP rozesílá routerům aktualizace každých 30 sekund
• RIP rozesílá celkou směrovací tabulku každých 30 sekund
• RIP používá vzdálenostní formu jako metrickou - počet skoků
• RIP používá Bellmanův-Fordův algoritmus pro určení 
nejkratší cesty v síti

RIP verze
RIP má 2 verze, verze první (RIPv1) a verzi druhou (RIPv2).
RIPv1 (RFC 1058) je plno třídová a neobsahuje masku podsítě s aktualizacemi 
routovacích tabulek. Kvůli tomu, RIPv1 nepodporuje proměnnou vzdálenost 
masku podsítě (VLSMs). Když používáme RIPv1, sítě musí být sousedící a 
podsítě hlavní sitě musí být nastaveny se stejnou maskou jakou je maska 
podsítě. Jinak se objeví nesrovnalosti v routovací tabulce nebo hůř.
RIPv1 posílá aktualiza na broadcast - 255.255.255.255.
RIPv2 (RFC 2543) je bez třídová a to zahrnuje masku podsítě s jejími 
aktualizacemi směrovací tabulky. RIPv2 plně podporuje VLKSMs, umožňuje 
nesouvislé sítě a měnící se masky podsítí.
Další zlepšení nabízené v RIPv2 zahrnují:
• Směrovací aktualizace jsou posílány na multicast, používá adresu 224.0.0.9
• Šifrované autentizace můžou být nakonfigurovány na RIPv2 směrovačích (routerech)

Proč používat RIP?
• RIP je jednoduchý na realizaci →
– Mnoho ruzných implementací.
– Protokol byl testovaný mnoha týmy vývojářů.
• V malé síti, RIP má velice malou horní hranici pokud
jde o šířku pásma, malou spotřebu paměti,
zatížení procesoru, atd.

![snimek obrazovky porizeny 2016-11-16 09-18-40](https://cloud.githubusercontent.com/assets/11191013/20339667/f4637372-abdd-11e6-8faf-f252e67ad4f3.png)



Zdroje v čestině nebo v angličtině
http://www.routeralley.com/guides/rip.pdf
https://en.wikipedia.org/wiki/Routing_Information_Protocol
http://www.cisco.com/c/en/us/td/docs/ios/12_2/ip/configuration/guide/fipr_c/1cfrip.pdf
https://www.nada.kth.se/kurser/kth/2D1490/04/lectures/rip.pdf
http://docwiki.cisco.com/wiki/Routing_Information_Protocol
http://www.cs.cmu.edu/~./tungfai/Documents/PacketSwitching/SRIP.pdf
http://nptel.ac.in/courses/106105080/pdf/M7L2.pdf
http://web.cecs.pdx.edu/~jrb/routing/lectures/pdfs/RIP.pdf
