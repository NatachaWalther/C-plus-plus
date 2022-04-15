# C-plus-plus

## Erste Schritte

**Main** 
``` cpp
#include <iostream>
int main() {
	std::cout << "Hello World\n";
	return 0;
}
```

**Streams**

Ausgabe	`std::cout << "Text";`

Eingabe `std::cin >> wert;`

Fehler `std::cerr << "Text";`

**Kommentare**
``` cpp
// Einzeilig

/*	Mehrere
	...
	Zeilen */
```

## Basisdatentypen

### Deklaration
The variable declaration refers to the part where a variable is first declared or introduced before its first use.
``` cpp
int test;
int test1, test2, test3;
```

### Initialisierung
A variable initialisation is a part where the variable is assigned a memory location and a value.
``` cpp
test = 10;
test1 = 10, test2 = 20, test3 = 30;

// Einheitliche Initialisierung
int zahl {1};
int zahl1 {1}, zahl2 {2}, zahl3 {3};
```

### Ganzzahltypen
**Modifier**

* Signed -> Mit Vorzeichen (default)
* Unsigned -> Ohne Vorzeichen

**�bersicht**

Datentyp | Bytes | Range
---|---|---
short int	|2|	-32,768 to 32,767
unsigned short int	|2	|0 to 65,535
unsigned int	|4	|0 to 4,294,967,295
int|	4|	-2,147,483,648 to 2,147,483,647
long int|	4|	-2,147,483,648 to 2,147,483,647
unsigned long int	|4	|0 to 4,294,967,295
long long int	|8|	-(2^63)  to  (2^63)-1
unsigned long long int	|8|	0 to 18,446,744,073,709,551,615
signed char	|1|	-128 to 127
unsigned char	|1|	0 to 255
float	|4| 
double	|8|	 
long double	|12|	 

**Literale**

Prefixes: They are basically represent in four types.
1. Decimal-literal(base 10):- a non-zero decimal digit followed by zero or more decimal digits(0, 1, 2, 3, 4, 5, 6, 7, 8, 9). <br>
	For example, 56, 78.  
2. Octal-literal(base 8):- a zero followed by zero or more octal digits(0, 1, 2, 3, 4, 5, 6, 7). <br>
	For example, 045, 076, 06210.  
3. Hex-literal(base 16):- 0x or 0X followed by one or more hexadecimal digits(0, 1, 2, 3, 4, 5, 6, 7, 8, 9, a, A, b, B, c, C, d, D, e, E, f, F). <br>
	For example, 0x23A, 0Xb4C, 0xFEA.
4. Binary-literal(base 2):- 0b or 0B followed by one or more binary digits(0, 1). <br>
	For example, 0b101, 0B111.

### Chars

Speicherplatz 1 Byte
``` cpp
char c1 = 'A';
char c2 = 41; // Auch A -> Siehe ASCII-Tabelle
```

### Auto

Compiler sucht automatisch den passenden Typ
``` cpp
auto days = 365; //int
auto hello = "hello"; //string
```

### Konstanten

K�nnen nach der Initialisierung nicht mehr ver�ndert werden

M�ssen direkt initialisiert werden!
``` cpp
constexpr int months = 12;
months = 13; //Fehler
```

Konstanten k�nnen auch mit `const` deklariert werden, wenn sie nicht zur compile Zeit angelegt werden, bsp. Benutzereingaben. Wird auch f�r Variabeln, Objekte, Zeiger oder Parameter verwendet.

## Eingebaute Typen

### Arithmetische Operatoren

F�r mathematische Operationen

Operator | Beispiel | Bedeutung
|---|---|---|
|+ | x+y | Addition 
|- | x-y | Subtraktion
|* | x*y | Multiplikation 
|/ | x/y | Division
|% | x%y | Modulo (Rest)

**Beispiel**

``` cpp
int main() {
	constexpr double pi = 3.141592;
	double r = 0.0;
	std::cout << "Kreisumfangsberechnung\n";
	std::cout << "Radius eingeben: ";
	std::cin >> r;
	if (std::cin.fail()) {
		std::cerr << "Fehler bei der Eingabe\n";
		return EXIT_FAILURE;
	}
	const double U = 2 * r * pi;	//const, da von Eingabe beinflusst
	std::cout << "Der Umfang betraegt " << U << "\n";
	return EXIT_SUCCESS;
	}
}
```
### Inkrement und Dekrement

| Operator | Bedeutung |
|---|---|
|++|Inkrement|
|--|Dekrement|

```cpp
int main() {
	int ivar = 1;
	std::cout << "ivar = " << ivar << '\n';
	ivar++;
	std::cout << "ivar = " << ivar << '\n';
	std::cout << "ivar = " << ivar++ << '\n'; //Zuerst print, dann erh�hen
	std::cout << "ivar = " << ivar << '\n';
	std::cout << "ivar = " << ++ivar << '\n'; //Zuerst erh�hen, dann print
}
```
Output:

ivar = 1

ivar = 2

ivar = 2

ivar = 3

ivar = 4

### Typumwandlung

**Implizit**
Implizite Casts werden vom Compiler automatisch vorgenommen, z.B. um bei einer arithmetischen Operation die Typen der beiden Operanden einander anzugleichen. Auch bei Funktionsaufrufen:

``` cpp
int f(float);
int x = f(1); // konvertiert 1 nach float, um f aufrufen zu k�nnen
```

Wenn Zieltyp den Ausgangstyp aufnehmen kann

**Explizit**

Bisweilen muss ein Cast explizit verlangt werden. Im Beispiel
``` cpp
int a = 3, b = 4;
float x = a/b;
```
erh�lt x den Wert 0, weil die Division zweier Ganzzahlen eine Ganzzahl liefert und den Nachkommateil abschneidet. Sie k�nnten das Problem l�sen, indem Sie eine tempor�re float-Variable einf�hren und damit die Flie�komma-Division erzwingen:
``` cpp
int a = 3, b = 4;
float fa = a;
float x = fa/b; // jetzt wird x = 0.75 zugewiesen
```
Das l�sst sich ohne die tempor�re Variable eleganter schreiben, entweder in der �klassischen� Cast-Notation (C-style cast)
``` cpp
float x = (float)a/b;
```
oder gleichwertig in der funktionalen Notation (function-style cast)
``` cpp
float x = float(a)/b;
```
Mehr in Kapitel 4

## Kontrollstrukturen



## Arrays und Strings



## Referenzen und Zeiger



## Funktionen


## Modularisierung und Pr�prozessor



## Strukturen, Aufz�hlungen und dynamische Speicherobjekte



## Klassen



## Objekte und Klassenelemente



## Operatoren �berladen



## Vererbung



## Templates



## Fehlerbehandlung



## Ein-/Ausgabestreams


## Weitere Sprachelemente


