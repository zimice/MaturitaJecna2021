---
author: "Šimon Kochánek"
date: "31/12/2020"
output: pdf_document
fontsize: 12pt
---

<style type="text/css">
body{
    font-size: 12pt;
}
</style>

# 1. Koncepce a architektura číslicových počítačů

    Pro koncepce číslicových počítačů se používají historicky dvě.

- Hardwardská koncepce
- Von Neumannova koncepce

| ![](images/VonNeumannKoncepce.png) | ![](images/HarvardKoncepce.png) |
| :--------------------------------: | :-----------------------------: |
|        Von Neumann Koncepce        |        Harvard Koncepce         |

## Základní principy počítače Von Neumanova

### A)

- ALU (Aritmeticko-logická jednotka)
- Řadič
- vstupní a výstupní jednotky
- paměť

### B)

    Algoritmus je převeden do programu (posloupnost instrukcí) => Technické prostředky jsou nezavíslé na řešené úloze.
### C)

    Všechny data, instrukce a také adresy jsou vyjádřeny dvojkovými číslicemi.

### D)
    Data a instrukce se uchovávají ve společné paměti na místech označených adresami. Přístup k datům v paměti trvá stejnou dobu pro různá paměťová místa.

### E)
    Zpracování dat řízené programem probíhá automaticky.

## Druhá základní koncepce je Harvardská

    Ta se liší od von Neumanovy v bodu d:
    počítač má dvě oddělené paměti - jednu jen pro uložení programu, druhou jen pro data.
    (Paměťové místo není tedy jednoznačně určeno jen adresou  - na stejné adrese jsou dvě, případně i více než dvě, různá paměťová místa.)

## Základní pojmy

### Procesor

    Procesor neboli CPU je elektrický obvod, který zpracovává instrukce a tím vykonává počítačový program.
    CPU vykonává základní aritmetické, logické, kontrolní, a I/O operace specifikované v instrukci programu.
    Toto vykonává za pomocí hlavní paměti a I/O řadiče a také speciální grafické procesní jednotky.
    Toto zařízení na základní desce osobního počítače tvoří základ počítače tak jak ho známe.

### Mikroprocesor

    Mikroprocesor je obvod obvykle složen na jednom čipu, který dělá stále stejnou činnost.
    Jedná se o více účelové,signálem hodin řízené, registrově založené zařízení,
    které přijme data ve formě binárního kódu a náležitě zpracuje dle instrukcí ve své paměti.
    Odlišnosti od procesoru:
    - Většinou daleko nižší takt
    - Není to část osobního počítače
    - Mnohem nižší bitová architektura

### Mikrokontrolér

    Mikrokontrolér má v sobě mikroprocesor.
    Na čipu Mikrokontroléru najdeme:
    - Mikroprocesor
    - operační pamět
    - pamět programu
    - A/D převodník
    - I/O řadič
    - většinou rozhraní pro sériovou komunikaci
    - obvod pro hodinový signál  
    
    Mikrokontrolér tedy tvoří kompletní zařízení, které je možné naprogramovat s nějakým programem a ono to bude vykonávát neustále svůj program na základě vstupů/výstupů.

### Embedded systém

    Jedná se jednoúčelový počítač, ve kterém je řídící systém zcela zabudován do zařízení, které ovládá. Tvůrci těchto zařízení mohou při návrhu myslet jen na jednu úlohu a tím optimalizovat výkon a odebrat nepotřebné části.Jelikož tyto zařízení většinou musí být levné a prodávat se po sériích je kladen důraz na levnost a zvládání primarních úkolů.
    Může se kupříkladu jednat o herní konzole, bankomaty,digitální kamery atd.


## Architektury procesorů

  Podle vnitřního uspořádaní dělíme procesory na RISC a CISC

### CISC (Complex instruction set computer)

    Označení complex vyjadřuje skutečnost, že strojové instrukce pokrývají velmi široký okruh funkcí, které by jinak šly naprogramovat pomocí jednodušších již obsažených strojových instrukcí(například násobení je možné nahradit sčítaním a bitovými posuny).

### RISC (Reduced instruction set computer)

    RISC udává procesory s redukovanou instrukční sadou, jejichž návrh je zaměřen na jednoduchou, vysoce optimalizovanou sadu strojových instrukcí, která je v protikladu s množstvím specializovaných instrukcí ostatních architektur.Registry bývají víceúčelové, což zjednodušuje návrh překldačů.


# 2. Zobrazení údajů v číslicovém počítači, kódování

## Proč používáme v hw ČP dvojkovou soustavu

        V běžném životě používáme desítkovou soustavu, ale u hardwaru obecně nejde reprezentovat každé číslo stejně.Používat několik stupnic napětí a udržovat je tak aby byly čitelné a bezchybné by byl nemožný úkol.  

    Místo toho se počítače zaměřují na používání pouze dvou hodnot a nuly a jedničky.Když se nachází vyšší napětí než např. 0.9 voltu jedná se o logickou jedničku.

    A samozřejmě se také tento systém nejlépe ukládá na magnetické a optické nosiče.

## převod celého čísla DES do čísla BIN /pomocí dělení/

    Příklad  71 desítkově.  
    71/2 = 35 jelikoz je se zbytkem tak 1
    35/2 = 17 jelikoz je se zbytkem tak 1  
    17/2 = 8 jelikoz je se zbytkem tak 1  
    8/2 = 4 jelikoz je beze zbytku tak 0  
    4/2 = 2 jelikoz je beze zbytku tak 0  
    2/2 = 1 jelikoz je beze zbytku tak 0  
    1/2 = jelikoz je se zbytkem tak 1  
    a vezme to odspoda  
    71 desitkove je 01000111 dvojkove

## převod necelého - reálného čísla BIN do čísla DES /pomocí mnohočlenu/

    číslo kupříkladu 00010110 dvojkově převedu pomocí 

    0*2^0 + 1*2^1 + 1*2^2 + 0*2^3 + 1*2^4 + 0*2^5 + 0*2^6 +0*2^7  = 21

## převod celého čísla DES do čísla BIN /pomocí řádové mřížky/ - příklad u IP adresy 138.72…

    například čislo 183 desítkově

    | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
    |-----|----|----|----|---|---|---|---|
    | 1   | 0  | 1  | 1  | 0 | 1 | 1 | 1 |  

    = 10110111 

    Vyberu si nejblíže mocninu dvou na n a jednoduše jestli je to číslo menší jak čislo nad ním tak ho odečtu napíšu jedničku a jdu na další.

## kódování čísel DES do n-bitového BINÁRNÍHO kódu /n = 4, 5, 16, … co to je váhový kód a jeho význam, hodnoty rozsahu čísel DES v závislosti na n= xx/


    BCD kód je to tzv. "váhový" kod a reprezentuje stavy 0-9 jiné hodnoty nereprezentuje.

    Při převodu např. 2390 desítkově musíme převést každé čislo samostatně
    tedy 0010 0011 1001 0000 v bcd kodu.

    2 desítkově = 0010
    | 8 | 4 | 2 | 1 |
    |-|-|-|-|
    | 0 | 0 | 1 | 0 |

## převod čísla BIN do čísla HEX /vysvětlit vznik Hexadecimálních čísel a jejich význam při zkráceném zápisu operandu nebo adresy, BIN např. jen 10 místné pro převod/

    00011110 dvojkove tak to je 1E seštnáctkově 

    převod je jednoduchy HEX využivá {0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F} a kodovani je pres ctyr mistnou mrizku tedy 8 4 2 1 

    Jestliže máme jen desetimístné čislo přídáme před něj další dvě nuly.HEX zápis čísel se využívá zhlediska zkráceného zápisu jinak velkých čísel.

## převod čísla HEX do čísla BIN

    2F šestnáckově vezmu každé číslo a rozeberu ho na čtyři bity <br />

    2= 0010
    | 8 | 4 | 2 | 1 |
    |-|-|-|-|
    | 0 | 0 | 1 | 0 |

    F = 1111
    | 8 | 4 | 2 | 1 |
    |-|-|-|-|
    | 1 | 1 | 1 | 1 |

    2F HEX = 0010 1111 BIN

## kódování čísel DES do kódu BCD /vysvětlit vznik kódu BCD, co to je váhový kód a jeho význam/

    BCD kód je to tzv. "váhový" kod a reprezentuje stavy 0-9 jiné hodnoty nereprezentuje.Při převodu např. 2390 desítkově musíme převést každé čislo samostatně
    tedy 0010 0011 1001 0000 v bcd kodu.

    2 desitkove tedy=  8 4 2 1 
                       0 0 1 0 

## kódování čísel do kódu GRAY /vysvětlit vznik kódu GRAY, co to je neváhový kód, význam u PLC/

    kod kde se po sobe jdouci hodnoty liší v bitovém vyjádření změnou pouze jedné bitové pozice.
    původně navržen kvůli řušení z elektromagnetických přepínačů.
    Navržen tak aby eliminoval jednoznačnost.

## kódování znaků v ČP (písmena, číslice, řídící znaky komunikace, … )

    Používá se kodování ASCII což je kódová tabulka, která definuje znaky a převádí na reprezentaci ve dvojkové soustavě.

## pravidla kódu ASCII vč. jeho rozsahu, zavedení národního prostředí /srovnání En – CZ/ a spec. znaky semigrafiky

    První ASCII tabulka měla rozsah 128 znaků a byla americká a přídavek o dalších 128 znaků přidal české znaky.

    pravidla pro kódy UNICODE, WINxxx, UTF /každý jednou větou

    S každou verzí unicodu přibývali nové a nové znaky první verze z roku 1991 měla 7129 znaků.
    Každá z těchto kodovacích sad je omezena i když už je docela vysoká např UTF32 využívá 4 bajty.
    Unicode je reprezentace, enkodovani  a práce s textem
    Základní kódování Unicode jsou: UTF-8 UTF-16 (UTF-16BE, UTF-16LE) UTF-32 (UTF-32BE, UTF-32LE)
    WINxxx je take textova reprezentace vyrobena Microsoftem 

## Proč používáme v hw ČP dvojkovou soustavu

V běžném životě používáme desítkovou soustavu, ale u hardwaru obecně nejde reprezentovat každé číslo stejně.
Používat několik stupnic napětí a udržovat je tak aby byly čitelné a bezchybné by byl nemožný úkol.Místo toho
se počítače zaměřují na používání pouze dvou hodnot a nuly a jedničky.Když se nachází vyšší napětí než např. 0.9 voltu jedná se o logickou jedničku.
A samozřejmě se také tento systém nejlépe ukládá na magnetické a optické nosiče.

## převod celého čísla DES do čísla BIN /pomocí dělení/

Příklad  71 desítkově.  
71/2 = 35 jelikoz je se zbytkem tak 1
35/2 17 jelikoz je se zbytkem tak 1  
17/2 8 jelikoz je se zbytkem tak 1  
8/2 = 4 jelikoz je beze zbytku tak 0  
4/2 = 2 jelikoz je beze zbytku tak 0  
2/2 = 1 jelikoz je beze zbytku tak 0  
1/2 = jelikoz je se zbytkem tak 1  
a vezme to odspoda  
71 desitkove je 01000111 dvojkove

## převod necelého - reálného čísla BIN do čísla DES /pomocí mnohočlenu/

číslo kupříkladu 00010110 dvojkově převedu pomocí 

nula krát dva na nultou+ jedna krát dva na prvou + jedna krát dva na druhou + nula krát dva na třetí + jedna krát dva na čtvrtou + nula krát dva na pátou
nula krát dva na šestou + nula krát dva na sedmou což se rovná 21 desítkově

## převod celého čísla DES do čísla BIN /pomocí řádové mřížky/ - příklad u IP adresy 138.72…

například čislo 183 desítkově

128  64  32  16  8  4  2  1  
1 &nbsp;&nbsp;&nbsp;   0 &nbsp;  1 &nbsp; 1 &nbsp;  0  1  1  1

10110111 dvojkově

Vyberu si nejblíže mocninu dvou na n a jednoduše jestli je to číslo menší jak čislo nad ním tak ho odečtu napíšu jedničku a jdu na další.

### kódování čísel DES do n-bitového BINÁRNÍHO kódu /n = 4, 5, 16, … co to je váhový kód a jeho význam, hodnoty rozsahu čísel DES v závislosti na n= xx/


BCD kód je to tzv. "váhový" kod a reprezentuje stavy 0-9 jiné hodnoty nereprezentuje.Při převodu např. 2390 desítkově musíme převést každé čislo samostatně
tedy 0010 0011 1001 0000 v bcd kodu.
2 desitkove tedy=  8 4 2 1 <br />
		               0 0 1 0 

### převod čísla BIN do čísla HEX /vysvětlit vznik Hexadecimálních čísel a jejich význam při zkráceném zápisu operandu nebo adresy, BIN např. jen 10 místné pro převod/

00011110 dvojkove tak to je 1E seštnáctkově 
převod je jednoduchy HEX využivá {0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F} a kodovani je pres ctyr mistnou mrizku tedy 8 4 2 1 
Jestliže máme jen desetimístné čislo přídáme před něj další dvě nuly.HEX zápis čísel se využívá zhlediska zkráceného zápisu jinak velkých čísel.

### převod čísla HEX do čísla BIN

2F šestnáckově vezmu každé číslo a rozeberu ho na čtyři bity <br />
2 = 8 4 2 1 <br />
    0 0 1 0 <br />
F = 8 4 2 1 <br />
    1 1 1 1 <br />
2F HEX = 0010 1111 BIN 

kódování čísel DES do kódu BCD /vysvětlit vznik kódu BCD, co to je váhový kód a jeho význam/
BCD kód je to tzv. "váhový" kod a reprezentuje stavy 0-9 jiné hodnoty nereprezentuje.Při převodu např. 2390 desítkově musíme převést každé čislo samostatně
tedy 0010 0011 1001 0000 v bcd kodu.
2 desitkove tedy=  8 4 2 1 <br />
		               0 0 1 0 

### kódování čísel do kódu GRAY /vysvětlit vznik kódu GRAY, co to je neváhový kód, význam u PLC/

kod kde se po sobe jdouci hodnoty liší v bitovém vyjádření změnou pouze jedné bitové pozice.původně navržen kvůli řušení z elektromagnetických přepínačů .
Navržen tak aby eliminoval jednoznačnost.

### kódování znaků v ČP (písmena, číslice, řídící znaky komunikace, … )

Používá se kodování ASCII což je kódová tabulka, která definuje znaky a převádí na reprezentaci ve dvojkové soustavě.

### pravidla kódu ASCII vč. jeho rozsahu, zavedení národního prostředí /srovnání En – CZ/ a spec. znaky semigrafiky

První ASCII tabulka měla rozsah 128 znaků a byla americká a přídavek o dalších 128 znaků přidal české znaky.

- pravidla pro kódy UNICODE, WINxxx, UTF /každý jednou větou, zkouší se v PV ústní, DS ústní/ 

S každou verzí unicodu přibývali nové a nové znaky první verze z roku 1991 měla 7129 znaků.
Každá z těchto kodovacích sad je omezena i když už je docela vysoká např UTF32 využívá 4 bajty.
Unicode je reprezentace, enkodovani  a práce s textem
Základní kódování Unicode jsou: UTF-8 UTF-16 (UTF-16BE, UTF-16LE) UTF-32 (UTF-32BE, UTF-32LE)
WINxxx je take textova reprezentace vyrobena microsoftem 

# 3. Aritmetické a logické operace v číslicovém počítači, logické funkce


### uveďte -množiny čísel DES / BIN „přirozená“, „celá“, „racionální“, „iracionální“, formáty čísel „INTEGER“, „REAL“, „DOUBLE“ a kde se zpracovávají (celočíselná ALU, NEU z koprocesoru)

<br />  

přirozená by se dala reprezentovat unsigned int,pro celá integer a proc racionální  a iracionální používame float a double.
Double v C++ využívá dvojnásobného místa 64  bitů oproti floatu, ale má více místa na floating point tedy místa za čárkou.
Tedy celočíselná čísla se zpracovávají aritmeticko logické jednotce a s desetinnou čárkou v floating point unit tedy v matematickém koprocesoru

### přehled aritmetických operací (+ - * /) v EU s celočíselnou ALU – sčítačka, násobička
<br />
Binárně sčítat znamená pokud je tam jedna jednička je to jedna jestli obě čísla tak o řád nahoru
Binárně odčítat znamená upravi menšitele na šířku menšence
udělat doplněk menšitele což znamená negaci
a k doplnku přičíst jedničku
součet menšence a druhého doplnku menšitele a upravíme rozdíl na stejnou šířku
Binární násobička
 	 1101
* 	 1010

  	 0000
 	1101
       0000	
      1101
     10000010
Pokud to neni 1*1 tak nula
a kazdy bit nasobim zvlast
Binárně dělit
11011101/1010 = 1011
  1111
   1010
      01 - zbytek
-aritmetické sčítání BIN (A + B), vysvětlení přenosu mezi řády, doporučeno A B celá čís. bez znaménka max. 6 bitů
poloviční binární sčítačka
A B C S
0 0 0 0
0 1 0 1
1 0 0 1
1 1 1 0
S je suma prvního řádu a C je carry out což je o jeden řád nahoru 

-aritmetické odčítání BIN (A - B) za pomoci sčítání s použitím druhého doplňku /pravidla pro jeho vytvoření/, doporučeno A B celá čísla max. 6 bitů a A>B

Binárně odčítat znamená upravi menšitele na šířku menšence
udělat doplněk menšitele což znamená negaci
a k doplnku přičíst jedničku
součet menšence a druhého doplnku menšitele a upravíme rozdíl na stejnou šířku


1101111-1001000 = 0100111

1001000 znegovat 0110111
0110111 + 1 = 0111000

1101111
+0111000

10100111
a upravime na sirku mensence tedy ubereme prvni cislo 0100111

-zapsat doplněk do Bytu (např. -50 DES), znaménkový bit, rozsahy pro Byte (-,+)
Znamenkova cisla 8bitu + je logicka nula a - je logicka jednicka jako prvni bit v bytu 
tedy hodnoty takoveho cisla jsou +127 az -127
+127 je 01111111
-18 je  10010010

-aritmetické sčítání BCD (A + B), jen slovně jak se dělá korekce výsledku, kdy je BCD+ výhodné

Korekce vysledku se provadi dalsi korekcni scitackou jenz po bcd detektoru a scitacke opravi vysledek na bcd
za pouziti korekcniho cisla je jim bud 0 nebo 6 a ma pak i paty bit C

- výroková matematika (technické využití některých log.funkcí / operací), popsat operace „průnik“, „sjednocení“, „shodnost“, „implikace“, „negace“ s využítím Vennových diagramů


prunik logicky AND 
A B AND 
0 0 0
0 1 0
1 0 0
1 1 1
jen pokud jsou obe v jednicce nebo prunik dvou mnozin je mnozina jen spolecnych prvku

sjednoceni logicky OR
A B OR
0 0 0
0 1 1
1 0 1
1 1 1
kdyz alespon jednou jednicka tak vysledek je jedna.Sjednoceni dvou mnozin je mnozina vsechn techto prvku
Implikace
A	B	A->B
0	0	1
0	1	1
1	0	0
1	1	1

znamená vztah vyplývání nebo zahrnutí. Skutečnost nebo výpověď A implikuje nějaké B
Neshodnost logicky XOR

A B XOR
0 0 0
0 1 1
1 0 1
1 1 0

Jestli ze se nerovnaji tak jednicka

-logické násobení BIN (A * B), pravdivostní tabulka pro *, doporučeno A B max. 6 bitů, maskování

A	B	A*B
0	0	0
0	1	0
1	0	0
1	1	1

 	 1101
* 	 1010

  	 0000
 	1101
       0000	
      1101
     10000010

- logické sčítání BIN (A + B), pravdivostní tabulka pro +, doporučeno A B max. 6 bitů

A B A+B
0 0  0
0 1  1
1 0  1
1 1  1
 	 1111 
	+0100
	010011
- logický doplněk BIN, pravdivostní tabulka pro negaci, doporučeno A max. 6 bitů
A A'
0 1
1 0

100101 jeho negace 011010
 
-logická neshodnost BIN (A xor B), pravdivostní tabulka pro xor, doporučeno A B max. 6 bitů
A B XOR
0 0 0
0 1 1
1 0 1
1 1 0

11001 XOR 00101 = 11100
kazdy bit pokud se neshoduji tak jedan

# 4. Kombinační obvody, jejich realizace z pravdivostní tabulky

### Pravdivostní tabulky logických funkcí

        Logická funkce je funkce, která pro konečný počet vstupních parametrů vrací logické hodnoty.

        - Logický průnik AND

        A    B    AND 
        0    0    0   
        0    1    0   
        1    0    0   
        1    1    1   

        <br />

        - Logické sjednocení OR

        A    B    OR  
        0    0    0   
        0    1    1   
        1    0    1   
        1    1    1   

        <br />

        - Logická neshodnost  XOR

        A    B    XOR 
        0    0    0   
        0    1    1   
        1    0    1   
        1    1    0   

        <br />

        - Logický doplněk Negace

        A    A'  
        0    1   
        1    0   

### Kombinační obvody

        Jedná se o takové logické obvody, ve kterých stavy na výstupech závisí pouze na okamžitých kombinacích vstupních proměnných a nezávisí na jejich předchozích hodnotách.

    KO nemají žádnou pamět předchozích stavů, takže kombinaci vstupních parametrů odpovídá jediná výstupní kombinace

    Nejdostupnějším kombinačním obvodem je NAND, neboli známé hradlo 74HC00.Existuje dvou vstupové až osmivstupové ale nikoli liché číslo.
  
        Jeho pravdivostní tabulka:  

        A    B    NAND 
        0    1    1    
        0    1    1    
        1    0    1    
        1    1    0      
  
### Metoda normálních forem

    Jsme tím schopni zapsat a zjednodušit zápis logické funkce.

    Formy:

- součtová (Součet mintermů)

    Jedná se o součet součinů
    a*b*c + a*b*c^....

- součinová (Součin maxtermů)
    Jedná se o součin součtů
    (a+b+c) * (a+b+c^)

### Boolova algebra a zákony

    Skládá se z proměných(X,Y), konstant (1,0) a operací (+,-) a negace (^)

1. Komutativní zákon
   
    x+y = y+x  x*y = y*x

2. Asociativní zákon
   
    (x+y)+z = x+(y+z)  (x*y)*z = x*(y*z)  
3. Distributivní zákon
   
    x*(y+z) = (x*y)+(x*z)  x+(y*z) = (x+y)*(x+z)
4. Zákon o neutrálnosti
   
    x+0 = x     x*1 = x
5. Zákon o agresivitě
   
    x+1 = 1   x*1 = x
6. zákon o idempotenci

    x+x = x  x*x = x
7. Zákon absorpce
   
   x+x*y = x   x*(x+y) = x
8. Zákon absorbce negace
   
   x + ^x *y = x+y    x*(^x+y) = x*y
9.  Zákon dvojí negace
    
    ^^x = x
10. De Morganův zákon
    
    ^(x+y) = ^x*^y   ^(x*y) = ^x+^y

### Reprezentace log. 1 a 0 pomocí napětí

    Ve elektrotechnických výpočetních zařízeních se používá jako nositel informace obvykle elektrické napětí.Informace jsou kódováný binárně používají se dvě napěťové úrovně.Vysoká úroveň je napětí blízke napájecímu Vdd.Nízká úroveň se obvykle blíží 0 voltům(referenční zem, GND).
    
    Hodnoty se líší podle typu použitých obvodů.Obvykle se používá stejnosměrné napětí v řádu několika vltů.V silno

## Pravdivostní tabulky logických funkcí

- Logický průnik AND

| A   | B   | AND |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |

<br />

- Logické sjednocení OR

| A   | B   | OR  |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 1   |

<br />

- Logická neshodnost  XOR

| A   | B   | XOR |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 0   |

<br />

- Logický doplněk Negace

| A   | A'  |
| --- | --- |
| 0   | 1   |
| 1   | 0   |

<br />

## Typy kombinačních obvodů

  Nejdostupnějším kombinačním obvodem je NAND, neboli známé hradlo 74HC00.Existuje dvou vstupové až osmivstupové ale nikoli liché číslo.
  
Jeho pravdivostní tabulka: 

| A   | B   | NAND |
| --- | --- | ---- |
| 0   | 1   | 1    |
| 0   | 1   | 1    |
| 1   | 0   | 1    |
| 1   | 1   | 0    |

<br />

Důvod většího výskytu NANDu je z důvodu jednodušího zapojení než AND.

Mezi kombinačními obvody najdeme krom těchto základních také NOR který má takovou to pravdivostní tabulku:

| A   | B   | NOR |
| --- | --- | --- |
| 0   | 1   | 1   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 0   |

<br />

Také můžeme použít pevné paměti na programování jednotlivých vstupů a na výstup nahrát danou hodnotu.

# 5. Sekvenční obvody, jejich realizace, použíté klopné obvody

## Využití sekvenčních obvodů

<br />

### Definice
  
    Sekvenční obvod se liší od kombinačního nezávislostí na okamžité hodnotě signálu.U sekvečního nám nezáleží na hodnotách na hradlo vstupovanými dokud nepřepneme signál CLK = synchonizační impuls do logické jedničky.Tím získáváme obvod, který je schopen si zapamatovat stav(obsahují pamět).

## Rozdělení

<br /> 

### Synchronní

<br />

    Je zaveden řídící synchronizační signál(hodinový signál, hodiny). Změna vstupní proměnné se promítne do stavu sekvenčního obvodu až při příchodu hodinového signálu.

### Asychronní

    se změna vstupní proměnné promítne ihned do stavu sekvenčního obvodu

### Monostabilní klopné obvody

    mají pouze jeden ustálený stav, tzn., že po aktivacije výstup po určitou dobu v opačném, než ustáleném stavu. Lze je použít např. pro
    časovače, ošetření zákmitu kontaktů atd.

### Bistabilní klopné obvody

    mají dva možné ustálené stavy, tzn., že v libovolném z nich může zůstat libovolnou dobu. Lze je použít např. jako paměť, tvoří i základ složitých sekvenčních obvodů - čítače atd. Nejčastěji se setkáváme s typy RS, RST, D,JK buď v podobě integrovaného obvodu, nebo v podobě funkčních bloků v programovacích schématech programovatelných automatů.

### Astabilní klopné obvody

    nemají ustálený stav, jejich výstup se stále přepíná mezi logickou nulou a jedničkou. Lze je použít jako generátory obdélníkového signálu,např. jako zdroj hodinového kmitočtu.


## Typy obvodů

### D


![](images/d-flip-flop.png)


### JK

### SR

## Realizace sekvenčního obvodu


# 6. Programovatelné logické obvody

### Definice programovatelných hradlových polích (FPGA)

    Programovatelná hradlová pole je v elektronice typ logického integrovaného obvodu, který je vyroben tak, aby mohl být naprogramován až u zákazníka.
    
    Obsahuje pole programovatelných logických obvodů (PLD), logických bloků, umožňuje je navzájem propojit a tím vytvořit takřka libovolné číslicové zařízení (například mikroprocesor, řídící obvod síťové karty a podobně).
    Tím se odlišuje od zákaznických integrovaných obvodů (ASIC), jejichž funkce je dána již při výrobě.
    
    FPGA obvody dnes nacházejí uplatnění v široké škále aplikací díky své programovatelnosti, snadnému návrhu, flexibilitě, neustále klesajícím cenám a zvolna se snižující spotřebě energie vlastním čipem.

### Logický obvod a jeho odvození z pravdivostní tabulky (mintermy, maxtermy) nebo z diagramu

    Máme následující funkci: 
     A  B  | X 
     0  0  | 1 
     0  1  | 0 
     1  0  | 0 
     1  1  | 1 
    F = (a^*b^)+0+0+(a*b) = (a^*b^)+(a*b)
    Tato logická funkce je dosti jednoduchá takže nevyžaduje komplexní řešení za pomocí mintermů/maxtermů a dále nejde zjednodušit.

### Způsoby programování FPGA

#### SRAM

    Programovací buňka založená na technice SRAM se skládá ze šesti tranzistorů, tvořících statickou paměťovou buňku, která řídí programovatelný spínač, následně konfigurující funkci logického bloku nebo topologii propojovacích vodičů. Tato metoda se vyznačuje možností opakovatelného konfigurování FPGA, v některých případech dokonce za chodu. Funkci buňky lze plně ověřit při výrobě FPGA.
    
    Programovací buňka SRAM má mnohem větší rozměry než antipojistka, nicméně, jak již bylo uvedeno, technologie výroby FPGA sleduje technologii výroby SRAM. Jelikož při ztrátě napájecího napětí se u této metody ztrácí informace o konfiguraci, musejí být tato FPGA doplněna trvalou, nezávislou pamětí o konfiguraci.

#### Antipojistka

    Pokud projde antipojistkou vysoký proud tak pojistka sepne jinak je v nesepnutém stavu. Antipojistka se vyznačuje trvalým naprogramováním, malým odporem přechodu, malými rozměry a úplnou testovatelností při výrobě nebo v programátoru.
    
    Její nevýhodou je, že je naprogramována jednou provždy.
    Naopak potenciální výhodou tohoto způsobu je, že výsledný obvod neobsahuje paměť se souborem konfiguračních bitů (configuration bitstream), což je důležité z hlediska obrany proti tzv. zpětnému inženýrství.

### PLA (Programmable Logic Array)

    Obvody PLA byly jedny z prvních, které se v minulosti začaly vyrábět. Avšak z trhu je vytlačily obvody PAL.Dnes se s principem PLA můžeme setkat u některých CPLD obvodů
    
    Obvody PLA ze skupiny PLD, která vychází z teorie programovatelných matic AND a OR. Obě matice jsou programovatelné.
    
    Významy: 
    - Možnost skupinové minimalizace, tím že jeden součinový term mohl být použit ve více výstupních funkcích.
    - Počet součinových termů pro výstupní funkci není omezen jako u obvodů PAL.

![](images/princip_pla.png)

    Obvody PLA realizují zapojení kombinační sítě, které vychází z DNF – součtové normálové formy. 
    V programovatelné součinové matici se vytvářejí jednotlivé součinové termy ze vstupních signálů v přímém a negovaném tvaru.
    
    V programovatelné součtové matici se potom provede součet jednotlivých součinových termů.
    
    Na obrázku je PLA struktura určená pouze pro logickou kombinační síť. Dalším pokračováním je umístění paměťového elementu za součtové hradlo, a tím možnost vytvářet logické sekvenční AND a OR matice obvody

### PAL (Programmable Array Logic)

    Obvody PAL jsou variantou aplikace součinové a součtové matice. V době jejich vzniku doznaly velkého praktického rozšíření a byly jednou programovatelné. Obvody PAL byly časem nahrazeny obvody GAL.
    
    Obvody PAL, Programmable Array Logic je skupina obvodů vycházející z teorie matic AND a OR, kde matice AND je programovatelná a matice OR je pevná.
    
    Významy: 
    - Význam PLA obvodů je dnes spíše historický, protože jako samostatná skupina se v minulosti neprosadily.
      
    - Byly uspěšnější než PLA.
      
    - Původně byly PAL obvody jednou programovatelné, dnes se objevují i reprogramovatelné a hlavně jsou nahrazeny obvody GAL.

![](images/princip_pal.png)

    Podle obrázku může každý výstup použít do logického součtu maximálně 4 součinové termy. Výraz y1 má pouze dva součinové termy, v zapojení se použijí pouze dvě součinová hradla a dvě zůstanou nepoužitá. Nepoužitá součinová hradla neovlivňují výsledný výraz y1.

### GAL (Generic Array Logic)

    Obvody typu GAL, Generic Array Logic jsou obvody, které navazují na obvody PAL a rozšiřují je o dvě významné vlastnosti.
    
    První vlastností je reprogramovatelnost GAL obvodů, čímž vzniká skupina elektricky mazatelných obvodů.
    Druhou vlastností je rozšíření používání OLMC Output Logic Macro Cell, která umožňuje jeden obvod využívat jako kombinační nebo s paměťovými elementy.
    
    Obvody GAL vycházejí z obvodů PAL, mají programovatelnou matici AND a pevnou matici OR a na výstup součtového hradla je zařazena OLMC.
    
    Významy:
    - Z aplikace OLMC buňky vyplývá možnost použití pouze jednoho typu GAL obvodů pro všechny PLD prvky na desce plošného spoje. Je to zmenšení počtu typů součástek na desce plošného spoje.
     
    - Zavedení opětovného programování má význam jednak pro návrháře ale i pro výrobce. Reprogramovatelnost GAL obvodů umožňuje pozdější zavádění změn zapojení GAL obvodů. Je to významný rozdíl vůči PAL obvodům.
     
    -Aplikace elektronického podpisu, který umožňuje identifikaci obsahu GAL obvodů.

![](images/princip_gal.png)

    U GAL obvodů je aplikován bezpečnostní bit, Security Fuse, který zabraňuje neautorizovanému čtení obsahu GAL obvodu. Bezpečnostní bit se dá vymazat pouze s vymazáním celého obsahu GAL obvodu.

### CPLD ( Complex Programmable Logic Device)

    CPLD obvody lze jednak chápat jako další vývojový stupeň obvodů PAl a GAL, zvyšování integrace, protože nejdříve začínaly na principu AND a OR matice.
    Dnes přebírají některé prvky dříve typické pro FPGA, hlavně uplatněním buňky s LUT tabulkou. 

![](images/princip_cpld.png)

    Nejzákladnější popis CPLD obvodu je nejlépe při pohledu na křemík, jedná se o řez integrovaným obvodem.
    Základ CPLD prvku tvoří PLD obvody, IO buňky a propojovací síť vyšší úrovně.
    
    PLD obvod je v převážně typu GAL s OLMC buňkou. Dnes se na tomto místě objevují i zapojení pomocí buněk s LUT, které jsou známe s FPGA obvodů.
    
    PLD obvod má vlastní programovatelnou propojovací síť a je možné v něm vytvářet zapojení logické sítě.Propojovací síť PLD obvodu nazývám propojovací sítí nižší úrovně. Druhá také programovatelná propojovací síť je propojovací síť vyšší úrovně, která propojuje jednotlivé PLD obvody mezi sebou, a tím umožňuje vytvářet logické sítě větší složitosti. 
    
    Základní rozdíl mezi jednotlivými úrovněmi propojovacích sítí je ve zpoždění signálu. Zapojení, které využije pouze propojovací síť PLD obvodu bude mít menší zpoždění než zapojení, které využije i propojovací síť vyšší úrovně.

### Makrocell/OLMC

    OLMC buňka je konfigurovatelná pomocí programovatelných propojek S0 a S1, které umožňují konfigurovat buňku jako kombinační nebo registrový výstup. Jedná se o výstup s paměťovým elementem nebo jako kombinační. Další rozdíl je v aktivnosti výstupu, v přímém tvaru výstup nemá invertor a v negovaném tvaru jej obsahuje.

![](images/princip_macrocell.png)

    Jako paměťový element je většinou D klopný obvod. Signál AR – Asynchronous Reset je asynchronní nulování a signál SP je Synchronous Preset – synchronní nastavení. Signály AR, SP a CLK mohou být odvozeny od pinu nebo generovány jako součin v programovatelné AND matici. 

### Současná nabídka FPGA

    V současnosti FPGA vyrábějí zejména firmy Actel, Altera, Atmel, Lattice a Xilinx. Zde se soustředíme na dvě z nich, na firmy Altera a Xilinx.
    
    Oba výrobci nabízejí jak obvody zohledňující nízkou cenu řešení (Altera Cyclone/CycloneII, Xilinx Spartan-2/Spartan-3), tak obvody s velkou výkonností pro technicky náročné úlohy (Altera APEX/Excalibur Xilinx Virtex2/Virtex4).

### Programování Výstupů

    K popisu hardwarové struktury PLD obvodů slouží v dnešní době vyšší programovací jazyky. Těch existuje několik, jmenujme například Verilog, ABEL nebo VHDL.
    
    VHDL původně vzniklo jako jazyk pro simulace hardwaru. Až později se začal používat k popisu reálných obvodů. Jeho výhodou je hardwarová nezávislost – můžeme psát kód ve VHDL a simulovat jej, aniž bychom předem věděli jaký hardware nakonec použijeme. Jeho nevýhodou je ale relativně velká „ukecanost“ a časté opakování stejných bloků.



# 7. Mikrořadiče (MCU), jeho struktura, význačné integrované periferie

## Harvardská Koncepce ČP 

    Mikrořadiče jsou z hardwarového hlediska hardvardskou architekturou, jelikož zakomponovávají procesor, pamět, i/o periferie atd.

![](images/HarvardKoncepce.png)

    
<br />

## blokové schéma MCU a jeho CPU

![](images/microcontrollerScheme.jpg)

### Mikrořadič minimálně obsahuje:
- CPU /mikroprocesor/, 
- generátor hodinového signálu CLK, 
- paměťový subsystém  
- V/V subsystém. 

Dále jsou běžně přítomny: 

- čítače (pro práci v reálném čase), 
- sériový port, I2C sběrnice, SPI rozhraní,
- řadič přerušení, 
- ale i A/D převodníky s multiplexory, D/A převodníky, obvody logického řízení a řízení spotřeby atd.  


## výrobci + architektury MCU

### Architektury MCU

Vývoj systému s MCU staví návrháře před protichůdné požadavky, které nabízí dvě možnosti řešení:

1) k mikrořadiči připojit z vnějšku rozšiřující sběrnici s potřebnými obvody
   
2) mikrořadič rozšířit uvnitř, tj. vytvořit nový čip – klon, derivát, který nově zahrne původní mikrořadič a navíc i ty pomocné obvody, které vyžaduje aplikace. 
   
Zásadní rozdíl proti variantě

1) rozšíření „vnější sběrnice“ je v tom, že při rozšiřování na „vnitřní sběrnici“ nedochází k ome­zování funkcí vývodů MCU (např. paralelních portů) a tím k deklasování jeho výhod. Rozšiřování na vnitřní sběrnici 
   
2) je ovšem v možnostech jen výrobců MCU.Ti však produkují stále větší počet takto zdokonalených typů, se složením zřetelně orientovaným na určité aplikace, ale se zachováním plné instrukční kompatibility s původním typem MCU. 

### Výrobci

- Nejznámnějším výrobcem v současti je Firma Microchip, jelikož koupila firmu Atmel, která produkuje světově známé mikrokontroléry řady Atmega, jenž jsou používané v deskách Arduino a jejích klonech.
  
- Další známé firmy jsou STMicroelectronics, kteří výrazně více produkují 32bit mcu, jenž nabízejí daleko větší výpočetní výkon.Jejich sady, ale nejsou tak zdokumentované pro veřejnost, ale nemůžeme říct, že by se o to STM snažilo.
  
- Texas Instruments s bohatou historií stojí za zmínku

## charakteristiky a parametry

### Charakteristiky MCU

Rozlišujeme podle:

- Bitové architektury
- Počet vstupů/výstupů
- Frekvence krystalu
- Ceny

#### Bitová architektura

#### Počet vstupů/výstupů

#### Frekvence krystalu

#### Cena

### Paramertry MCU

## integrované periférie + jejich přehled

## technologická realizace a módy periférií (nastavení či programování módu a registry Control a Status)

## přerušovací systém

## Programování MCU (programovací jazyky, vývojové prostředí, asembler, instrukce)

# 8. Program, programovací jazyky, příkaz, instrukce, druhy adresování, skoky


## Program

    Jedná se o posloupnost instrukcí, která popisuje realizaci dané úlohy počítačem.Zápisem algoritmu v programovacím jazyce vytváříme program.Zdrojový kód může být přeložen překladačem do strojového kódu, který je pak přímo vykonáván procesorem, nebo je zdrojový kód vykonáván interpretem.Každý program musí mít začátek nesmí obsahovat syntaktické chyby nebo nebude fungovat správně a musí obsahovat konec jinak se může stát, že program nikdy neskončí nebo vychybuje.

### Mezi tím, jak se programovalo před 40ti lety a jak se programuje dnes, je velký rozdíl.

1. ### Strojový kód
    
    Jedná se program, jenž je souborem instrukcí, kde jsme nemáme žádnou možnost pojmenovávat proměnné nebo zadávat matematické výrazy.

2. ### Nestrukturované paradigma

    Nestrukturovaný přístup je podobný assemblerům, jedná se o soubor instrukcí, který se vykonává odshora dolů. Zdrojový kód již nebyl závislý na hardwaru a byl lépe čitelný pro člověka, přístup na nějakou dobu umožnil vytvářet komplexnější programy. Bylo tu však stále mnoho úskalí: Jediná možnost, jak udělat něco vícekrát nebo jak se v kódu větvit, byl příkaz GOTO .

3. ### Strukturované paradigma


    Strukturované programování je první paradigma, které se udrželo delší dobu a opravdu chvíli postačovalo pro vývoj nových programů. Programujeme pomocí cyklů a větvení. To je v podstatě to, kam jsme se doteď dostali.

    Program lze rozložit do funkcí (metod). U strukturovaného programování hovoříme o tzv. funkcionální dekompozici. Problém se rozloží na několik podproblémů a každý podproblém potom řeší určitá funkce s parametry. Nevýhodou je, že funkce umí jen jednu činnost. Neexistuje totiž způsob, jak vzít starý kód a jen trochu ho modifikovat, musíme psát znovu a znovu - vznikají zbytečné náklady a chyby. Tuto nevýhodu lze částečně obejít pomocí parametrizace funkcí (počet parametrů poté ale rychle narůstá) nebo použitím globálních proměnných. S globálními daty vzniká však nové nebezpečí - funkce mají přístup k datům ostatních.Celý program se potom skládá z nezapouzdřených bloků kódu a špatně se udržuje.

## Používané programovací jazyky

## Python

        Python je interpretovaný, vysoko úrovňový programovací jazyk, jenž je veřejně známý jakožto nejjednoduší a zároveň používaný i u obtížných úloh.
        Jeho filozofie si zadává za cíl jednoduchou orientaci v textu v koleraci s významným odsazováním.
        Využívá objektově orientovaný přístup, aby pomáhal programátorům psát čistý, jednoduchý,logický kód na psaní malých a velkých programů.
        Python program probíhá dynamicky a obsahuje garbage collector.
        Nedávno uveřejnění mikrokontrolér Rpi Pico je v základu inzerován s použítím MicroPythonu se soustředěním na začínající programátory.
        Jelikož je snad s těcho jazyků python nejvýše, vyplňuje nesmyslně moc času zpracováváním jednoho primitivního příkazu a to se negativně jeví na chodu programu.

## Javascript

        S počátky už od roku 1995 jako skriptovací jazyk pro jeden z prvních webových prohlížečů Mosaic, se datuje Javascript.
        Jedná se také interpetovaný jazyk, jenž je používaný na webových stránkách na stylizaci a efekty stránky.Jedná o tzv. Frontend.
        Javascript je také možno používat velice dobře na backend zvaný Node.js na kterém je možné stavět webový server, REST API, atd.
        Javascript potažmo Node.js klade důraz už sám na více vláknové programování a proto je rychlejší než python ve všech ohledech.
        Většina prohlížečů má svůj engine na zpracování Javascriptu.

## Java

        Programovací jazyk, který si zakládá na třídách, a objektově-orientovanému programování.
        Vývíjen společností Oracle, vytvořen ve stejnou dobu jako Javascript. S myšlenkou napsat jednou program a umožnit jeho běh na jakémkoliv zařízení.
        Zkompilovaný kód může běžet na jaké koliv platformě, která Javu podporuje bez jakékoliv rekompilace.
        Kód býva typicky v bytekódu a ten poběží na jakémkoliv Java virtual machine s irelevantostí na jaké počítačové architektůře poběží.
        Java runtime umožňuje dynamicky odkazovat a upravovat běžící kód.Dle Githubu byla Java za rok 2019 nejvíce používaný jazyk.
        

## C++

        S úmyslem vytvořit dodatek k C vznikl jazyk C++.Moderní C++ nabízí OOP, generika a funkcové možnosti, ale stále nabízí výhody C,
        jakožto manipulaci s pamětí a uklízení si paměti.C++ je široce používaný jazyk a je s ním psáno ve všech odvětvích.
        Hry, serverové aplikace, desktopové aplikace, a výkonostní-kritické aplikace.Nevyužívá garbage collector a je kompilován kompilátorem.
        Je hojně používán u mikrořadičů jako STM32 a Arduino, které k tomu využívá knihovnu Wiring.

## C

        Jazyk C je nejnižší jazyk s čitelností dnešních programovacích jazyků.Vyvinut v roce 1972 Dennisem Ritchie, jenž je také otcem Unixu,
        se tento jazyk stále používá u Linuxu, kernelů, a mikrokontrolérů.Je využíván jak zařízeními se 8bit architekturou tak Superpočítači.
        Napsat program v C je dosti složíté, jelikož musí programátor udělat většinu práce sám.V C je napsán Linux díky Linusu Torvaldosi.
        Tento jazyk má také spousty kompilátorů nabízených např. IBM, Microsoft atd.Tento jazyk nemá konkurenci v exekučním čase.
        Na algoritmizaci a zpracování dat neexistuje lepší konkurence, pokud si můžeme dovolit strávit většinu času psaním programu.

## Proces a řízení procesoru



## Programové konstrukce (ukázka příkladu)


```c

#include <stdio.h>

int main(){

}

```

## datové konstrukce (ukázka příkladu)

```java

    public class Item{
        private int id;
        private String nazev;

        public Item(String nazev,int id){
            this.nazev=nazev;
            this.id=id;
        }
    }
    
```

## příkazy + srovnání s instrukcemi

```nasm

    MOV EAX, 7
    MOV R8, 4
    ADD EAX, R8
    MOV R9, 2
    SUB EAX, R9

```

## symbolická instrukce

## instrukční sada

## Způsoby adresování v instrukci
x
## Nepodmíněný a podmíněný skok

# 9. Mikroprocesor v reálném režimu, adresování LA a FA

# 10. Chráněný režim operační paměti, adresování LA a FA

# 11. Stránkování OP, virtuální pamět, princip přenosu DMA

# 12. Multitasking a jeho průběh, popis obvodu řadiče přerušení

# 13. Přerušení a jeho průběh, předání řízení, průběh instrukce volá-ní


# 14. Matematický koprocesor / FPU, kódování čísel v FPU

## Pojem koprocesor

Univerzální procesor v počítači třídy PC umožňuje tvořit programy pro škálu různorodých úkolů, ale ne všechny úkoly jsou řešeny optimálně. Jako příklad lze uvést: 

- výpočty matematických funkcí (goniometrické, exponenciální, v pohyblivé řádové čárce atd.) 

- přenosy dat mezi pamětí a periferiemi pomocí datových kanálů (cyklus DMA  se zabezpečením přenosu proti chybám vč. opakování přenosu při výskytu chyby). 

<br />

Toto je prostor pro realizaci speciálních obvodů procesorového typu, které pak tvoří s hlavním, univerzálním procesorem víceprocesorový systém.

> Z tohoto pak vychází název koprocesor, jelikož se nejedná o hlavní procesor na který by přicházela všechna data, nýbrž spíše jako úsek, který je potřeba spravovat a neústalé přerušování výpočetních cyklů by dosti zpomalovalo práci s počítačem.

<br />

## Vazba a spolupráce s hlavním procesorem

<br />

Komunikační procesor je příkladem volně vázaného koprocesoru, který pracuje podle vlastního programu, uloženého v samostatné části paměti systému.

- Komunikační I/O koprocesor  může pracovat úplně samostatně, je vybaven vlastní operační pamětí (někdy zvanou privátní paměť), proto si své instrukce čte sám. Má vlastní programovací jazyk s asi 50 instrukcemi, s hlavním procesorem  komunikuje přes operační paměť.

Numerický koprocesor (8087) je příkladem závislého koprocesoru 

- Numerický koprocesor je těsně vázaný procesor, který má své instrukce jako součást programu hlavního procesoru. Má asi 70 instrukcí, které z paměti, z kódového segmentu čte hlavní procesor do své fronty instrukcí (reg. RI) a koprocesor frontu sleduje a své instrukce přebírá k řešení.

Koprocesory jsou členěné stejně jako hlavní procesor na 2 jednotky (jednotka řadiče a jednotka realizující úkol - výpočet), což umožňuje i v nich proudově zpracovávat instrukce. Procesory spolu komunikují po lokální sběrnici a obvodům, které budí sběrnici, předávají své požadavky pomocí vlastních stavových signálů.


| Koproc |           | Proc |
| ------ | --------- | ---- |
| ->     | dotaz     |      |
|        | přidělení | <-   |
| ->     | hotovo    |      |

<br />

## Porovnání instrukcí pro FPU a procesor

Hlavní procesor rozpoznává instrukce koprocesoru jako ESCinstrukce (v horní slabice OZ je 11011xxx), rozpozná odkaz na OP (vypočte adresu operandu) a odešle vypočtenou adresu koprocesoru.

Odlišují se instrukce pro FPU předponou F, která představuje 5b konstantu.Takže místo ADD máme FADD atd.

Koprocesor převezme sběrnici a při operandech až 10B dlouhých dokončí jejich načtení. Pokud nejsou potřeba výsledky z „koprocesorovské“ instrukce, může procesor pracovat na dalších svých instrukcích. 

Když je potřeba získat výsledek z koprocesoru, testuje se signál BUSY z koprocesoru, který signalizuje dokončení výpočtu (a nebo způsobí generování „zpožďovací“ instrukce WAIT).

<br />

## Formáty dat v matematickém koprocesoru

Matematický koprocesor zpracovává celá čísla se znaménkem.Zpracovává čísla v binárním kódu jako 32b short integer nebo 64b long integer. Je také schopen pracovat s BCD kodém jako 80 b.U každého formátu je nejvyšší bit znaménkový.
Tedy + = 0.

Všechny formáty se pro práci v koprocesoru převedou na Temp.Real s šířkou 80b.Z toho jsme pak schopni odvézt shortReal a Long Real.Kde se jedná o číslo kde máme 1b signum 8b exponent a 23 mantisu u ShortRealu

<br />

## Blokové schéma FPU, registry

![](images/SchemaFPU.png) 

<br />

Registry koprocesoru 8087:

a) 8 * 80b. datové registry s libovolným přístupem k registrům  nebo
s přístupem k 8 úrovňovému zásobníku (3b ukazatel na zásobník, reg. SW)

b) 8 * 2b. značky (TAG) ke každému registru s významem  00 – platný obsah, 01 – nulový obsah 01 -  „divná“ hodnota a 11 – prázdný

c) 2 * 16b. registry stavového slova a řídícího slova  (SW a CW)

d) 2 * 32b. ukazatelé výjimek – registr Adresa IP je ukazatel instrukce v OP (20b. FA a 11b. části oper. znaku) 

## Řízení módu pomocí CW a SW a průběh výpočtu

- Registr CW:

    | 15 | 14 |   |    |     |     |     | 8   | 7   |   |    |    |    |    | 1  | 0  |
    |----|----|---|----|-----|-----|-----|-----|-----|---|----|----|----|----|----|----|
    | x  | x  | x | IC | RC1 | RC0 | PC1 | PC0 | IEM | x | PM | UM | OM | ZM | DM | IM |

    IC vyjadřuje 2 způsoby nekonečna

    RC řídí zaokrouhlování:  00 k nejbližší hodnotě,  01 k -∞,  10 k +∞  a  11 uříznutí

    PC řídí přesnost:  00 short real, 10 long real a 11 temporary real

    zbylé bity jsou masky přerušení – celkové Interrupt Enable a jednotlivých přerušení

    <br />

- Registr SW:
  
    | 15 | 14 |     |     |     |    |    | 8  | 7  |   |    |    |    |    | 1  | 0  |
    |----|----|-----|-----|-----|----|----|----|----|---|----|----|----|----|----|----|
    | B  | C3 | ST2 | ST1 | ST0 | C2 | C1 | C0 | IR | x | PE | UE | OE | ZE | DE | IE |


    BUSY se připojuje na vstup TEST u 8086

    C3, C2, C1 a C0 jsou podmínkové kódy (analogie s příznakovými bity u F reg.)

    ST (3 bity) je ukazatel zásobníku

    IR je žádost o přerušení (chápe se jako exception - výjimka)

    příznaky chyb – P (přesnosti), U (podtečení), O (přetečení), Z (dělení 0), D (denormalizovaný výsledek) a I (neplatná operace)

## Spolupráce FPU s Cache pamětí

FPU potřebuje na náročné výpočty ukládat mezi výpočty do mezipaměti aby docházelo k efektivním výpočtům a koprocesor mohl úlohu rozkouskouvat na malé kousky.V materiálech jsem nenašel k tomuto bodu dostatek materiálů.

## Příklad převodu reálného čísla do ShortRealu (reálné desítkové – reálné dvojkové – ShortReal 32b)

<br />

Máme po převodu z 10 -> 2 sosutavy znaménkové číslo racionální

+110100,11001

1. normalize ke 2  ( tj. 1,xxxx)

    +1,1010011001*2^5
    nám určí hodnotu exponentu +5
    protože jsme pohnulli o 5 míst vlevo
    
2. určení kódu exponentu
   
    | .. | -1 | 0  | +1 | +2 | +3 | +4 | +5 | +6 | Dec |
    |----|----|----|----|----|----|----|----|----|-----|
    | .. | 7E | 7F | 80 | 81 | 82 | 83 | 84 | 85 | Hex |

    +5 je 84 hex a to je 1000100 bin v kódu s posunutou nulou

3. přepis do ShortRealu formátu

    | S   | 8b EXPONENT | (1+23)b MANTISA |
    |-----|-------------|-----------------|
    | +=0 | 10000100    | 10100110010...0 |
    |     |             | 1,

    Tato 1 je "skrytý bit, který vygeneruje NEU!!!

# 15. Vývoj procesorů od Pentia do současnosti

## Zavedení superskalárních a hyperskalárních procesorů

## Víceúrovňové Cache paměti

## Paralelní ALU a předvídání skoků + možné kolize

## Jednotka MMX a její instrukce

## RISC mikroinstrukce od PeII a dynamické spouštění instrukcí 

## Flashování mikrokódu procesoru

## Vývoj procesoru s 64b architekturou (HyperThreading, core, Cache, …).

# 16. Struktura osobního počítače (stolní, přenosný), popis základní desky 

# 17. Princip monitoru, typy grafických adapterů, kódování souborů

# 18. Digitalizace zvuku, zvukové adaptery a soustavy, kódování soubor

# 19. Vnitřní paměti osobního počítače a jejich provedení, vyrovnávací paměti v procesor

# 20. Vnější paměti osobního počítače, fyzické a logické uspořádání dat

# 21. Nemagnetické nosiče informace pro osobní počítače, uspořádání dat 

# 22. Vstupní a výstupní zařízení osobních počítačů

# 23. Tiskárny pro osobní počítače, používaná rozhraní osobního počítače 

# 24. Ochrana a zabezpečení dat 

# 25. Start počítače, operační systém a jeho zaveden