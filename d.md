### 1. Definice OS: typy OS; design OS: abstrakce a operace nad nimi – služby, systémová volání.
- **`[2] Dvě základní funkce OS (s vysvětlením)`**
	- rozšíření stroje (virtualizace)
		- zjednodušující interface, abstrakce
		- příklad: čtení/zápis na disk
	- správa prostředků
		- procesory, paměti, V/V zařízení
		- multiplexing (sharing) – sdílení prostředků v čase a prostoru
- **`[4] Vlastnosti moderního OS.`**
	- preemptivní plánování procesů
	- zajištění izolace procesů navzájem
	- efektivní správa paměti
	- operační paměť – virtualizace paměti,
	- sekundární paměť – úložiště – souborové systémy,
	- izolace uživatelů – implementace oprávnění jak na úrovni procesů, tak i na úrovni úložišť (souborů),
	- podpora IPC – umožní procesům komunikaci a synchronizaci, pomáhá předcházet nežádoucím stavům jako je deadlock.
- **`[3] Typy OS podle účelu (alespoň šest).`**
	- Mainframe - OS/390
	- Serverové OS - Linux,Unix
	- Víceprocesorové OS - Beowulf, QNX
	- Osobní - Windows, Mac OS
	- RTOS - QNX, VxWorks
	- Vestavěné OS - QNX, PalmOS 
	- SmartCard OS
- **`[2] Reprezentace abstrakcí (koncepcí) v OS a definice systémového volání.`**
	- procesy - reprezentuje běžící program
	- pamět - virtuální pamět
	- uložiště - souborový systém pro sekundární pamět
	- vstupy/výstupy - zařízení ovladá pomocí driverů
	<br><br>
	- Systémových volání – volání služeb jádra OS
- **`[3] Průběh systémového volání.`**
	- parametry na stack
	- volání systémové funkce v knihovně
	- knihovna: nastavení registru na typ volání
	- knihovna: instrukce TRAP (skok do jádra OS)
	- jádro: dispatch, volání příslušného ovladače
	- (návrat do knihovny a programu)
- **`[1] Příklady systémových volání a co obstarvají (alespoň tři).`**
	- Pro procesy – fork(), exec(), wait()
	- soubory (a V/V operace) – open(), read(), write()
	- adresáře a souborové systémy – mkdir()
	- ostatní volání – nastavení práv, operace se signály, zjištění času, správa paměti
	
---
### 2. Architektura jádra OS: monolitický systém, vrstvený systém, virtualizace na úrovni jádra OS, mikrojádro.
- **`[2] Definice monolitického jádra OS.`**
	- Jádro ve kterém jsou všechny systémové funkce implementovány jako součást jednoho velkého jádra.
	- Všechny části běží v privilegovaném režimu a mají přímý přístup ke všem systémovým prostředkům.
- **`[2] Definice vrstveného jádra OS a čím se liší od monolitického s vnitřní strukturou vrstev.`**
	- Vícevrstvé jadro je rozdělené do vrstev, každá vrstva může volat procedury pouze svoji vrstvy nebo vrsvy pod ní
- **`[3] Definice mikrojádra OS a které funkce zajišťuje.`**
	- Jádro obsahuje pouze nezbytnou čáat, která pracuje v kernel modu. Ostatní funkce jsou implementovány v běžných procesech.
	- Mikrojádro se stará pouze o plánování procesů, komunikaci mezi nimi (IPC) a virtualizaci paměti.
- **`[2] Jak jsou v OS s mikrojádrem zajištěny ostatní funkcionality (které nejsou v mikrojádru).`**
	- Funkcionality existuji v user modu jako procesy. Komunikace uživatelského procesu s těmito procesy je provaděna jádrem.
- **`[3] Definice virtualizace na úrovni jádra OS s příkladem.`**
	- jediné jádro OS + kontejnery: izolace skupin procesů, uživatelů (vč. správce), sítě i souborového systému
	- Tato forma virtualizace je implementována přímo v jádře OS
	- Příklad: Linux Containers – cgroups
- **`[3] Příklady OS různých architektur jádra (monolitické, vrstvené, mikrojádro).`**
	- monolitické - Linux
	- vrstvene - MULTICS
	- mikrojádro - GNU/HURD

---
### 3. Návrh OS a jeho bezpečnost: důvody náročnosti implementace OS, principy jeho vývoje; zabezpečení systému, uživatelských dat a procesů (vyjma útoků na systém, to je jiný okruh).
- **`[4] Hlavní obecné cíle návrhu OS.`**
	- definovat abstrakce
	- poskytnout základní operace nad abstrakcemi
	- zajistit izolaci
	- spravovat prostředky (hardware)
- **`[5] Důvody náročnosti návrhu OS.`**
	- Sdílení dat a prostředků
	- Zpětná kompatibilita
	- Obecnost použití
	- Přenositelnost
	- Rozsáhlost, komplexnost
	- Ochrana
	- Konkurence
- **`[3] Principy vývoje OS.`**
	- jednoduchost
	- úplnost
	- efektivita implementace
- **`[3] Způsoby zabezpečení procesů, dat na médiu a přenášených dat.`**
	- zabezpečení procesů
		- auhtentifikace
		- autorizace
	- zabezpečení dat na médiu
		- šifrování
		- přístupová práva
	- zabezpečení přenešených dat
		- šifrování
		- kontrola integrity dat

---
### 4. CPU: provádění instrukce, pipeline, atomicita a přerušitelnost procesu a průběhu zpracování instrukce, přerušovací systém, průběh zpracování přerušení, časovač, sdílení času.
- **`[4] Popis fází provádění instrukce.`**
	- fetch – načtení instrukce
	- decode – dekódování instrukce (určení činnosti)
	- execute – provedení instrukce
	- write – zápis výsledku
- **`[4] Definice pipeline a další možnosti zvyšování výkonu CPU.`**
	- pipeline -  paralelní zpracování instrukcí na základě rozdělení zpracování na nezávislé kroky 
		- lze zahájit zpracovávání jedné instrukce ještě před dokončením předchozí
	- další možnosti:
		- spekulativní provádění instrukcí
		- hyperthreading
		- více jader
- **`[2] Přerušitelnost procesu, průběhu zpracování instrukce.`**
	- TODO
- **`[5] Přerušovací systém: účel, průběh přerušení.`**
	- Účelem je umožnit okamžitou reakci na události, které vyžadují pozornost, a přerušit běžící proces pro jejich obsluhu.
	- Průběh:
		- CPU provádí proces a HW vygeneruje IRQ
		- CPU: dokončení rozpracované instrukce - uloží se adresa návratu
		- CPU: skok na obslužnou rutinu přerušení
		- rutina: uloží se kontext 
		- rutina: obsluha přerušení
		- rutina: vrátí se kontext, návrat do procesu 
			- plánovač může naplánovat také jiný proces

---
### 5. Vstupně‑výstupní zařízení: ovladače a techniky programování vstupu a výstupu, DMA. Paměť cache, procesorová cache a střední přístupová doba do paměti.
- **`[2] Popis metodu pro komunikaci s V/V Metoda 1 (neefektivní).`**
	- = přístup pouze pomocí instrukcí CPU
	- Procesor má instrukce pro posílání/čtení dat na V/V porty, ale procesor je mnohonásobně rychlejší než V/V zařízení
        -> je potřeba po každé takové operaci čekat, než je možné pokračovat v komunikaci.
	- KROKY: 
        - read/write instrukce registru V/V zařízení,
        - kontrola stavu read/write – neproduktivní čekání
- **`[2] Popis metodu pro komunikaci s V/V Metoda 2 (efektivnější).`**
	- = přístup pomocí instrukcí CPU s přerušovacím signálem z HW
    - Během V/V operace může procesor provádět jinou činnost, která bude po dokončení přerušena HW signalem a pokračuje
    - KROKY:
        - read/write instrukce registru V/V zařízení,
        - provádění jiných operací – produktivní využití CPU,
        - po dokončení přenosu generuje V/V zařízení přerušovací signál, lze tedy pokračovat předáváním dalších dat -> krok 1
- **`[3] Popis metodu pro komunikaci s V/V Metoda 3 (nejefektivnější).`**
	- = DMA (Direct Memory Access).
    - KROKY:
        - Zápis adresy dat, množství dat a příkazu do registru V/V zařízení,
        - provádění jiných operací – produktivní využití CPU,
        - po dokončení přenosu dat generuje V/V zařízení přerušovací signál, který přeruší operace v kroku 2, čímž je přenos dokončen.
    - Tímto způsobem se přenáší celý blok dat bez účasti CPU.
	- Připojené V/V zařízení má alokovaný kanál DMA, pomocí kterého přistupuje k datům přímo do operační paměti.
	- Procesor je použit pouze na začátku přenosu.
- **`[2] Definice paměti cache.`**
	- (Mezipaměť) - Paměť cache je malá, rychlá a vysoce výkonná paměť umístěná blízko procesoru nebo jádra CPU.
	- Je určena ke zrychlení přístupu k datům, která jsou často používána nebo mají tendenci být v blízké budoucnosti použita.
- **`[1] Důvod existence konceptu paměti cache.`**
	- Rychla paměť je drahá, ale levná je pomalejší, aby procesor nebyl zdržován, používá se mezipaměť, která je rychlostí blíž k procesoru.
- **`[2] Důvod efektivity cache i při její relativně malé velikosti.`**
	- (princip lokality) Proces má tendenci přistupovat ke stejné části paměti často, proto i když je relativně malá tak bude více efektivní  
- **`[3] Výpočet střední přístupové doby do paměti.`**
	- Ts = Tc + (HR - 1) * To
	- Tc - přístupová doba do cache
	- To - přístupová doba od operační paměti
	- HR - Hit ratio, kolikrát je se použije blok paměti

---
### 6. Požadavky OS na HW nutný pro jeho implementaci: zejména na procesor, správu a adresování paměti. Registry CPU.
- **`[2+3] Nutné vlastnosti CPU a paměti pro implementaci OS a jejich účel.`**
	- podpora alespoň dvou úrovní oprávnění 
		- kernel a user, což umožní v neprivilegovaném režimu ošetřit neoprávněné přístupy
	- podpora ochrany a virtualizace paměti 
		- umožní využít sekundární paměť pro odložení nepotřebných procesů z operační paměti, umožní relokaci procesů.
- **`[2+2] Nutné subsystémy HW pro implementaci OS (kromě CPU a paměti) a jejich účel.`**
	- přerušovací systém – umožní efektivní využití CPU při asynchronních přenosech dat (např. DMA)
	- programovatelný časovač pravidelně generující přerušení, které umožní preempci procesů
- **`[1+2] Definice registrů CPU, jejich druhy.`**
	- Malé a rychlé paměťové oblasti, které se nacházejí přímo v jádře procesoru. Slouží k uchovávání aktuálních hodnot a provádění operací během provádění instrukcí procesoru.
	- Druhy:
		- program counter
		- instruction register
		- stack pointer
		- PSW
		- ostatní registry (adresní, datové, obecné privátní)`
- **`[3] Stavový registr CPU a zahrnuté příznaky (alespoň tři).`**
	- registr obsahující jednobitové příznaky, které odrážejí různé stavy a výsledky operací prováděných procesorem.
	- Zero flag - označuje, zda je výsledek poslední operace nulový
	- Carry Flag - označuje, zda došlo k přenosu nebo přetečení při aritmetické operaci nebo operaci posunu bitů.
	- Overflow Flag - Indikuje, zda došlo k přetečení při sčítání nebo odčítání s čísly se znaménkem. 

---
### 7. Implementace procesu v OS: proces a program, tabulka procesů, přepínání kontextu, stav procesu, třístavový model, příčiny změn stavů.
- **`[2] Proces a program: definice.`**
	- Proces je běžící instance programu na počítači.
	- Program je soubor instrukcí, které popisují postup nebo algoritmus pro provedení určitého úkolu.
- **`[3] Metadata procesu (alespoň šest).`**
	- PID, PPID, stav, priorita, prava, čas vzniku, doba strávená na cpu
- **`[3] Průběh přepnutí kontextu.`**
	- proces běží
	- -> je zavolan syscall nebo interupt
	- -> skočí se do jádra
	- -> planovač převezme kontrolu
	- -> planovač uloží stav (kontext) do pcb
	- -> nasledně vybere dle algoritmu další process
	- -> stav dalšího procesu nahraje do paměti a přenechá kontroli 
- **`[3] Třístavový model: popis stavů.`**
	- připravený (ready) – pozastaven jádrem OS – může běžet, až mu systém přidělí CPU,
	- běžící (running) – používá CPU
	- blokovaný (blocked) – čekající na vnější událost – nemůže běžet, dokud událost nenastala
- **`[4] Třístavový model: příčiny přechodů mezi stavy.`**
	- vytvořený proces - stav ready
	- scheduler prideli procesor procesu - stav running
	- čekání na I/O - stav bloked
	- vracení výsledku z I/O - stav ready
	- preempce zastavi proces - stav ready

---
### 8. Procesy v OS UNIX/Linux: vznik a zánik procesu, systémová volání fork(2), exec(3), exit(3), wait(2), kill(2); hierarchie procesů, stavy procesů v Linuxu (podle příkazu ps); posixové signály a jejich zpracování.
- **`[4] Příčiny vzniku procesu a spuštění nového programu v posixových systémech, související systémová volání, hierarchie procesů.`**
	- Při inicializaci systému 
	- Systémovým voláním 
	<br><br>
	- fork(), exec()
	- Při inicializaci vytvoří jádro první process od kterého se forkují další procesy -> tím vzniká hiearchie
- **`[4] Příčiny zániku procesu a čekání na potomka v posixových systémech, související systémová volání.`**
	- dobrovolné 
		- Normální - exit()
		- Při chybě 
	- nedobrovolné
		- Fatální chyba
		- Zabití (jiným procesem, jádrem) - kill()
	<br><br>
	- čekání se může vyskytovat v rodičovském procesu, když očekává ukončení svého dětského procesu.
		- wait(), waitpid(), waitid()
- **`[4] Stavy procesů v Linuxu.`**
	- R – připravený nebo běžící (runnable/running),
	- Z – ukončený (defunct, zombie),
	- S – blokovaný (sleep),
	- T – pozastavený nebo krokovaný (stopped, traced),
	- D – nepřerušitelný spánek (uninterruptible sleep); v jádře.
- **`[3] Posixové signály, možnosti jejich zpracování a příklady.`**
	- posixove signaly jednouché zpravy procesum, které jsou zpracovany jadrem nebo registrovanou funkci.
		- SIGHUP 1
		- SIGINT 2
		- SIGQUIT 3
		- SIGTERM 15
		- SIGKILL 9
---
### 9. Vlákna: motivace zavedení vláken, proces × vlákno, možné implementace vláken, obecné problémy při implementaci a používání vláken; knihovna posixových vláken: mutex, bariéra, podmínková proměnná a jejich použití.
- **`[1] Motivace zavedení vláken.`**
	- zvýšení výkonu a zjednodušení programovaní. vlákna vznikají rychleji než procesy
- **`[3] Společné a samostatné položky metadat procesů/vláken.`**
	- ASI ŠPATNĚ!!
	- samostané:
		- program counter a registry (kontext procesoru)
		- stav vlákna
		- stack
	- Ostatní položky jsou sdílené v PCB, hlavně - adresní prostor a prostředky
- **`[2] Důvody vyhrazené části paměti pro každé vlákno.`**
	- umožnění vlastního kontext volání 
	- umožnění vlastních lokálních proměnných 
	- řízení stavu vlákna 
- **`[4] Implementace vláken s podporou OS a bez ní, výhody a nevýhody.`**
	- Bez podpory OS
		- \+ strategie plánovače se dá přizpůsobit aplikaci
		- \+ nevyžaduje se přechod do režimu jádra
		- \+ lepší režie
		- \− page-fault zastaví všechna vlákna.
		- \− složitá implementace knihovny
	- S podporou OS 
		- \+ není třeba neblokujících volání,
		- \+ lze provádět i vlákno procesu, jehož jiné způsobilo page-fault,
		- \− pevná strategie plánovače vláken.
		- \− horší režie – přechod do režimu jádra,
- **`[2] Komplikace při zavádění vláken.`**
 	- vznikají při paralelním provádění více vláken ve stejném procesu
	- při použití nereentrantích fukncí, může docházet k problémům se synchronizací
		- deadlock, race conditions, starvation 
- **`[3] Posixová knihovna vláken: nástroje pro řešení problémů souběhu a jejich účel.`**
		- semafory - Semafor umožňuje vláknu čekat, dokud není dostupný určitý počet prostředků, a poté je uvolnit.
		- mutexy - Nástroj pro zamykání kritických sekcí a zajišťování exkluzivního přístupu k sdíleným prostředkům
		- bariéry - Bariéra je objekt, který umožňuje vláknům čekat na dosažení určitého bodu v programu, než budou pokračovat dál

---
### 10. Plánovač. Cíle plánování, režimy plánování, plánovací kriteria (cíle) pro plánovací algoritmy, plánovací algoritmy.
- **`[3] Úloha plánovače, režimy plánování procesů.`**
	- rozhoduje, který proces (vlákno) má CPU
	- režimy: 
		- preemptivní - proces se musí sám vzdát CPU nebo použít blokující systémové volání,
		- nepreemptivní- plánovač rozhoduje, kdy který proces dostane CPU.
- **`[3] Cíle plánování (obecně a dle určení OS).`**
	- obecně:
		- spravedlnost – každý proces by měl stejně času
		- dodržování strategie (priorit)
		- efektivní využití zdrojů,
	- Dle určení OS:
		- Interaktivní systémy
			- minimalizovat odezvu
			- proporcionalita – vyhovění očekáváním uživatelů
		- Dávkové systémy
			- maximalizovat propustnost (throughput) – počet vykonaných úloh za jednotku času (typicky h),
			- minimalizovat obrat (turnaround time) – průměrný čas na vykonání úlohy,
			- využití CPU – využívat maximálně procesor, aby nevznikaly prostoje, kdy je procesor nevyužit.
		- Systémy real-time
			- respektovat lhůty – zabránění ztráty dat,
			- předvídatelnost – zabránění degradace kvality; je třeba dopředu počítat s možným problémem
- **`[3] Popis plánovacích algoritmů: historické.`**
	- First-Come First-Served (fronta FIFO)
		- ulohy se vykonávají v pořadí co přišli. 
		- ulohy bez V/V zvýhodněny, musí čekat pouze 1
		- ulohy s mnoha V/V musí čekat po dokončení práce než se jiný proces vzdá cpu
	- Shortest Job First  (Nepreemptivní)
		- kratší procesy mají přednost
		- Účinnost je závislá na dobrém odhadu délky běhu procesu
		- Dlouhým procesům hrozí „vyhladovění“ pokud budou systému stále přicházet krátke processy
	- Shortest Remaining Time Next  ( preemptivní )
		- Jedná se o preemptivní variantu SJF.
		- Spustí se proces s nejkratší očekávanou dobou do dokončení.
		- Proces lze přerušit (preempce), nicméně se tak děje zejména v případě nové úlohy v systému
- **`[6] Popis plánovacích algoritmů: moderní a specifické.`**
	- Round robin (preemptivní)
		- plánovač je periodicky aktivován při obsluze přerušení časovače.
		- Typické plánování moderních OS je založené na round-robinu 
		- Každý proces dostane přiděleno časové kvantum pro využívání CPU. Přepnutí na jiný proces je prováděno při vypršení tohoto kvanta nebo při volání blokujícího systémového volání.
		- Délku kvanta je třeba optimalizovat, aby byl čas procesoru efektivně využíván.
	- Priority Based Scheduling (prioritní plánování)
		- Každý proces má přidělenou prioritu, což je obvykle celé číslo.
		- Při výběru, který proces dostane CPU, se dává přednost procesu s vyšší prioritou. 
		- Obvykle algoritmus pracuje s více frontami pro připravené procesy – pro každou prioritu samostatná fronta.
		- Nízká priorita může mít za následek „vyhladovění“ procesu (starvation) – proces s nízkou prioritou se nedostane k CPU
	- Guaranteed Scheduling – Fair-Share
		- Tento algoritmus zaručuje každému uživateli stejné podmínky pro využívání procesoru. Pracuje-li v systému n uživatelů, každý bude mít nárok na CPU 1/n doby.
	- Lottery Scheduling 
		- Každý proces dostane tiket(y) a periodicky se losuje. „Výherní“ proces získá časové kvantum na CPU. Když mu vyprší, losuje se znova.
		- Důležité procesy mohou mít více tiketů, čímž se dá částečně simulovat priorita.
		- Kooperativní procesy si mohou tikety předávat podle vlastní potřeby a tím optimalizovat svůj běh.

---
### 11. Požadavky na plánování v systémech reálného času. Možnosti plánování vláken na víceprocesorových systémech (SMP). Časové a periodické plánování úloh uživatelem – příkazy at a crontab.
- **`[4] Specifické požadavky na plánování procesů v systémech reálného času, plánovatelnost.`**
	- Rychlý souborový systém (rychlé čtení, zápis)
	- Rychlá komunikace procesů
	- Rychlé přepínání kontextu
	- Preemptivní plánování založené na prioritách
	- Plánovatelnost - klíčový koncept v RTOS. Znamená schopnost předem odhadnout a garantovat, že časové požadavky úloh budou splněny.
- **`[4*2] Plánování vláken na systémech SMP a možné optimalizace.`**
	- Procesy obvykle tvoří jednu frontu, ze které se vybírá proces, pokud je volný procesor. Složitější plánování příliš nepoužívá.
	- Plánují-li se však vlákna, lze jejich plánování optimalizovat:
		- load sharing
		- gang scheduling - související vlákna jsou plánována tak, aby běžela na různých procesorech současně, vzájemná synchronizace
		- dedicated processor assignment - při plánování jsou všem vláknům aplikace napevno přiřazeny procesory
		- dynamic scheduling - počet vláken se může během provádění měnit
- **`[3] Příkazy pro nastavení spouštění úloh v daném čase a démony, které to obstarávají. Orientačně možnosti konfigurace.`**
	- Příkaz at
		- Provede příkaz pouze jednou v určitý čas
		- konfigurace se provádí pomocí příkazového řádku, případně /etc/at.allow, /etc/at.deny
		- Příklad: at 10:00
		- Obstarávaný démonem - atd
	- Příkaz crontab
		- Umožňuje periodické spouštění úloh v určitých časových intervalech.
		- konfigurace se provádí pomocí souborů v adresáři /etc/cron.d/ nebo v osobním crontab souboru každého uživatele.
		- Obstaraný démonem - cron

---
### 12. Požadavky na paměť, alokace, adresování, pevné (statické) a proměnné (dynamické) dělení paměti (fixed partitioning, variable partitioning), fragmentace paměti, typy fragmentace, umisťovací algoritmy.
- **`[3] Požadavky na operační paměť (na její vlastnosti).`**
	- relokace paměti procesu
	- ochrana paměti
	- možnost sdílení paměti mezi procesy
	- logická a fyzická organizace
		– logické členění paměti (procesu)
		– adresace (logické adresy → fyzické adresy)
- **`[4] Pevné dělení paměti, nevýhody, umisťování procesů.`**
	- Dostupná paměť je rozdělena do oblastí s pevnými hranicemi.
	- Stejně velké oblasti
		- Proces je zaveden do libovolné volné oblasti
		- Malý proces vždy zabere celou oblast a vzniká tak vnitřní fragmentace 
	- Různě velké oblasti
		- Při umisťování procesů do takto dělené paměti dvě možnosti:
			- zavedeme samostatnou frontu pro každou velikost oblasti - minimalizování vnitřní fragmentace
			- jedinou frontu - přidělí se procesu vždy nejmenší volná oblast, do které se proces vejde (best-fit)
	- nevýhody pevného dělení: fragmentace
- **`[4] Dynamické dělení paměti, nevýhody.`**
	- Při dynamickém dělení paměti jsou paměťové bloky vytvářeny a uvolňovány podle aktuálních potřeb procesů
	- nevýhody: vnější fragmentace, časově náročnější
- **`[4] Umisťovací algoritmy pro dynamické dělení paměti (s popisem).`**
	- best‑fit - nejmenší volnou oblast, do které se proces ještě vejde.
	- worst‑fit - největší volnou oblast, do které je proces následně umístěn.
	- exact‑or‑worst‑fit - jako worst-fit, ale proces se přednostně umístí do přesně vyhovující oblasti, je‑li taková nalezena.
	- first‑fit - hledá první vyhovující oblast, do které se proces vejde.
	- next‑fit - stejně jako first‑fit vybírá první volnou oblast, do které se proces vejde, ale vždy od oblasti, do které se naposledy umisťovalo.

---
### 13. Problém nedostatku operační paměti, odkládání obsahu paměti na disk, virtuální paměť, motivace k zavedení virtuální paměti, výhody virtualizace paměti, princip lokality odkazů, thrashing.
- **`[2+2] Možná řešení nedostatku RAM (s vysvětlením principu).`**
	- překrývání (overlaying)
		- různé moduly programu nejsou vyžadovány současně
		- Jakmile skončí využívání jednoho modulu a je vyžadován modul jiný, první se z paměti uvolní a na jeho místo se nahraje druhý
	- swapping
		- odkládání procesu z operační paměti na sekundární
		- využití levné sekundární paměti (disku)
- **`[3] Virtualizace paměti: definice a HW podpora.`**
	- Procesor je obvykle schopen adresovat větší množství paměti, než je skutečně instalováno.
	- Adresový prostor lze rozšířit tak, aby zahrnoval kromě skutečné fyzické paměti i část sekundární paměti (disku).
	- -> Získáváme tak virtuální paměť.
	- HW podpora:
		- Procesor musí umět pracovat s logickou (virtuální) adresou, kterou předává paměťové jednotce
		- MMU (Memory Management Unit)
			- převádí virtuální adresu na adresu skutečnou - Mezi dvě hlavní virtualizační metody patří stránkování a segmentace.
- **`[2] Virtualizace paměti: motivace a důsledky zavedení, princip fungování (proč může efektivně, přestože je sekundární paměť řádově pomalejší).`**
	- TODO rozdíli v otázkách
	- Motivací zavedení virtuální paměti je umožnit procesům pracovat s větším adresním prostorem, než je fyzicky dostupná paměť.
	- Princip fungování: spočívá v mapování virtuálních adres na fyzické a dynamickém přesouvání dat mezi fyzickou pamětí a sekundární pamětí.
	- Operační systém rozděluje paměť na stránky a udržuje paměťové tabulky pro překlad virtuálních adres na fyzické adresy.
	- I když je sekundární paměť řádově pomalejší než fyzická paměť, virtuální paměť může stále efektivně fungovat díky technikám, jako je cachování a strategie nahrazování stránek
- **`[1] Virtualizace paměti: pojmy (RS, S).`**
	- Část paměti procesu, která je držena ve fyzické operační paměti, se označuje pojmem resident set.
	- Sekundární paměť využívaná pro odkládání (dočasně) nepoužívaných částí adresových prostorů procesů se nazývá swap.
- **`[2] Princip lokality odkazů.`**
	- Dle principu lokality odkazů má proces tendenci v nejbližších okamžicích přistupovat do stejné paměťové oblasti, kam přistupoval nyní.
- **`[3] Thrashing – definice a příčiny.`**
	- situace, kdy část paměti procesu je odložena na disk těsně před tím, než ji proces potřebuje. Tuto část paměti je pak třeba následně nahrát zpět do fyzické operační paměti. Proces tak zbytečně čeká v blokovaném stavu.
	- Thrashing může být následkem špatné organizace operační paměti, nedostatku operační paměti, ale také neoptimalizovaného překladu programu kompilátorem, který nedostatečně dodržuje princip lokality odkazů.

---
### 14. Stránkování paměti, převod adresy, vlastnosti stránkování, sdílení stránek, volba velikosti stránky, řešení problému rozsáhlých stránkových tabulek, TLB.
- **`[5] Princip, vlastnosti (spojitost, fragmentace, sdílení).`**
	- Princip: 
		- fyzická operační paměť RAM je rozdělena na oblasti malé velikosti – rámce (frames)
		- logický adresový prostor procesu se rozdělí na stejně velké části jako RAM – stránky (pages)
		- OS udržuje pro každý proces tabulku přiřazení stránek k rámcům
		- logická adresa se skládá z čísla stránky a offsetu 
			- offset je relativní adresa vzhledem k začátku stránky
			- číslo stránky = logická adresa / velikost stránky
	- Spojitost:
		- procesu se jeví jeho adresový prostor spojitý – lineární
		- skutečné umístění stránek v RAM je nespojité
	- Fragmentace:
		- Díky možnosti umístění stránky kamkoliv se odstraní vnější fragmentace
		- Paměť procesům alokuje vždy po stránkách pevné velikosti, zůstává problém vnitřní fragmentace
		- Pokud budou stránky dostatečně malé, bude i vnitřní fragmentace nízká.
		- Při zmenšování velikosti stránky ale roste počet stránek na proces, a tedy roste také velikost stránkové tabulky, která zabírá další paměť.
	- Sdílení:
		- stejné stránky různých procesů mohou sdílet rámec
			- je zbytečné mít v paměti stejné kopie dat
			- je snadné sdílet stránky v režimu read-only (kód)
			- je třeba brát ohled na odkládání obsahu sdílených rámců na swap
		- lze sdílet i stránky obsahující stránkové tabulky
			- např. dva procesy vykonávající stejný program mohou sdílet část stránkové tabulky příslušející přiřazení stránek pro kód programu
- **`[4] Stránkové tabulky, převod adresy.`**
	- Operační systém udržuje pro každý proces tabulku přiřazení stránek k rámcům.
		- Kromě čísla rámce jsou v tabulce ještě řídicí stavové bity pro danou stránku.
	- Stránkové tabulky musí být také v paměti
		- velikost tabulky může být velká, proto se tabulka umisťuje také do virtuální paměti
		- v RAM nemusí být tabulka celá část může být na disku (swap)
	- Převod adresy:
		- Virtuální adresa se rozdělí na dvě části: číslo stránky a offset v rámci stránky.
		- Číslo stránky se použije jako index do stránkové tabulky, aby se získal příslušný záznam.
		- Záznam ve stránkové tabulce obsahuje fyzickou adresu strnky a příznakyá 
		- Offset se přičte k fyzické adrese stránky získané ze stránkové tabulky, čímž se získá konečná fyzická adresa.
- **`[3] Volba velikosti stránky a důsledky.`**
	- TODO ? promenna/pevná?
	- paměť se alokuje po stránkách pevné velikosti
	- vzniká vnitřní fragmentace
	- menší velikost stránky
		- menší vnitřní fragmentace
		- více stránek na proces - větší stránková tabulka – zabírá další paměť
		- více rámců v RAM = lepší hospodaření s RAM
			- v RAM budou stránky z okolí posledních odkazů na paměť a počet neúspěšných přístupů se bude snižovat
	- větší velikost stránky
		- větší vnitřní fragmentace
		- menší stránková tabulka
		- méně rámců v RAM = horší hospodaření s RAM
			- v RAM budou díky velikosti stránek i bloky paměti, které nejsou aktuálně využívány – princip lokality
			- při nedostatku RAM se bude počet neúspěšných přístupů zvyšovat – hrozí thrashing
		- sekundární paměť je efektivnější při přenosu dat po větších blocích
- **`[3] Řešení rozsáhlosti stránkových tabulek, TLB.`**
	- Problém rozsáhlosti stránkových tabulek se dá řešit několika způsoby:
		- Udržováním pouze části stránkové tabulky v paměti s využitím TLB
		- Použitím invertované stránkové tabulky, která eviduje místo stránek rámce, takže její velikost ovlivňuje jen množství fyzické paměti
		- Použitím víceúrovňových stránkových tabulek a neevidování nepotřebných části tabulky (případně také ještě v kombinaci s TLB).
	- TLB
		- speciální cache pro položky stránkové tabulky
		- obsahuje několik posledních použitých položek stránkové (příp. invertované)
		- tabulky při hledání položky stránkové tabulky se prohledá nejprve TLB
			- kontrola přítomnosti v TLB může být paralelizována
			- nalezení (hit) – převod virtuální adresy na fyzickou
			- nenalezení (miss) – doplnění položky do TLB 

---
### 15. Řídicí bity ve stránkových tabulkách, strategie zavádění, umisťování, nahrazování a uklízení (čištění) stránek paměti, vliv velikosti resident‑set na běh procesů.
- **`[3] Důležité řídicí bity ve stránkové tabulce (z hlediska využívání algoritmy nahrazování) a jejich význam.`**
	- TODO ?
	- R (Referenced)
		- Tento bit označuje, zda byla stránka přistoupena (čtena nebo zapsána) od posledního času, kdy byla označena nebo aktualizována.
		- Algoritmy nahrazování mohou využívat tento bit pro určení, které stránky jsou aktivní a mají být ponechány v paměti.
	- M (Modified): 
		- Tento bit označuje, zda byla stránka od svého posledního nahrání do paměti změněna (modifikována).
		- Algoritmy nahrazování mohou tento bit využít pro identifikaci stránek, které musí být před nahrazením zálohovány na disk, aby byly uloženy aktuální změny.
	- U (Used):
		- Tento bit se podobá bitu R a slouží k označení, zda byla stránka přistoupena nebo ne.
		- Algoritmy nahrazování ho mohou využívat jako jeden ze vstupů pro rozhodování, které stránky mají být nahrazeny.
	- C (Caching):
		- Tento bit označuje, zda je stránka v mezipaměti (cache).
		- Algoritmy nahrazování mohou tento bit využít pro rozhodování, zda je vhodné nahradit stránku v mezipaměti nebo v paměti.
	- X (Exclusive):
		- Tento bit označuje, zda je stránka sdílená mezi více procesy nebo je používána exkluzivně jedním procesem.
		Tento bit může ovlivnit rozhodnutí algoritmů nahrazování, které se snaží minimalizovat výměny stránek mezi procesy.
- **`[3] Strategie zavádění stránek: účel, algoritmy.`**
	- fetch policy – určuje, která stránka procesu se má zavést do fyzické operační paměti.
	- V podstatě existují dva přístupy:
		- demand paging
			- zavádění stránek až v okamžiku, kdy jsou potřeba.
			- Tato strategie způsobuje neúspěšné přístupy (page‑fault) při zavádění procesu.
		- lookahead paging 
			- zavádění stránek předem, obvykle ve větším množství.
			- Dle principu lokality odkazů se zavedou stránky z okolí té právě vyžadované
- **`[1] Strategie umisťování stránek: účel, algoritmy.`**
	- placement policy – určuje, na jaké adresy se stránka zavede.
	- Jelikož procesor pracuje s logickými adresami a přístupová doba do operační paměti je nezávislá na fyzické adrese, typicky se tím operační systém nemusí nezabývat. Skutečnou (fyzickou) adresu určuje a používá obvykle pouze HW.
- **`[4] Strategie nahrazování stránek: účel, algoritmy.`**
	- replacement policy – výběr stránek, které se odloží na disk, je‑li třeba načíst do fyzické op. paměti jiné stránky a není pro ně již volné místo.
	- Mezi algoritmy pro nahrazování stránek patří:
		- Least Recently Used (LRU) – nahrazuje stránku, která nebyla nejdelší dobu použita,
		- Not Recently Used (NRU) – nahrazuje stránku podle příznaků použití a změny (evidováno v řídicích bitech),
		- First-In, First-Out (FIFO) – nahrazuje stránku, která je v paměti nejdéle,
		- Second Chance – FIFO s využitím příznaku použití, kdy použitá stránka je s vynulovaným příznakem použití zařazena na konec fronty
		- Clock Policy - modifikace FIFO TODO
- **`[3] Strategie uklízení (čištění) stránek: účel, algoritmy.`**
	- cleaning policy – určuje, které (modifikované) stránky se uloží na disk.
	- Možné jsou dva typy přístupů:
		- Demand cleaning
			- ukládá stránku až v okamžiku, kdy je to potřeba.
			- Proces, který čeká na nahrání stránky, tak bude čekat na dokončení dvou V/V operací: uložení a načtení.
		- Precleaning
			- implementují periodické ukládání modifikovaných stránek v dávce.
			- Proces, který čeká na načtení stránky, tak bude většinou čekat pouze na dokončení jedné vstupně‑výstupních operace – čtení.
			- Tento přístup však může vést ke zbytečným zápisům, neboť uložené stránky se mohou opět změnit ještě před nutností je odložit.
- **`[1] Volba velikosti resident‑set.`**
	- pevná alokace – fixed-allocation policy
		- procesu je při nahrávání vyhrazen pevný počet rámců RAM
			- rovné či proporcionální rozdělení rámců mezi procesy
			- při page fault, se musí uvolnit rámec stejného procesu
	- proměnná alokace – variable-allocation policy
		- počet rámců procesu se průběžně může měnit
			- zvětšuje se pří vysoké frekvenci výskytů page fault
			- snižuje se při nízké frekvenci výskytů page fault
		- vyžaduje režii OS při odhadu chování procesů

---
### 16. Požadavky na OS pro práci v reálném čase, rozdělení RT OS, pojmy latence a odezva (na úrovni přerušení); vestavěné systémy, OS pro ně a typické požadavky na ně.
- **`[1] Definice systémů RT (pracujících v reálném čase) a jejich správná funkce.`**
	- Operační systémy, které zpracovávají úlohy s přísnými časovými požadavky.
	- Jejich správná funkce spočívá v tom, že dokážou:
		- zpracovávat úlohy v přesně definovaném časovém rámci
		- přiřazovat prioritní úrovně úlohám
		- minimalizovat zpoždění při přepínání mezi úlohami
		- zajišťovat deterministické a konzistentní výsledky.
- **`[3] Rozdělení systémů RT dle dodržování termínů (s popisem).`**
	- hard real‑time – existují absolutní časové limity, při jejichž překročení je odezva zcela bezcenná – systém selže,
	- soft real‑time – časové limity jsou pouze přibližné, jejich překročení pouze sníží užitečnost systému,
	- firm real‑time – odezva po časovém limitu je bezcenná, nicméně systém může snést několik málo zmeškání, aniž by selhal.
- **`[4] Charakteristické vlastnosti RTOS.`**
	- rychlé přepínání kontextu
	- preemptivní plánování založené na prioritách
	- multitasking s komunikací procesů
	- rychlý souborový systém
	- rychlá komunikace procesů
	- speciální systémové služby – alarm, timeout apod.,
	- malé rozměry
- **`[1] Příklady RTOS (alespoň dva).`**
	- QNX, RTLinux
- **`[2] Definice pojmů latence a odezva (na úrovni přerušovacího systému).`**
	- doba odezvy - za jak dlouho operační systém reaguje na požadavek přerušení
	- skládá se z:	
		- doby latence (interrupt latency)
			- doba mezi okamžikem příchodu požadavku na přerušení a okamžikem, kdy se začne provádět odpovídající obslužný program
		- doby obsluhy přerušení (interrupt processing) 
			- doba potřebná k vlastnímu zpracování přerušen
- **`[1] Definice vestavěných systémů.`**
	- počítačové systémy, které jsou součástí jiných (obvykle technických) systémů
	-  obvykle představují jejich řídicí složku nebo tvoří jejich podsystémy
- **`[3] Typické vlastnosti vestavěných systémů (alespoň šest).`**
	- malá spotřeba 
	- malé rozměry a váha 
	- odolnost 
	- reaktivita
	- funkce v reálném čase 
	- spolehlivost a bezpečnost
	- extrémní cenová citlivost

---
### 17. Víceprocesorové systémy, rozdělení dle vazby a dle symetrie, granulovatelnost úlohy, souvislost s vazbou (víceprocesorových systémů) a stupně paralelismu, distribuované (rozptýlené, clusterové) OS.
- **`[2] Kategorie počítačových systémů z hlediska paralelizace zpracování dat.`**
	- SISD (single instruction, single data) – jeden procesor zpracovává jednu množinu dat jedním proudem instrukcí,
	- SIMD (single instruction, multiple data) – jedním proudem instrukcí zpracovává více procesorů více různých množin dat
	- MISD (multiple instruction, single data) – více procesorů provádí různé operace nad jednou množinou dat (neefektivní)
	- MIMD (multiple instruction, multiple data) – více procesorů zpracovává různými proudy instrukcí více různých množin dat.
- **`[2] Rozdělení víceprocesorových systémů dle vazby.`**
	- S volnou vazbou - každý procesor má vlastní operační paměť a V/V subsystém
	- S těsnou vazbou - procesory sdílejí operační paměť
- **`[2] Rozdělení víceprocesorových systémů dle symetrie.`**
	- Symetrický víceprocesorový systém
		- mají shodné procesory.
		- Jádro OS, procesy i vlákna mohou být prováděny libovolným procesorem.
	- Asymetrický víceprocesorový systém
		- procesory jsou funkčně specializované
		- jádro a většina úloh běží na CPU, některé specializované úlohy či jejich části jsou zpracovávané na specializovaných procesorech.
- **`[2] Granularita úlohy: účel, jak se pozná, že úloha je/není granulovatelná.`**
	- Rozdělení úlohy nebo procesu na menší části pro paralelní zpracování a efektivní využití víceprocesorového systému.
	- Granulovatelná úloha: Obsahuje dostatečně dlouhou a samostatnou část, není příliš závislá na ostatních částech úlohy, pracuje s dostatečně velkými daty a umožňuje rovnoměrné rozdělení práce mezi procesory.
	- Ne-granulovatelná úloha: Má příliš krátkou část, je silně závislá na ostatních částech úlohy, pracuje s malými daty nebo je obtížné rovnoměrně rozdělit práci mezi procesory.
- **`[2] Vhodné stupně vazby pro různou granularitu.`**
	- Čím je vazba víceprocesorového systému volnější, tím větší časové ztráty přináší komunikace a synchronizace.
	- Pro hrubě granulované úlohy postačí tedy i víceprocesorový systém s volnou vazbou, který je obvykle levnější.
	- Pro jemně granulované úlohy je z hlediska efektivity lepší použít víceprocesorový systém s těsnou vazbou.

---
### 18. Soupeření procesů (o prostředky), obecné problémy souběhu, vzájemné vylučování, kritická sekce, předpoklady pro řešení KS, požadované vlastnosti řešení KS, typy řešení.
- **`[4] Definice kritické sekce v programu.`**
	- část kódu procesu, ve kterém se manipuluje se sdíleným prostředkem.
- **`[4] Předpoklady pro řešení přístupu do kritické sekce. (Co se předpokládá, že platí, a co se nesmí předpokládat.)`**
	- předpokládá, že procesy se provádějí nenulovou rychlostí
	- algoritmus nesmí mít žádné předpoklady o relativní rychlosti procesů ani o jejich plánování
	- U víceprocesorových systémů se předpokládá, že paměťové místo smí v jednom okamžiku zpřístupnit vždy pouze jediný procesor.
- **`[3] Požadované vlastnosti řešení přístupu do kritické sekce (s vysvětlením).`**
	- pokrok v přidělování - každé vlákno nebo proces, které žádá o přístup do kritické sekce, má nakonec šanci získat přístup
	- omezené čekání -  Řešení by mělo minimalizovat nebo eliminovat zbytečné čekání na přístup do kritické sekce. 
	- vzájemné vylučování – zajištění exkluzivního přístupu
	<br><br>
	- omezené čekání – pouze omezený počet jiných procesů smí získat přístup do kritické sekce před vyhověním žádosti o vstup danému procesu.
	- pokrok v přidělování – rozhodování musí proběhnout v konečném čase, přičemž do rozhodování nesmějí zasahovat procesy provádějící svou ZS
- **`[4] Typy řešení přístupu do kritické sekce (s příklady)`**
	- SW řešení (použití algoritmu pro vstupní a výstupní sekci) 
	- HW řešení (využití speciálních instrukcí procesoru) 
	- Řešení OS (semafor, předávání zpráv) 
	- Řešení programovacího jazyka (monitor) 

---
### 19. Řízení přístupu do kritické sekce pomocí SW metod, příklady nevhodných (obecně nefunkčních) SW řešení, SW algoritmy, vlastnosti (nedostatky) SW metod.
- **`[1+1] SW algoritmus pro KS s proměnnou locked, důvod nefunkčnosti.`**
	```
	locked = 0;	// sdílená proměnná evidující obsazenost KS
	repeat // Pi
		while (locked != 0); // čekání, dokud není KS volná
		locked = 1;	// nastavení obsazené KS
		// kód KS
		locked = 0;	// uvolnění KS
		// kód ZS
	forever
	```
	- Důvod nefunkčnosti:
		- Pokud dojde k přepnutí kontextu u `while(locked != 0)`, pak oba procesy vstoupí do KS
- **`[1+1] SW algoritmus pro KS s proměnnou turn, důvod nefunkčnosti.`**
	```
	turn = 0; // sdílená proměnná určující proces s právem vstupu do KS
	repeat // Pi
		while (turn != i); // čekání, dokud není Pi na řadě
		// kód KS
		turn = 1 − i; // KS je volná pro jiný proces
		// kód ZS
	forever
	```
	- Důvod nefunkčnosti:
		- Pokud P0 již nepožaduje vstup do KS a P1 jej opětovně požaduje, bude P1 trvale čekat – vyhladovění. Požadavek pokroku není splněn!
- **`[1+1] SW algoritmus pro KS s proměnnými flag[i], důvod nefunkčnosti.`**
	```
	flag[i] = false; // sdílené proměnné určující požadavek vstupu do KS procesem Pi
	repeat // Pi
		flag[i] = true; // nastavení požadavku vstupu do KS procesem Pi
		while (flag[1−i]); // čekání, dokud je druhý proces v KS
		// kód KS
		flag[i] = false; // KS není požadována
		// kód ZS
	forever
	```
	- Důvod nefunkčnosti: 
		- Pokud dojde k přepnutí kontextu u `flag[0] = true;` dojde k deadlocku 
- **`[2+2] Funkční SW algoritmy pro řízení přístupu do KS, krátká charakteristika.`**
	- Petersonův algoritmus
		- Kombinuje sdílené proměnné z návrhů 2 a 3, tedy proměnnou turn a pro každý proces proměnnou flag[i]
	- Algoritmus „bakery“
		- Zobecněním Petersonova algoritmu pro více procesů
		- Každý proces dostane před vstupem do KS číslo, které je stejné nebo vyšší než jakékoli již přidělené.
		- Držitel nejmenšího čísla smí vstoupit do KS.
		- Dostanou-li procesy Pi a Pj stejná čísla, přednost má nižší index – min(i, j).
		- Ve výstupní sekci nastaví proces přidělené číslo na nulu.
- **`[5] Specifické nevýhody SW algoritmů pro řízení přístupu do KS (včetně vysvětlení, bez všeobecných nevýhod všech typů algoritmů).`**
	- DOST MOŽNÁ ŠPATNĚ
	- Odolnost vůči chybám v KS. pokud proces Pi havaruje v KS, pro ostatní Pi je stále v KS a ty se do ní nedostanou
	- Aktivní čekání. Procesy čekající na vstup do obsazené KS spotřebovávají v cyklu zbytečně a neproduktivně čas procesoru.
	
---
### 20. Řízení přístupu do kritické sekce pomocí HW metod, výchozí předpoklady pro HW řešení, algoritmy využívající HW instrukce, vlastnosti (nedostatky) HW metod.
- **`[3] Hardwarové předpoklady pro řízení přístupu do KS.`**
	- procesy se provádějí v procesoru kontinuálně, dokud nevyvolají službu OS nebo nejsou přerušeny
	- k přerušení procesu může dojít pouze na hranicích instrukcí
		- mezi dokončením jedné instrukce a zahájením další
	- přístup k paměti je obvykle výlučný – důležité zejména pro systémy SMP
- **`[2+3] HW podpora pro řízení přístupu do KS, popis řešení.`**
	- přes zákaz přerušení
		- Pokud je zakázána obsluha přerušení a proces nevyužívá systémových volání, plánovač nemůže být aktivován, a tudíž žádný jiný proces nemůže běžet -> Toho lze využít pro ošetření kritické sekce pokud není v KS použité systémové volání
		- Nevhodné pro SMP
		- Zvyšuje latenci systému
	- přes speciální instrukce
		- přístup k paměťovému místu je obvykle výlučný -> lze tedy navrhnout instrukci, která atomicky provede dvě akce
			- čtení a zápis jako nedělitelná operace
		- provedení instrukce nelze přerušit
		- context switch probíhá pouze na hranicích instrukcí – zaručí nám tak vzájemné vylučování na SMP
		- test-and-set, xchg (intelx86)
- **`[4+3] Vlastností (nedostatky) HW řešení.`**
	- Neodstraňují nedostatek softwarových řešení, je stále třeba aktivního čekání. 
	- Řeší pouze vzájemné vylučování, ostatní požadované vlastnosti řízení přístupu do kritické sekce je třeba řešit algoritmicky.
	- Nabízejí velmi krátkou vstupní i výstupní sekci.

---
### 21. Nástroj OS: semafor, jeho popis včetně systémových volání, použití semaforu pro řízení přístupu do KS a pro synchronizaci, problém obědvajících filozofů.
- **`[1] Popis nástroje OS: semafor.`**
	- Semafor umožňuje vláknu čekat, dokud není dostupný určitý počet prostředků, a poté je uvolnit.
- **`[1+2+2] Popis systémových volání semaforu.`**
	- sem_init(ref, pshared, value) - inicializuje čítač na hodnotu, pshared uvdava typ sdileni (mezi procesy/vlakny)
	- sem_wait() - snizuje citac
	- sem_post() - zvysuje citac
	- všechny 0 uspech, -1 chyba udavana errno
- **`[3] Popis řešení přístupu do KS používajícího semafor.`**
	- sdílený semafor s se inicializuje na počet procesů smějících vstoupit do KS
	- vstupní sekce volá wait, výstupní sekce volá signal
- **`[3] Popis řešení synchronizace vláken pomocí semaforu.`**
	```
	proces P0
		vypočti x; // S1
		sem_post(&sync);
	proces P1
		sem_wait(&sync);
		použij x; // S2
	```
	- semafor sync inicializujeme na 0
	- s2 musí být proveden po s1 
	- P1 příkazem sem_wait čeká na sem_post z P0
- **`[2] Definice problému obědvajících filozofů a jeho řešení pomocí semaforů.`**
	- u stolu sedí pět filosofů - každý buď přemýšlí nebo jí
	- při jídle každý potřebuje dvě vidličky, ale k dispozici je pouze pět vidliček
	```
	proces Pi
	repeat
		think; // ZS
		sem_wait(&waiter);
		sem_wait(&fork[i]);
		sem_wait(&fork[(i+1)%n]);
		eat;
		// KS
		sem_post(&fork[(i+1)%n]);
		sem_post(&fork[i]);
		sem_post(&waiter);
	forever
	```

---
### 22. Nástroj OS: předávání zpráv, popis systémových volání a možností blokování, použití fronty zpráv pro řízení přístupu do KS a pro synchronizaci, problém svázaných producentů a konzumentů.
- **`[3] Popis nástroje OS: předávání zpráv.`**
	- prostředek k předávání dat mezi procesy, přičemž se používají dvě základní operace:
		- send - zasílá zprávu do fronty,
		- receive - přijímá zprávu z fronty.
- **`[3] Popis typické implementace (ne)blokování systémových volání pro předávání zpráv.`**
	- volání send je neblokující, je-li ve frontě místo, a blokující v případě plné kapacity fronty.
	- Volání receive je neblokující, je-li ve frontě dostupná zpráva, a blokující, je-li fronta prázdná.
	- Blokování končí, jakmile je do fronty zaslána zpráva.
- **`[3] Popis řešení KS používajícího frontu zpráv.`**
	- Do fronty zpráv zašleme tolik inicializačních zpráv, kolik procesů smí současně provádět kód kritické sekce.
	- Ve vstupní sekci se volá operace receive, ve výstupní sekci operace send.
- **`[3] Popis řešení synchronizace vláken pomocí fronty zpráv.`**
	- Inicializace: na začátku je fronta zpráv prázdná.
	```
	proces P0
	vypočti x; // S1
	send(sync, msg);
	proces P1
	receive(sync, &msg);
	použij x; // S2
	```
	- mailbox sync na 0
	- s2 musí být proveden po s1 
	- P1 před provedením S2 volá blokující receive
	- P0 po provedení S1 volá neblokující send
- **`[3] Definice problému svázaných producentů a konzumentů a jeho řešení pomocí fronty zpráv.`**
	- Máme jeden nebo více procesů generujících data (producenti) a několik procesů zpracovávajících vygenerovaná data (konzumenti).
	- Pro snížení prodlev je zaveden mezisklad, kam budou producenti data ukládat a odkud si je konzumenti budou vybírat.
	- Problém
		- Přístup do skladu: producenti ukládali data pouze na volná místa a konzumenti vybírali každý jiná data z obsazených míst.
		- Konzumenti musejí čekat, pokud je sklad prázdný, producenti musejí čekat, pokud je zaplněný.

---
### 23. Nástroj programovacích jazyků: koncept monitoru, problém producentů a konzumentů a jeho řešení pomocí monitoru.
- **`[2+2] Popis konceptu monitoru: jeho účel, struktura a základní vlastnosti.`**
	- konstrukce ve vyšším programovacím jazyce poskytující stejné služby jako semafory, ale snadněji ovladatelné
	- Všechny lokální proměnné jsou přístupné pouze pomocí funkcí monitoru.
	- uvnitř monitoru smí být v každém okamžiku nejvýše jedno vlákno/proces. 
	- Synchronizaci lze řešit pomocí podmínkových proměnných monitoru.
		- S každou podmínkovou proměnnou je sdružena fronta pro vlákna čekající na danou podmínku.
- **`[2] Popis řešení KS pomocí monitoru.`**
	TODO
	- Jelikož monitor zaručuje vzájemné vylučování při spouštění svých funkcí, stačí deklarovat
	  sdílená data v monitoru a umístit kritickou sekci do jeho funkce.
- **`[3] Popis řešení synchronizace vláken pomocí monitoru.`**
	TODO
	- Pro synchronizaci lze použít podmínkové proměnné monitoru v kombinaci s proměnnou vypovídající o stavu dokončení akce.
- **`[6] Definice problému svázaných producentů a konzumentů a jeho řešení pomocí monitoru, podmínky použité u synch. a zdůvodnění jejich použití.`**
	TODO
	- Stačí definovat sdílená data uvnitř monitoru a pro synchronizaci použít podmínkové proměnné.
	  Funkce pro vložení a výběr položek budou součástí monitoru.

---
### 24. Nástroje knihovny posixových vláken: mutex, bariéra, podmínková proměnná.
- **`[3] Popis mutexu, účel a vlastnosti, popis funkcí.`**
	- Nástroj pro zamykání kritických sekcí a zajišťování exkluzivního přístupu k sdíleným prostředkům 
	- Vlastnosti mutexu: Vzájemné vyloučení, Atomická operace 
	- Funkce pro práci s mutexem:
		- pthread_mutex_init(): Inicializuje mutex
		- pthread_mutex_lock(): Zamkne mutex. 
		- pthread_mutex_unlock(): Odemkne mutex.
- **`[2] Způsob použití mutexu.`**
	- před vstupem do části se sdíleným prostředkem se mutex zamkne pro ostatní vlákna/procesy
	- při odchodu z části se sdíleným prostředkem se mutex odemkne pro ostatní vlákna/procesy
	- tím zajišťujeme, že pouze jedno vlákno nebo proces může provádět kód uvnitř této sekce v daný okamžik.
- **`[1+4] Bariéra: účel, použití a popis funkcí (včetně návratové hodnoty funkce čekání).`**
	- Bariéra je objekt, který umožňuje vláknům čekat na dosažení určitého bodu v programu, než budou pokračovat dál
	- Synchronizace vláken na konkrétní místo v programu
	<br><br>
	- pthread_barrier_init
	- pthread_barrier_wait
		- vrací při úspěchu pro jedno vlákno hodnotu PTHREAD_BARRIER_SERIAL_THREAD a pro ostatní nulu; nenulová hodnota = číslo chyby
	- pthread_barrier_destroy
- **`[1+4] Podmínková proměnná: účel, způsob použití a vlastnosti.`**
	- obdoba bariéry, ale nečeká se na určitý počet čekajících vláken, ale na splnění podmínky
	- při jejím splnění mohou být spuštěna všechna vlákna nebo jen jedno

---
### 25. Stav uváznutí (deadlock) a vyhladovění (definice a rozdíl), nutné podmínky pro vznik stavu uváznutí, předcházení a řešení problému stavu uváznutí, algoritmus bankéře.
- **`[2] Definice stavu uváznutí (deadlock).`**
	- když každý proces ve skupině čeká na událost, kterou může vyvolat pouze jiný proces ze skupiny
- **`[1] Definice stavu vyhladovění (starvation), příklad.`**
	- nekončící čekání procesu na přidělení prostředku, proces nečiní žádný pokrok
	- proces v soupeření o prostředek neustále prohrává 
		- př. nízká priorita při soutěži o procesorový čas
- **`[4] Vysvětlení podmínek pro vznik stavu uváznutí.`**
	- vzájemné vylučování prostředků – prostředky lze vlastnit pouze jediným procesem, nelze je sdílet
	- alokace a čekání – proces vlastnící nějaký prostředek může požadovat další prostředek
	- neodnímatelné prostředky – operační systém nemůže alokované prostředky odejmout, ty musejí být explicitně uvolněny vlastnícím procesem,
	- cyklické čekání – řetěz vzájemně čekajících procesů uzavírá cyklus.
- **`[3] Přístupy k řešení odstranění vzniklého stavu uváznutí.`**
	- Vyhnutí se zablokování opatrnou alokací zdrojů 
		- Dovoleny jsou pouze bezpečné stavy.
		- Je nutné znát jisté informace o procesech a prostředcích, aby byla možná implementace.
	- Ignorování problému
	- Prevence/řešení negováním jedné z podmínek pro vznik
	- Detekce a obnovení
		- Násilné odebraní prostředků
		- Obnova (rollback) do stavu bez zablokování přes checkpointy.
		- Násilné ukončení (zabití)
- **`[3] Způsoby prevence vzniku stavu uváznutí.`**
	- prevence negací vzájemného vylučování - pomocí spoolingu -> vytvoření fronty požadavků.
	- prevence negací alokace a čekání – zajistit alokaci všech potřebných prostředků naráz
	- prevence negací neodnímatelných prostředků – zavést možné odebrání prostředku / zabití procesu
	- prevence negací cyklického čekání
	<br><br>
	- Prevence vzniku zablokování dovolením pouze bezpečných stavů
		- Bezpečný stav 
			- není stav uváznutí a existuje plánovací pořadí, při kterém všechny procesy mohou být dokončeny, i když všechny procesy naráz budou požadovat maximum svých potřebných zdrojů (prostředků)
		- Nebezpečný stav
			- stav, kdy může (ale nemusí vždy) nastat uváznutí
			- pokud by každý proces požadoval maximum svých deklarovaných zdrojů a ani jednomu nebude moci systém vyhovět, jedná se o nebezpečný stav
- **`[2] Popis bankéřova algoritmu aplikovaného na procesy (s popisem stavů).`**
	- řešení situace bankéře při jednání s klienty, kterým poskytuje půjčku
	- pokud požadavek klienta vede k nebezpečnému stavu, je tento požadavek odmítnut
	- výchozí předpoklady:
		- pevný počet prostředků
		- každý proces deklaruje své maximální požadavky
		- postupná alokace prostředků
	<br><br>
	- Bezpečný stav:
		- Je možné dokončit všechny procesy a uvolnit všechny zdroje.
		- Žádný proces není zablokován a všechny potřebné zdroje jsou k dispozici.
	- Nebezpečný stav:
		- riziko uvíznutí.
		- Pokud by byl přidělen další zdroj některému z procesů, mohl by systém uvíznout.
	- Uvízlý stav:
		- procesy nemohou dále pokračovat kvůli nedostatku potřebných zdrojů.
		- Tyto procesy jsou vzájemně blokovány a nejsou schopny dokončit svou práci.

---
### 26. IPC: komunikace procesů a vláken, možné prostředky komunikace.
- **`[5] Možné prostředky pro komunikaci procesů / vláken.`**
	- soubor
	- roura
	- socket
	- fronty zpráv
	- sdílená paměť
- **`[5] Krátká charakteristika prostředků pro komunikaci procesů / vláken.`**
	- soubor, databáze - pomalé, náhodný přístup, současný přístup je třeba řídit
	- roura - proudový přístup (FIFO), jednosměrná komunikace
	- socket - proudový přístup (FIFO), obousměrná síťová komunikace
	- fronty zpráv - exkluzivní přístup (FIFO), (jednosměrná) komunikace
	- sdílená paměť - nejrychlejší, náhodný přístup, současný přístup nutno řídit
- **`[5] Popis funkcí pro sokety (alespoň pěti typů).`**
	- socket() - vytvoření nového soketu. Funkce vrací deskriptor soketu.
	- bind() - přiřazení konkrétní adresy a portu k soketu.
	- listen() - slouží k naslouchání příchozích spojení
	- accept() - přijímá příchozích spojení od klientů; Blokuje provádění programu, dokud není přijato příchozí spojení.
	- connect() - k navázání spojení se vzdáleným serverem.
---
### 27. Dělení disku na oddíly, zavaděč OS, důvody dělení, MBR, GPT, swap.
- **`[4] Popis důvodů pro rozdělení disku na oddíly.`**
	- větší flexibilita např:
	- jiný souborový systém (např. pro jiný OS)
	- snadnější správa – oddělení systému od dat
	- možnost snadnější obnovy části dat při přepsání či při HW chybě - chyba se může týkat jen některého oddílu
	- oddíl pro swap – na rozdíl od souboru oddíl netrpí datovou fragmentací - rychlejší přístup
- **`[3] Popis MBR a způsob dělení disku na oddíly.`**
	- struktura používaná na diskových zařízeních s konvenčním BIOS
	- obsahuje zavaděč OS a tabulku rozdělení disku(MPT)
		- tabulka rozdělení disku na oddíly - čtyři záznamy
			- primární – lze z něj zavést OS sekundárním zavaděčem
			- rozšířený – dělí se na logické disky
		- zavaděč systému, může být univerzální – skok na sekundární zavaděč na aktivním primárním oddíle
	- limit 2TB
- **`[3] Popis typů oddílů (pro dělení MBR).`**
	- Primární oddíl
		- základní typ oddílu v MBR.
		- Na disku může být vytvořeno až čtyři primární oddíly.
		- Každý primární oddíl může obsahovat samostatný souborový systém a může být zaveden jako spustitelný.
	- Rozšířený oddíl
		- Rozšířený oddíl je speciální typ oddílu v MBR, který slouží k vytvoření dalších logických oddílů uvnitř něj.
		- Zabírá jeden ze čtyř primárních oddílů.
		- Na disku může být pouze jeden rozšířený oddíl.
- **`[3] Charakterizace GPT.`**
	- GPT je navržena pro disková zařízení s UEFI
	- až 128 (primárních) oddílů (1 záznam má 128 B)
	- odstraňuje limity MBR, nutné pro disky nad 2 TiB
- **`[2] Vysvětlení rozdílů mezi odkládacím prostorem (swap) na samostatném diskovém oddíle a v souboru.`**
	- Odkládací prostor na samostatném diskovém oddílu
		- Je vyhrazen samostatný oddíl na pevném disku pro odkládací prostor.
		- Operační systém přistupuje k tomuto oddílu přímo.
	- Odkládací prostor v souboru
		- Odkládací prostor je uložen jako soubor na existujícím souborovém systému.

---
### 28. Souborový systém, metadata, speciální soubory.
- **`[3] Popis obecné struktury souborových systémů a jejich metadat.`**
	- umožňuje uživatelům a procesům přístup k souborům na paměťovém médiu
	– vytváří logickou strukturu souborů
	– eviduje metadata souborů (atributy, oprávnění)
	– organizuje uspořádání souborů na médiu
	

	- Soubor - slouží jako univerzální forma dlouhodobého uložení dat v sekundární paměti
	- Adresář/Složka - Adresáře umožňují hierarchicky uspořádat soubory do stromové struktury. 
		- Obvykle je adresář reprezentován speciálním souborem, jehož obsah interpretuje operační systém
	- Souborový systém - Umožňuje uživatelům a procesům přístup k datům uloženým v souborech.
		- Eviduje metadata souborů (atributy, oprávnění) a organizuje způsob uložení dat a metadat na paměťovém médiu.
	- Metadata
		- Metadata souborů jsou uložena ve struktuře souborového systému
- **`[3] Metadata souborů vyjma oprávnění (alespoň šest).`**
	- umístění souboru na médiu (adresy alokovaných bloků), typ, velikost, čas změny, vlastnictví, je soubor skrytý, nesmazatelný
- **`[3] Možná oprávnění na soubor (alespoň šest).`**
	- žádné – uživatel se souborem nemá právo jakkoli manipulovat, ani nemusí být schopen zjistit existenci souboru
	- znalost existence – možnost zjistit metadata (jméno, velikost, vlastníka, oprávnění apod.),
	- provádění – jedná-li se o uložený program, smí jej uživatel spustit, ale nemá právo jej číst
	- čtení – soubor lze otevřít ke čtení pro libovolné účely (výpis, kopírování, někdy i provádění), ale nelze v souboru dělat změny,
	- přidávání – do souboru lze přidávat další záznamy, ale nelze nijak modifikovat již uložená data,
	- zápis – lze zapisovat i přepisovat,
	- mazání – uživatel smí soubor odstranit,
	- vytvoření – uživatel smí v adresáři vytvořit nový soubor,
	- změna práv – uživatel může nastavit přístupová práva.
- **`[2] Popis zvláštních typů souborů (alespoň čtyř).`**
	- Symbolic link
		- Jedná se o speciální typ souboru, v jehož datové části je uvedeno nové jméno. 
		- Při přístupu k symbolickému odkazu provede systém textovou záměnu jmen
	- Named pipe - Jednosměrný komunikační nástroj ve formě souboru, dva ukazatele(čtení/zápis) chová jako FIFO.
	- IPC Socket - Umožňuje procesům komunikovat obousměrně.
	- Soubory pro HW zařízení
		- Rozlišují se dva typy zařízení:
			- bloková - s náhodným přístupem po blocích: disky 
			- znaková - proudový přístup po bajtech
- **`[2+2] Charakteristika typů odkazů a jejich reprezentace na souborovém systému.`**
	- hard link
		- Nejedná se tak o speciální typ souboru, ale o vlastnost souborového systému.
		- Jedná se tedy o nové jméno pro již existující soubor včetně jeho metadat.
	- symbolic link
		- Jedná se o speciální typ souboru, v jehož datové části je uvedeno nové jméno.
		- Při přístupu k symbolickému odkazu provede systém textovou záměnu jmen -Tato změna je pro proces transparentní.

---
### 29. Konzistence metadat souborových systémů: příčiny vzniku nekonzistencí, metody zachování konzistence, vlastnosti metod, příklady souborových systémů.
- **`[3] Popis příčiny vzniku nekonzistence metadat souborového systému.`**
	- zápis dat do souboru znamená provedení operací na různých místech na médiu
	- změny probíhají postupně -> vznik nekonzistence
- **`[5] Popis principu žurnálování (včetně nevýhod) a činnost obnovy konzistence po pádu.`**
	- je to transakční log
		- zabraňuje ztrátě konzistence dat při pádu systému
			- žurnál nezabraňuje ztrátě dat při pádu systému
		- změny metadat (případně i dat) se zapisují do transakčního logu, což je kruhový buffer
			- teprve po potvrzení zápisu do žurnálu se provede patřičná změna souborového systému = dvojí zápis = zpomalení
		- při startu systému po pádu není třeba kontrolovat konzistenci celého souborového systému -> zrychlení
			- prochází se žurnál a zkontroluje se konzistence pouze na místech posledních změn
- **`[4] Popis principu metody copy‑on‑write (včetně nevýhod) a činnost obnovy konzistence po pádu.`**
	- kopírování bloku při změně
	- nekonzistence vzniká při změně informací – zápisu
	- souborový systém nikdy nemodifikuje bloky na místě
		- při přepisu se modifikuje kopie bloku
		- stejným způsobem se aktualizují metadata
		- po dokončení zápisu se atomicky provede zneplatnění původních dat a metadat a potvrdí se platnost nových
		- souborový systém je tedy vždy konzistentní
		- data se nezapisují dvakrát (nevýhoda žurnálu odstraněna)
		- nevýhoda: větší datová fragmentace
- **`[3] Příklady souborových systémů ve vztahu k metodě zachování konzistence, alespoň dva různé pro každou metodu (nikoliv různé verze téhož), pro žurnálování zvlášť po dvou příkladech pro dvojí způsob.`**
	- Žurnálování: Ext4, NTFS
	- Kontrola a oprava: FAT32, UFS
	- Copy-on-write: BrtFS, ZFS


---
### 30. Typy úložišť, RAID, způsob alokace dat souborů.
- **`[3] Popis typů úložišť (DAS, NAS, SAN) s příklady.`**
	- DAS (Directly Attached Storage) - lokální paměťové úložiště (blokové zařízení)
		- SCSI, SATA, IDE
	- NAS (Network Attached Storage) - souborový systém zpřístupněný síťovým protokolem
		-  NFS, CIFS (SMB, Samba), AFS
	- SAN (Storage Area Network) - blokové zařízení zpřístupněné síťovým protokolem
		- iSCSI, Fibre Channel
- **`[0] Charakteristika RAID (způsob zapojení včetně minimálního počtu disků a principu ukládání dat, odolnost, rychlost R/W).`**
	- Redundant Array of Independent Disks - zapojení více disků do jednoho virtuálního zařízení
		- HW: závislé na řadiči
		- SW: výpočet parity v CPU
	- výhodou je rychlost a/nebo redundance
- **`[3] RAID 0.`**
	- stripping: prokládané ukládání
	- rychlejší, ale výpadek disku znamená ztrátu všeho
	- minimálně 2 disky
- **`[3] RAID 1.`**
	- mirroring: zrcadlené ukládání
	- rychlejší, redundantní, kapacita jen jednoho disku
	- minimálně 2 disky
- **`[3] RAID 5.`**
	- stripping + parity: prokládané s paritou
	- rychlejší, redundantní, kapacita snížená o jeden disk
	- minimálně 3 disky
- **`[3] Charakteristika možných způsobů alokace dat pro soubory.`**
	- Souvislá alokace - souboru jsou přiděleny po sobě jdoucí bloky
		- při alokaci prostoru na médiu dochází k vnější fragmentaci
			- vznikají díry, které je obtížné využít
			- soubor nemůže (bez přemístění) růst nad limit volného prostoru za posledním blokem
	- Řetězená alokace - alokují se jednotlivé bloky
		- alokační tabulka obsahuje zřetězený seznam
			- každý blok obsahuje odkaz na následující blok
		- odstraněna vnější fragmentace
			- souboru lze přidělit libovolný další blok
		- logicky sousedící bloky mohou být na různých místech na médiu – datová fragmentace
		- př.: souborový systém FAT 
	- Indexová alokace - index obsahuje seznam přidělených bloků
		- odstraněna vnější fragmentace
		- index se může odkazovat na blok s indexem
			- nepřímý index (víceúrovňový)
		- bloky mohou mít i různou velikost
			- redukce vnitřní fragmentace
		- př.: unixové souborové systémy
---
### 31. Vzdálený přístup k OS, telnet, SSH, autentizace, autorizace, zásady tvorby hesla, typy útoků na systém a prevence.
- **`[2] Definice pojmů autentizace a autorizace.`**
	- autentifikace – ověření identity
	- autorizaci – ověření oprávnění
- **`[2] Možné metody autentizace (alespoň čtyři).`**
	- přihlašovací jméno a heslo.
	- heslo na jedno použití
	- biometrie
	- smart card
- **`[3] Popis principu zabezpečení přihlašování pomocí protokolu SSH.`**
	- Princip spočívá v kombinaci asymetrického šifrování, symetrického šifrování a ověřování identity.
	- TODO
- **`[2+2] Riziko přihlašování pomocí protokolu SSH a jak mu předcházet.`**
	- TODO
- **`[2] Zásady tvorby hesla (čtyři nejdůležitější).`**
	- Délka hesla
	- Komplexnost hesla
	- Heslo by nemělo obsahovat slovníkova slova
	- Heslo by nemělo obshaovat osobní udaje
- **`[2] Popis alespoň čtyř typů útoků na systém.`**
	- trojské koně – nevinně vypadající programy, které mají škodlivou „funkci“ navíc (malware),
	- login spoofing – imitace přihlašovací obrazovky,
	- zadní vrátka (back door) – vložená metoda přístupu navíc, např. při speciální kombinaci vstupních dat se zaručí další práva,
	- skenování portů (port scanning) – zjišťování spuštěných služeb a jejich programů pro následný pokus o využití známé bezpečnostní slabiny
	- (D)DoS – (Distributed) Denial of Service – zahlcení serveru množstvím požadavků, takže se služba zastaví nebo alespoň velmi zpomalí
