
# ☕ Java – Kompletní průvodce syntaxí a objektovým programováním (maturita-ready)

Tento dokument je kombinací:
- přehledu syntaxe Javy **od základů až po pokročilé funkce**
- vysvětlení principů **objektově orientovaného programování**
- praktického využití v projektu **Správa sítě** s GUI

---

## 📌 Základy syntaxe

### Proměnné a datové typy
```java
int celeCislo = 10;
double desetinne = 3.14;
String text = "Ahoj!";
boolean pravda = true;
char znak = 'A';
```

### Operátory
```java
int a = 5 + 3;     // sčítání
int b = 10 - 4;    // odčítání
int c = 2 * 6;     // násobení
int d = 9 / 3;     // dělení
int e = 10 % 3;    // zbytek po dělení
```

---

### Podmínky a větvení
```java
if (a > 0) {
    System.out.println("kladné");
} else if (a == 0) {
    System.out.println("nula");
} else {
    System.out.println("záporné");
}

switch (den) {
    case "pondělí": System.out.println("Začátek týdne"); break;
    default: System.out.println("Jiný den");
}
```

---

### Cykly
```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}

int j = 0;
while (j < 5) {
    System.out.println(j++);
}

do {
    System.out.println("aspoň jednou");
} while (false);
```

---

### Funkce a metody
```java
public int secti(int a, int b) {
    return a + b;
}
```

---

### Pole a kolekce
```java
int[] cisla = {1, 2, 3};
for (int n : cisla) {
    System.out.println(n);
}

ArrayList<String> ovoce = new ArrayList<>();
ovoce.add("Jablko");
ovoce.remove("Jablko");
```

---

## 🧱 Objektové programování (OOP)

### Třídy a objekty
```java
public class Osoba {
    String jmeno;
    int vek;
}
Osoba o = new Osoba();
o.jmeno = "Karel";
```

### Konstruktory
**Konstruktor** je speciální metoda, která je volána při vytváření objektu třídy. Jeho úkolem je inicializovat nové objekty s požadovanými hodnotami. Konstruktor má stejný název jako třída a nemá návratový typ.

```java
public class Osoba {
    String jmeno;
    int vek;

    // Konstruktor
    public Osoba(String jmeno, int vek) {
        this.jmeno = jmeno;  // this odkazuje na atribut třídy
        this.vek = vek;
    }
}

Osoba o = new Osoba("Karel", 25);  // Konstruktor inicializuje objekt
```

---

### Gettery a settery
**Gettery** a **settery** jsou metody, které slouží k přístupu a úpravě hodnot atributů (fields) objektu.

- **Getter** je metoda pro získání hodnoty atributu
- **Setter** je metoda pro nastavení hodnoty atributu

```java
public class Osoba {
    private String jmeno;
    
    // Getter pro jmeno
    public String getJmeno() {
        return jmeno;
    }

    // Setter pro jmeno
    public void setJmeno(String jmeno) {
        this.jmeno = jmeno;
    }
}

Osoba o = new Osoba();
o.setJmeno("Karel");  // Nastaví hodnotu
System.out.println(o.getJmeno());  // Získá hodnotu
```

**Proč používat gettery a settery?**
- **Encapsulation**: Tímto způsobem můžeme kontrolovat, jak se hodnoty nastavují a čtou.
- Můžeme přidat logiku pro validaci hodnot při nastavení nebo změně.

---

### Třídy s konstruktorama, gettery a settery pro příklad
```java
public class Auto {
    private String znacka;
    private int rokVyroby;

    // Konstruktor
    public Auto(String znacka, int rokVyroby) {
        this.znacka = znacka;
        this.rokVyroby = rokVyroby;
    }

    // Gettery
    public String getZnacka() {
        return znacka;
    }

    public int getRokVyroby() {
        return rokVyroby;
    }

    // Settery
    public void setZnacka(String znacka) {
        this.znacka = znacka;
    }

    public void setRokVyroby(int rokVyroby) {
        this.rokVyroby = rokVyroby;
    }
}
```

---

### Dědičnost
Dědičnost umožňuje jedné třídě dědit vlastnosti a metody od jiné třídy. Pomocí klíčového slova `extends` může podtřída (child class) převzít metody a atributy nadtřídy (parent class).

```java
public class Student extends Osoba {
    int trida;
}
```

---

### Abstraktní třídy
**Abstraktní třídy** nelze přímo instancovat. Můžou obsahovat jak metody s tělem (implementované), tak metody bez těla (abstraktní). Třída, která dědí od abstraktní třídy, musí implementovat abstraktní metody, pokud nejsou již implementovány v nadtřídě.

```java
public abstract class Zvire {
    public abstract void zvuk();
}
```

---

### Rozhraní (interfaces)
**Rozhraní** definuje metody, které třída musí implementovat, ale neobsahuje jejich implementaci. Rozhraní je použitelné pro různé třídy, které mohou mít různý základní typ, ale sdílejí stejný **chování** (např. tiskárny mohou implementovat rozhraní `Tisknuto`).

```java
public interface Zobrazitelne {
    void zobraz();
}
```

### Polymorfismus
**Polymorfismus** znamená, že objekt může být různých typů a metody mohou být volány na základě skutečného typu objektu. Například, různé implementace metody `zvuk()` pro různé podtřídy zvířat.

```java
Zvire z = new Pes();
z.zvuk(); // volá metodu Pes.zvuk()
```

---

## 🎨 Swing GUI

### Vytvoření okna
```java
JFrame frame = new JFrame("Okno");
frame.setSize(400, 200);
frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
frame.setVisible(true);
```

### Komponenty
- `JLabel`, `JButton`, `JTextField`, `JPanel`, `JComboBox`, `JTable`, `JOptionPane`

---

## 🔍 Validace vstupu & regex
```java
String ip = "192.168.0.1";
if (ip.matches("^(\\d{1,3}\\.){3}\\d{1,3}$")) {
    System.out.println("IP validní");
}
```

---

## 🖌️ Stylování GUI
```java
UIManager.setLookAndFeel(new FlatLightLaf());
```

