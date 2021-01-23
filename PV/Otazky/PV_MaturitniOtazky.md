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


# 1. Adresování a správa paměti, Garbage collector

[comment]: <Source> (https://www.baeldung.com/java-stack-heap)

> Tato otázka je vysvětlena v javě.

## Adresace a správa paměti v programovacím jazyce aneb kam nás program pustí

 Ze začátku je nutno říci, že Java byla navržena jako bezpečné a samo řízené
 prostředí, která je řízeno JVM,
a proto nás nepustí jen tak kam se nám zachce, abychom mohli jako v nějakém nižším jazyce
měnit adresové hodnoty a přepisovat si pamět programu a implementovat garbage collector, který java má. To znamená, že v Javě nemůžeme používat destruktory.

- Kód:

```java
    class Osoba {
    int vek;
    String jmeno;

    public Osoba(int vek, String jmeno) {
        this.vek = vek;
        this.jmeno = jmeno;
    }
}

public class OsobaBuilder {

    public static vovek main(String[] args) {
        int vek = 23;
        String jmeno = "John";
        String jmeon = new String("John");
        Osoba Osoba = null;
        Osoba = Osoba(vek, jmeno);
    }
}
```

Na tomto kódu vidíme deklaraci a inizializaci několika jiných typů odvozených od základní třídy Object.

Pojďme analyzovat tento kód


1. Při vstupu do main metody místo v zásobníku je vytvořeno aby uložilo primitivní datové typy a blok této metody pro ukládání

   1. Primitivní hodnoty integeru id se uloží přímo na zásobník
   2. Reference na proměnnou osoba bude také vytvořena na zásobník, která bude ukazovat na objekt na haldě

2. Volání parametrizovaného konstruktoru Osoba(int,String) z main() zabere další pamět na vrcholu předchozího zásobníku.Uloží se:
   1. this object reference na volaný ojekt na zásobníku
   2. primitivní hodnota id na zásobník
   3. reference na proměnnou name, která bude ukazovat na string ze string pool na haldě
3. Pro nově vytvořený objekt person typu Osoba všechny instance proměnné budou uloženy na haldu

![](images/java-heap-stack-diagram.png)

## Garbage Collector a jeho implementace v javě

```java
    Integer i = new Integer(4);
    //Nějaký kód s proměnnou
    i = null;
    //System.gc(); Může zavolat Garbage Collector, ale navrhujeme
    // JVM aby recyklovalo nepoužívané objekty
```

Jak už bylo řečeno Garbage collector ničí objekty, které jsou podle něj unreachable.Nemůžeme předpokládat kdy bude gc čistit pamět nebo kdy se bude muset třeba v horším případě program i zastavit, kvůli čištění paměti. Je to určitě snažší pro programování bez myšlení na náročnost paměti či náročnosti výpočetní, ale jako programátor, který zodpovídá za svůj program by měl vědět kdy program bude využívat svůj čas pro svoji správu.

Výhody:

- Žádná nutnost obstarávání manuální alokace/delokace paměti kvůli nepoužitému místu 
- Nemusíme se starat o ukazal na místo kde už objekt neexistuje 
- Automatické starání se o přetečení paměti

Nevýhody:

- Kvůli tomu, že se JVM musí starta o objektovou referenci vytváření/ničení tato aktivita vyžaduje více výpočetní náročnosti místo originální aplikace

- Programátoři nemají kontrolu nad plánováním CPU času dedikovanému na uvolňování nepotřebných objektů

- Používání některých GC implementací může vyústit v nepředpokládanou zástavu aplikace
- Určitě to není tak efektivní jako manuální memory management

# 2. Algoritmizace - Grafy, Prohlédávání stavového prostoru, Řazení

## Teorie Grafů

### Co je graf? 

Graf je matematická struktůra, definovaná množina vrcholů a množinou hran, kde každá hrana je určena povinně dvěma vrcholy a volitelně směrem.
Používá se na modeloví vlastně čehokoliv v reálném světě.Není duležíté jak namalujete graf,ale jak ho propojíte

![](images/graph.svg)

Jak jde vidět, můžeme udělat i cykly a podgrafy v grafu.

### Strom

Jedná se o graf který neobsahuje žádnou smyčku tzn. že se nemohu dostat na stejný vrchol bez toho abych se dostal na vchol na kterém jsem už byl.

![](images/graph-tree.png)

### Binární strom

Binarní strom

![](images/graph-binary-tree.png)


## Prohledávání stavového prosturu

## Řazení



