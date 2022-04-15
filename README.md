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

**Übersicht**

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

**Chars**

Speicherplatz 1 Byte
``` cpp
char c1 = 'A';
char c2 = 41; // Auch A -> Siehe ASCII-Tabelle
```

**Auto**

Compiler sucht automatisch den passenden Typ
``` cpp
auto days = 365; //int
auto hello = "hello"; //string
```

**Konstanten**

Können nach der Initialisierung nicht mehr verändert werden

Müssen direkt initialisiert werden!
``` cpp
constexpr int months = 12;
months = 13; //Fehler
```

Konstanten können auch mit `const` deklariert werden, wenn sie nicht zur compile Zeit angelegt werden, bsp. Benutzereingaben. Wird auch für Variabeln, Objekte, Zeiger oder Parameter verwendet.

## Eingebaute Typen



## Kontrollstrukturen



## Arrays und Strings



## Referenzen und Zeiger



## Funktionen


## Modularisierung und Präprozessor



## Strukturen, Aufzählungen und dynamische Speicherobjekte



## Klassen



## Objekte und Klassenelemente



## Operatoren überladen



## Vererbung



## Templates



## Fehlerbehandlung



## Ein-/Ausgabestreams


## Weitere Sprachelemente


