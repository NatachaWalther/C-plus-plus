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

Können nach der Initialisierung nicht mehr verändert werden

Müssen direkt initialisiert werden!
``` cpp
constexpr int months = 12;
months = 13; //Fehler
```

Konstanten können auch mit `const` deklariert werden, wenn sie nicht zur compile Zeit angelegt werden, bsp. Benutzereingaben. Wird auch für Variabeln, Objekte, Zeiger oder Parameter verwendet.

## Eingebaute Typen

### Arithmetische Operatoren

Für mathematische Operationen

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
	std::cout << "ivar = " << ivar++ << '\n'; //Zuerst print, dann erhöhen
	std::cout << "ivar = " << ivar << '\n';
	std::cout << "ivar = " << ++ivar << '\n'; //Zuerst erhöhen, dann print
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
int x = f(1); // konvertiert 1 nach float, um f aufrufen zu können
```

Wenn Zieltyp den Ausgangstyp aufnehmen kann

**Explizit**

Bisweilen muss ein Cast explizit verlangt werden. Im Beispiel
``` cpp
int a = 3, b = 4;
float x = a/b;
```
erhält x den Wert 0, weil die Division zweier Ganzzahlen eine Ganzzahl liefert und den Nachkommateil abschneidet. Sie könnten das Problem lösen, indem Sie eine temporäre float-Variable einführen und damit die Fließkomma-Division erzwingen:
``` cpp
int a = 3, b = 4;
float fa = a;
float x = fa/b; // jetzt wird x = 0.75 zugewiesen
```
Das lässt sich ohne die temporäre Variable eleganter schreiben, entweder in der „klassischen“ Cast-Notation (C-style cast)
``` cpp
float x = (float)a/b;
```
oder gleichwertig in der funktionalen Notation (function-style cast)
``` cpp
float x = float(a)/b;
```
Mehr in Kapitel 4

## Kontrollstrukturen

### If

``` cpp
if (a < b ) {
	cout << "A ist grösser als B\n";
} else if (a > b ) {
	cout << "A ist kleiner als B\n";
}else {
	cout << "Beide sind gleich gross\n";
}
```

**Kurzform**

`Bedingung ? Ausdruck1: Ausdruck2`

Bei True trifft Ausdruck1 ein, sonst Ausdruck2

``` cpp
int max = (wert1 > wert2) ? wert1 : wert2;
```

### Switch

``` cpp
int main()
{
    int x = 2;
    switch (x) {
    case 1:
        cout << "Choice is 1";
        break;
    case 2:
        cout << "Choice is 2";
        break;
    case 3:
        cout << "Choice is 3";
        break;
    default:
        cout << "Choice other than 1, 2 and 3";
        break;
    }
    return 0;
}
}
```

1) The expression provided in the switch should result in a *constant* value otherwise it would not be valid. Some valid expressions for switch case will be,

2) Duplicate case values are not allowed.

3) The *default statement is optional*. Even if the switch case statement do not have a default statement, 
it would run without any problem.

4) The *break statement is used inside the switch to terminate a statement* sequence. When a break statement is reached, the switch terminates, and the flow of control jumps to the next line following the switch statement.

5) The *break statement is optional*. If omitted, execution will continue on into the next case. The flow of control will fall through to subsequent cases until a break is reached.

6) *Nesting of switch statements is allowed*, which means you can have switch statements inside another switch. However nested switch statements should be avoided as it makes the program more complex and less readable. 

7) Switch statements are *limited to integer* values only in the check condition.


### While

``` cpp
int main()
{
  
    int i = 5;
  
    while (i < 10) {
        i++;
        cout << "GFG\n";
    }
  
    return 0;
}
```
Bedingung wird zuerst geprüft

### Do While

``` cpp
do
{
    statements..
}
while (condition);
```
Bedingung wird nacher überprüft

### For

``` cpp
int main()
{
  
    int i = 0;
  
    for (i = 5; i < 10; i++) {
        cout << "GFG\n";
    }
  
    return 0;
}
```

**Range-based**

``` 
for ( range_declaration : range_expression ) 
    loop_statement

Parameters :
range_declaration : 
a declaration of a named variable, whose type is the 
type of the element of the sequence represented by 
range_expression, or a reference to that type.
Often uses the auto specifier for automatic type 
deduction.

range_expression : 
any expression that represents a suitable sequence 
or a braced-init-list.

loop_statement : 
any statement, typically a compound statement, which
is the body of the loop.
```

``` cpp
#include <iostream>
#include <vector>
#include <map>
  
//Driver
int main() 
{
    // Iterating over whole array
    std::vector<int> v = {0, 1, 2, 3, 4, 5};
    for (auto i : v)
        std::cout << i << ' ';
      
    std::cout << '\n';
      
    // the initializer may be a braced-init-list
    for (int n : {0, 1, 2, 3, 4, 5})
        std::cout << n << ' ';
      
    std::cout << '\n';
   
    // Iterating over array
    int a[] = {0, 1, 2, 3, 4, 5};     
    for (int n : a)
        std::cout << n << ' ';
      
    std::cout << '\n';
      
    // Just running a loop for every array
    // element
    for (int n : a)  
        std::cout << "In loop" << ' ';
      
    std::cout << '\n';
      
    // Printing string characters
    std::string str = "Geeks";
    for (char c : str) 
        std::cout << c << ' ';
          
    std::cout << '\n';
  
    // Printing keys and values of a map
    std::map <int, int> MAP({{1, 1}, {2, 2}, {3, 3}});
    for (auto i : MAP)
        std::cout << '{' << i.first << ", " 
                  << i.second << "}\n";
}
```
### Sprunganweisungen
Break springt aus Loop,
Continue macht mit nächster Iteration weiter


## Arrays und Strings

### Vector

Dynamisches Array mit flexibler Grösse

Elemente sind hintereinander im Speicher, bei Einschub in Mitte werden alle Elemente "nach rechts geschoben" -> Rechenaufwand!

``` cpp
std::vector<int> vec (6);   // Vektor mit Länge von 6
                            //Standardwerte der 6 Elemente sind 0
vec[0] = 11;                //Wert an Stelle 0 zuweisen
```

**Simple Iteration:**

``` cpp
for (auto element : vec) {
    std::cout << element << "\n";
}
```

Änderungen an `element` haben keine Auswirkungen auf das Element, ausser es wird so genutzt: `for (auto &element : vec)`

**Iterationsfunktionen:**

1. begin() – Returns an iterator pointing to the first element in the vector
2. end() – Returns an iterator pointing to the theoretical element that follows the last element in the vector
3. rbegin() – Returns a reverse iterator pointing to the last element in the vector (reverse beginning). It moves from last to first element
4. rend() – Returns a reverse iterator pointing to the theoretical element preceding the first element in the vector (considered as reverse end)
5. cbegin() – Returns a constant iterator pointing to the first element in the vector.
6. cend() – Returns a constant iterator pointing to the theoretical element that follows the last element in the vector.
7. crbegin() – Returns a constant reverse iterator pointing to the last element in the vector (reverse beginning). It moves from last to first element
8. crend() – Returns a constant reverse iterator pointing to the theoretical element preceding the first element in the vector (considered as reverse end)

``` cpp
#include <iostream>
#include <vector>
  
using namespace std;
  
int main()
{
    vector<int> g1;
  
    for (int i = 1; i <= 5; i++)
        g1.push_back(i);
  
    cout << "Output of begin and end: ";
    for (auto i = g1.begin(); i != g1.end(); ++i)
        cout << *i << " ";
  
    cout << "\nOutput of cbegin and cend: ";
    for (auto i = g1.cbegin(); i != g1.cend(); ++i)
        cout << *i << " ";
  
    cout << "\nOutput of rbegin and rend: ";
    for (auto ir = g1.rbegin(); ir != g1.rend(); ++ir)
        cout << *ir << " ";
  
    cout << "\nOutput of crbegin and crend : ";
    for (auto ir = g1.crbegin(); ir != g1.crend(); ++ir)
        cout << *ir << " ";
  
    return 0;
}
```

```
Output:

Output of begin and end: 1 2 3 4 5 
Output of cbegin and cend: 1 2 3 4 5 
Output of rbegin and rend: 5 4 3 2 1 
Output of crbegin and crend : 5 4 3 2 1
```

**Kapazität**

1. size() – Returns the number of elements in the vector.
2. max_size() – Returns the maximum number of elements that the vector can hold.
3. capacity() – Returns the size of the storage space currently allocated to the vector expressed as number of elements.
4. resize(n) – Resizes the container so that it contains ‘n’ elements.
5. empty() – Returns whether the container is empty.
6. shrink_to_fit() – Reduces the capacity of the container to fit its size and destroys all elements beyond the capacity.
7. reserve() – Requests that the vector capacity be at least enough to contain n elements.

``` cpp
#include <iostream>
#include <vector>
  
using namespace std;
  
int main()
{
    vector<int> g1;
  
    for (int i = 1; i <= 5; i++)
        g1.push_back(i);
  
    cout << "Size : " << g1.size();
    cout << "\nCapacity : " << g1.capacity();
    cout << "\nMax_Size : " << g1.max_size();
  
    // resizes the vector size to 4
    g1.resize(4);
  
    // prints the vector size after resize()
    cout << "\nSize : " << g1.size();
  
    // checks if the vector is empty or not
    if (g1.empty() == false)
        cout << "\nVector is not empty";
    else
        cout << "\nVector is empty";
  
    // Shrinks the vector
    g1.shrink_to_fit();
    cout << "\nVector elements are: ";
    for (auto it = g1.begin(); it != g1.end(); it++)
        cout << *it << " ";
  
    return 0;
}
```
```
Output:
Size : 5
Capacity : 8
Max_Size : 4611686018427387903
Size : 4
Vector is not empty
Vector elements are: 1 2 3 4
```
**Elemntzugriff**
1. reference operator [g] – Returns a reference to the element at position ‘g’ in the vector
2. at(g) – Returns a reference to the element at position ‘g’ in the vector
3. front() – Returns a reference to the first element in the vector
4. back() – Returns a reference to the last element in the vector
5. data() – Returns a direct pointer to the memory array used internally by the vector to store its owned elements.

``` cpp
#include <bits/stdc++.h>
using namespace std;
  
int main()
{
    vector<int> g1;
  
    for (int i = 1; i <= 10; i++)
        g1.push_back(i * 10);
  
    cout << "\nReference operator [g] : g1[2] = " << g1[2];
  
    cout << "\nat : g1.at(4) = " << g1.at(4);
  
    cout << "\nfront() : g1.front() = " << g1.front();
  
    cout << "\nback() : g1.back() = " << g1.back();
  
    // pointer to the first element
    int* pos = g1.data();
  
    cout << "\nThe first element is " << *pos;
    return 0;
}
```
```
Output:
Reference operator [g] : g1[2] = 30
at : g1.at(4) = 50
front() : g1.front() = 10
back() : g1.back() = 100
The first element is 10
```
**Modifiers:**

1. assign() – It assigns new value to the vector elements by replacing old ones
2. push_back() – It push the elements into a vector from the back
3. pop_back() – It is used to pop or remove elements from a vector from the back.
4. insert() – It inserts new elements before the element at the specified position
5. erase() – It is used to remove elements from a container from the specified position or range.
6. swap() – It is used to swap the contents of one vector with another vector of same type. Sizes may differ.
7. clear() – It is used to remove all the elements of the vector container
8. emplace() – It extends the container by inserting new element at position
9. emplace_back() – It is used to insert a new element into the vector container, the new element is added to the end of the vector

``` cpp
#include <bits/stdc++.h>
#include <vector>
using namespace std;
  
int main()
{
    // Assign vector
    vector<int> v;
  
    // fill the array with 10 five times
    v.assign(5, 10);
  
    cout << "The vector elements are: ";
    for (int i = 0; i < v.size(); i++)
        cout << v[i] << " ";
  
    // inserts 15 to the last position
    v.push_back(15);
    int n = v.size();
    cout << "\nThe last element is: " << v[n - 1];
  
    // removes last element
    v.pop_back();
  
    // prints the vector
    cout << "\nThe vector elements are: ";
    for (int i = 0; i < v.size(); i++)
        cout << v[i] << " ";
  
    // inserts 5 at the beginning
    v.insert(v.begin(), 5);
  
    cout << "\nThe first element is: " << v[0];
  
    // removes the first element
    v.erase(v.begin());
  
    cout << "\nThe first element is: " << v[0];
  
    // inserts at the beginning
    v.emplace(v.begin(), 5);
    cout << "\nThe first element is: " << v[0];
  
    // Inserts 20 at the end
    v.emplace_back(20);
    n = v.size();
    cout << "\nThe last element is: " << v[n - 1];
  
    // erases the vector
    v.clear();
    cout << "\nVector size after erase(): " << v.size();
  
    // two vector to perform swap
    vector<int> v1, v2;
    v1.push_back(1);
    v1.push_back(2);
    v2.push_back(3);
    v2.push_back(4);
  
    cout << "\n\nVector 1: ";
    for (int i = 0; i < v1.size(); i++)
        cout << v1[i] << " ";
  
    cout << "\nVector 2: ";
    for (int i = 0; i < v2.size(); i++)
        cout << v2[i] << " ";
  
    // Swaps v1 and v2
    v1.swap(v2);
  
    cout << "\nAfter Swap \nVector 1: ";
    for (int i = 0; i < v1.size(); i++)
        cout << v1[i] << " ";
  
    cout << "\nVector 2: ";
    for (int i = 0; i < v2.size(); i++)
        cout << v2[i] << " ";
}
```
```
The vector elements are: 10 10 10 10 10 
The last element is: 15
The vector elements are: 10 10 10 10 10 
The first element is: 5
The first element is: 10
The first element is: 5
The last element is: 20
Vector size after erase(): 0

Vector 1: 1 2 
Vector 2: 3 4 
After Swap 
Vector 1: 3 4 
Vector 2: 1 2
```

### C-Array

Statische Anzahl Elemente, Arbeit mit rohem Speicher

``` cpp
// Array declaration by specifying size
int arr1[10];
  
// With recent C/C++ versions, we can also
// declare an array of user specified size
int n = 10;
int arr2[n];

// Array declaration by initializing elements
int arr[] = { 10, 20, 30, 40 }
  
// Compiler creates an array of size 4.
// above is same as  "int arr[4] = {10, 20, 30, 40}"

// Array declaration by specifying size and initializing
// elements
int arr[6] = { 10, 20, 30, 40 }
  
// Compiler creates an array of size 6, initializes first
// 4 elements as specified by user and rest two elements as
// 0. above is same as  "int arr[] = {10, 20, 30, 40, 0, 0}"


//Accessing Elements
double element = arr[9];

//_____________________________EXAMPLE_______________________________________
int main () {

   int n[ 10 ]; /* n is an array of 10 integers */
   int i,j;
 
   /* initialize elements of array n to 0 */         
   for ( i = 0; i < 10; i++ ) {
      n[ i ] = i + 100; /* set element at location i to i + 100 */
   }
   
   /* output each array element's value */
   for (j = 0; j < 10; j++ ) {
      printf("Element[%d] = %d\n", j, n[j] );
   }
 
   return 0;
}

//Two Dimensional
type arrayName [ x ][ y ];

int a[3][4] = {  
   {0, 1, 2, 3} ,   /*  initializers for row indexed by 0 */
   {4, 5, 6, 7} ,   /*  initializers for row indexed by 1 */
   {8, 9, 10, 11}   /*  initializers for row indexed by 2 */
};
//The nested braces, which indicate the intended row, are optional. The following initialization is equivalent to the previous example −

int a[3][4] = {0,1,2,3,4,5,6,7,8,9,10,11};  //Zuerst alle Elemente erste Zeile, etc.

//access
int val = a[2][3];

int main () {

   /* an array with 5 rows and 2 columns*/
   int a[5][2] = { {0,0}, {1,2}, {2,4}, {3,6},{4,8}};
   int i, j;
 
   /* output each array element's value */
   for ( i = 0; i < 5; i++ ) {

      for ( j = 0; j < 2; j++ ) {
         printf("a[%d][%d] = %d\n", i,j, a[i][j] );
      }
   }
   
   return 0;
}

//Output
a[0][0]: 0
a[0][1]: 0
a[1][0]: 1
a[1][1]: 2
a[2][0]: 2
a[2][1]: 4
a[3][0]: 3
a[3][1]: 6
a[4][0]: 4
a[4][1]: 8

//Pass Array to function
//Way-1 Formal parameters as a pointer −

void myFunction(int *param) {
   .
   .
   .
}

//Way-2 Formal parameters as a sized array −

void myFunction(int param[10]) {
   .
   .
   .
}
//Way-3 Formal parameters as an unsized array −

void myFunction(int param[]) {
   .
   .
   .
}

//Example of usage
double getAverage(int arr[], int size) {

   int i;
   double avg;
   double sum = 0;

   for (i = 0; i < size; ++i) {
      sum += arr[i];
   }

   avg = sum / size;

   return avg;
}
/* function declaration */
double getAverage(int arr[], int size);

int main () {

   /* an int array with 5 elements */
   int balance[5] = {1000, 2, 3, 17, 50};
   double avg;

   /* pass pointer to the array as an argument */
   avg = getAverage( balance, 5 ) ;
 
   /* output the returned value */
   printf( "Average value is: %f ", avg );
    
   return 0;
}

```

**Advantages of an Array in C/C++:**

* Random access of elements using array index.
* Use of fewer line of code as it creates a single array of multiple elements.
* Easy access to all the elements.
* Traversal through the array becomes easy using a single loop.
* Sorting becomes easy as it can be accomplished by writing fewer line of code.

**Disadvantages of an Array in C/C++:** 

* Allows a fixed number of elements to be entered which is decided at the time of declaration. Unlike a linked list, an array in C is not dynamic.
* Insertion and deletion of elements can be costly since the elements are needed to be managed in accordance with the new memory allocation.

**Facts about Array in C/C++:**

* Accessing Array Elements: 
Array elements are accessed by using an integer index. Array index starts with 0 and goes till size of array minus 1.
* Name of the array is also a pointer to the first element of array.

-> Mehr in Kapitel 6.2.1

### Strings in C++

Strings sind Zeichenketten
`std::string`


``` cpp
#include <bits/stdc++.h>
using namespace std;
  
int main()
{
    // various constructor of string class
  
    // initialization by raw string
    string str1("first string");
  
    // initialization by another string
    string str2(str1);
  
    // initialization by character with number of occurrence
    string str3(5, '#');
  
    // initialization by part of another string
    string str4(str1, 6, 6); //    from 6th index (second parameter)
                             // 6 characters (third parameter)
  
    // initialization by part of another string : iterator version
    string str5(str2.begin(), str2.begin() + 5);
  
    cout << str1 << endl;
    cout << str2 << endl;
    cout << str3 << endl;
    cout << str4 << endl;
    cout << str5 << endl;
  
    //  assignment operator
    string str6 = str4;
  
    // clear function deletes all character from string
    str4.clear();
  
    //  both size() and length() return length of string and
    //  they work as synonyms
    int len = str6.length(); // Same as "len = str6.size();"
  
    cout << "Length of string is : " << len << endl;
  
    // a particular character can be accessed using at /
    // [] operator
    char ch = str6.at(2); //  Same as "ch = str6[2];"
  
  
    cout << "third character of string is : " << ch << endl;
  
    //  front return first character and back returns last character
    //  of string
  
    char ch_f = str6.front();  // Same as "ch_f = str6[0];"
    char ch_b = str6.back();   // Same as below
                               // "ch_b = str6[str6.length() - 1];"
  
    cout << "First char is : " << ch_f << ", Last char is : "
         << ch_b << endl;
  
    // c_str returns null terminated char array version of string
    const char* charstr = str6.c_str();
    printf("%s\n", charstr);
  
    // append add the argument string at the end
    str6.append(" extension");
    //  same as str6 += " extension"
  
    // another version of append, which appends part of other
    // string
    str4.append(str6, 0, 6);  // at 0th position 6 character
  
    cout << str6 << endl;
    cout << str4 << endl;
  
    //  find returns index where pattern is found.
    //  If pattern is not there it returns predefined
    //  constant npos whose value is -1
  
    if (str6.find(str4) != string::npos)
        cout << "str4 found in str6 at " << str6.find(str4)
             << " pos" << endl;
    else
        cout << "str4 not found in str6" << endl;
  
    //  substr(a, b) function returns a substring of b length
    //  starting from index a
    cout << str6.substr(7, 3) << endl;
  
    //  if second argument is not passed, string till end is
    // taken as substring
    cout << str6.substr(7) << endl;
  
    //  erase(a, b) deletes b characters at index a
    str6.erase(7, 4);
    cout << str6 << endl;
  
    //  iterator version of erase
    str6.erase(str6.begin() + 5, str6.end() - 3);
    cout << str6 << endl;
  
    str6 = "This is a examples";
  
    //  replace(a, b, str)  replaces b characters from a index by str
    str6.replace(2, 7, "ese are test");
  
    cout << str6 << endl;
  
    return 0;
}
```
```
Output :

first string
first string
#####
string
first
Length of string is : 6
third character of string is : r
First char is : s, Last char is : g
string
string extension
string
str4 found in str6 at 0 pos
ext
extension
string nsion
strinion
These are test examples
```

**Beispielapplikationen:**

``` cpp
#include <bits/stdc++.h>
using namespace std;
  
// this function returns floating point part of a number-string
string returnFloatingPart(string str)
{
    int pos = str.find(".");
    if (pos == string::npos)
        return "";
    else
        return str.substr(pos + 1);
}
  
// This function checks whether a string contains all digit or not
bool containsOnlyDigit(string str)
{
    int l = str.length();
    for (int i = 0; i < l; i++)
    {
        if (str.at(i) < '0' || str.at(i) > '9')
            return false;
    }
    //  if we reach here all character are digits
    return true;
}
  
// this function replaces all single space by %20
// Used in URLS
string replaceBlankWith20(string str)
{
    string replaceby = "%20";
    int n = 0;
  
    // loop till all space are replaced
    while ((n = str.find(" ", n)) != string::npos )
    {
        str.replace(n, 1, replaceby);
        n += replaceby.length();
    }
    return str;
}
  
// driver function to check above methods
int main()
{
    string fnum = "23.342";
    cout << "Floating part is : " << returnFloatingPart(fnum) 
         << endl;
  
    string num = "3452";
    if (containsOnlyDigit(num))
        cout << "string contains only digit" << endl;
  
    string urlex = "google com in";
    cout << replaceBlankWith20(urlex) << endl;
  
    return 0;      
}
```
```
Floating part is : 342
string contains only digit
google%20com%20in
```
### C-Strings

Am Ende muss der Terminator `\0` sein!

``` cpp
char str[4] = "GfG"; /*One extra for string terminator*/
/*    OR    */
char str[4] = {‘G’, ‘f’, ‘G’, '\0'}; /* '\0' is string terminator */
```
Strings using character pointers 
Using character pointer strings can be stored in two ways:

1) Read only string in a shared segment. 
When a string value is directly assigned to a pointer, in most of the compilers, it’s stored in a read-only block (generally in data segment) that is shared among functions. 

``` cpp
char *str  =  "GfG";  
```
In the above line “GfG” is stored in a shared read-only location, but pointer str is stored in a read-write memory. You can change str to point something else but cannot change value at present str. So this kind of string should only be used when we don’t want to modify string at a later stage in the program.

2) Dynamically allocated in heap segment. 

Strings are stored like other dynamically allocated things in C and can be shared among functions. 

``` cpp
char *str;
int size = 4; /*one extra for ‘\0’*/
str = (char *)malloc(sizeof(char)*size);
*(str+0) = 'G'; 
*(str+1) = 'f';  
*(str+2) = 'G';  
*(str+3) = '\0';  
```
Let us see some examples to better understand the above ways to store strings.

``` cpp
//Example 1 (Try to modify string) 
//The below program may crash (gives segmentation fault error) because the line *(str+1) = ‘n’ tries to write a read only memory. 
int main()
{
 char *str; 
 str = "GfG";     /* Stored in read only part of data segment */
 *(str+1) = 'n'; /* Problem:  trying to modify read only memory */
 getchar();
 return 0;
}
//The below program works perfectly fine as str[] is stored in writable stack segment. 
int main()
{
 char str[] = "GfG";  /* Stored in stack segment like other auto variables */
 *(str+1) = 'n';   /* No problem: String is now GnG */
 getchar();
 return 0;
}
//Below program also works perfectly fine as data at str is stored in writable heap segment. 
int main()
{
  int size = 4;
  
  /* Stored in heap segment like other dynamically allocated things */
  char *str = (char *)malloc(sizeof(char)*size);
  *(str+0) = 'G'; 
  *(str+1) = 'f';  
  *(str+2) = 'G';    
  *(str+3) = '\0';  
  *(str+1) = 'n';  /* No problem: String is now GnG */
   getchar();
   return 0;
}   

```

``` cpp
//Example 2 (Try to return string from a function) 
//The below program works perfectly fine as the string is stored in a shared segment and data stored remains there even after return of getString() 
char *getString()
{
  char *str = "GfG"; /* Stored in read only part of shared segment */
  
  /* No problem: remains at address str after getString() returns*/
  return str;  
}     
  
int main()
{
  printf("%s", getString());  
  getchar();
  return 0;
}
//The below program also works perfectly fine as the string is stored in heap segment and data stored in heap segment persists even after the return of getString()  
char *getString()
{
  int size = 4;
  char *str = (char *)malloc(sizeof(char)*size); /*Stored in heap segment*/
  *(str+0) = 'G'; 
  *(str+1) = 'f';  
  *(str+2) = 'G';
  *(str+3) = '\0';  
    
  /* No problem: string remains at str after getString() returns */    
  return str;  
}     
int main()
{
  printf("%s", getString());  
  getchar();
  return 0;
}
//But, the below program may print some garbage data as string is stored in stack frame of function getString() and data may not be there after getString() returns. 
char *getString()
{
  char str[] = "GfG"; /* Stored in stack segment */
  
  /* Problem: string may not be present after getString() returns */
  /* Problem can be solved if write static before char, i.e. static char str[] = "GfG";*/
  return str; 
}     
int main()
{
  printf("%s", getString());  
  getchar();
  return 0;
}


//Pointer Magic with Arrays
double balance[50];
//balance is a pointer to &balance[0], which is the address of the first element of the array balance
//Thus, the following program fragment assigns p as the address of the first element of balance −

double *p;
double balance[10];

p = balance;
//It is legal to use array names as constant pointers, and vice versa. Therefore, *(balance + 4) is a legitimate way of accessing the data at balance[4].
//Once you store the address of the first element in 'p', you can access the array elements using *p, *(p+1), *(p+2) and so on. Given below is the example to show all the concepts discussed above −

int main () {

   /* an array with 5 elements */
   double balance[5] = {1000.0, 2.0, 3.4, 17.0, 50.0};
   double *p;
   int i;

   p = balance;
 
   /* output each array element's value */
   printf( "Array values using pointer\n");
	
   for ( i = 0; i < 5; i++ ) {
      printf("*(p + %d) : %f\n",  i, *(p + i) );
   }

   printf( "Array values using balance as address\n");
	
   for ( i = 0; i < 5; i++ ) {
      printf("*(balance + %d) : %f\n",  i, *(balance + i) );
   }
 
   return 0;
}

//Output:
Array values using pointer
*(p + 0) : 1000.000000
*(p + 1) : 2.000000
*(p + 2) : 3.400000
*(p + 3) : 17.000000
*(p + 4) : 50.000000
Array values using balance as address
*(balance + 0) : 1000.000000
*(balance + 1) : 2.000000
*(balance + 2) : 3.400000
*(balance + 3) : 17.000000
*(balance + 4) : 50.000000
```

## Referenzen und Zeiger

Unterschied: Referenzen zeigen auf Objekte, Pointer zeigen auf dessen Adressen!

### Referenzen
Alias für ein Speicherobjekt 


``` cpp
//Leerzeichen können beliebig gesetzt werden:
int x = 10;

int &ref = x;
int& ref = x;
int &ref = {x};
int &ref {x};

int main()
{
  int x = 10;
 
  // ref is a reference to x.
  int& ref = x;
 
  // Value of x is now changed to 20
  ref = 20;
  cout << "x = " << x << '\n';
 
  // Value of x is now changed to 30
  x = 30;
  cout << "ref = " << ref << '\n';
 
  return 0;
}
```
```
x = 20
ref = 30
```
Ist die Referenz an ein Objekt gebunden, verändert die Anpassung der Referenz auch das Objekt!
``` cpp
int var = 100;
int othervar = 200;

int& ref1 = var;
int& ref2 {var};

ref1 = othervar;    //ref1 und damit auch var wird auf 200 geändert
```
### Zeiger

Rohe Pointer nur verwenden, wenn es sein muss!
Repräsentieren Datentyp und Adresse eines Speicherobjekts `datentyp *name`

Leerzeichen vor und nach dem Stern sind egal!
Achtung, der Zeigertyp muss vom selben Datentyp sein, wie das Objekt

**Zuweisung**
``` cpp

int var = 123;
int *ptr = &var;    //Zeiger prt zeigt auf var
```
Der Adressoperator & ermittelt die Adresse eines Speicherobjekts

Variable | Adresse | Wert
|---|---|---|
|int var|0x19F934|123|
|int* ptr|0x19F928|0x19F934|

Der Pointer ist Separat abgelegt (eigene Speicheradresse) und zeigt auf die Adresse der Variable

-> Indirekter Zugriff auf den Wert der Variable

``` cpp
int var = 123;
int* ptr = &var;                                    //Adresse von var zuweisen
cout << "Adresse von var : " << &var << "\n";       //Adresse der Variable
cout << "ptr verweist auf : " << ptr << "\n";       //Adresse auf die Pointer zeigt
cout << "Adresse von ptr : " << &ptr << "\n";       //Adresse der Pointers
cout << "Wert von var : " << *ptr << "\n";          //Wert auf den Pointer zeigt
```
```
Adresse von var : 0x7ffe017db27c
ptr verweist auf : 0x7ffe017db27c
Adresse von ptr : 0x7ffe017db280
Wert von var: 123
```
**Dereferenzierung**

Zugriff auf Wert auf den Pointer zeigt mit `*ptr`


**Nullpointer**

Zeiger die nicht direkt auf Veriable zeigend erstellt werden zeigen auf einen zufälligen Wert im Speicher, Nullpointer zeigen ins Leere

``` cpp
char* ptr = nullptr;    //Wird als Nullpointer erzeugt
int *ptr;               //Zufälliger zugewiesener Wert
```
Überprüfung des Zeigers

``` cpp
if (ptr == nullptr) {
cout << "Ich zeige ins Nichts!\n"
}
```

```cpp
#include <iostream>
using namespace std;
 
int main()
{
    // A normal integer variable
    int Var = 10;
 
    // A pointer variable that holds address of var.
    int *ptr = &Var;
 
    // This line prints value at address stored in ptr.
    // Value stored is value of variable "var"
    cout << "Value of Var = "<< *ptr << endl;
 
    // The output of this line may be different in different
    // runs even on same machine.
    cout << "Address of Var = " <<  ptr << endl;
 
    // We can also use ptr as lvalue (Left hand
    // side of assignment)
    *ptr = 20; // Value at address is now 20
 
    // This prints 20
    cout << "After doing *ptr = 20, *ptr is "<< *ptr << endl;
 
    return 0;
}
```
```
Output : 
Value of Var = 10
Address of Var = 0x7fffa057dd4
After doing *ptr = 20, *ptr is 20
```
**Mathe mit Pointern:**

Nur in einem Array anwenden!

* incremented ( ++ )
* decremented ( — )
* an integer may be added to a pointer ( + or += )
* an integer may be subtracted from a pointer ( – or -= )

Pointers contain addresses. Adding two addresses makes no sense, because there is no idea what it would point to. 
*Subtracting* two addresses lets you compute the offset between these two addresses.


``` cpp
#include <bits/stdc++.h>
 
// Driver program
int main()
{
    // Declare an array
    int v[3] = {10, 100, 200};
 
    // Declare pointer variable
    int *ptr;
 
    // Assign the address of v[0] to ptr
    ptr = v;
 
    for (int i = 0; i < 3; i++)
    {
        printf("Value of *ptr = %d\n", *ptr);
        printf("Value of ptr = %p\n\n", ptr);
 
        // Increment pointer ptr by 1
        ptr++;
    }
}
```
```
Output:Value of *ptr = 10
Value of ptr = 0x7ffcae30c710

Value of *ptr = 100
Value of ptr = 0x7ffcae30c714

Value of *ptr = 200
Value of ptr = 0x7ffcae30c718
```

An array name acts like a pointer constant. The value of this pointer constant is the address of the first element. 
For example, if we have an array named val then val and &val[0] can be used interchangeably. 


`int nums[2][3]  =  { {16, 18, 20}, {25, 26, 27} };`

In general, nums[i][j] is equivalent to *(*(nums+i)+j)

Pointer Notation	|Array Notation|	Value
---|---|---
*(*nums)	|nums[0][0]|	16
*(*nums + 1)	|nums[0][1]|	18
*(*nums + 2)	|nums[0][2]	|20
*(*(nums + 1))	|nums[1][0]	|25
*(*(nums + 1) + 1)	|nums[1][1]	|26
*(*(nums + 1) + 2)	|nums[1][2]	|27

## Funktionen

### Definition

`[Spezfizierer] <Datentyp> <Funktionsname> ( [Parameter] ) {//Anweisungen}`

Aufrufen mit `funktionsname([Parameter])`

Wichtig, wenn ein Rückgabetyp definiert ist, die Rückgabe nicht vergessen!

Funktionsprototyp

``` cpp
int main()
{
   foo();           //Prototyp
   getchar();
   return 0;
}
void foo()          //Definition der Funktion
{
   printf("foo called");
}
```

### Parameter

Parameter werden nicht verändert, wenn sie nicht als Referenz übergeben werden!
```cpp
#include <iostream>
using namespace std;
  
void fun(int x) {
    x = 30;
}
  
int main() {
    int x = 20;
    fun(x);
    cout << "x = " << x;
    return 0;
}
```
**Konstante Funktionsparameter**

Die Parameter können auch noch via const unveränderlich gemacht werden `void addieren(const int value1, const int value2);`

**Standardparameter**

Funktionsparameter mit einem Wert vorbelegen, wenn Funktion ohne Parameter aufgerufen wird, werden diese verwendet.
Wichtig, nur die Parameter am Ende können gegeben sein und dann alle, Sprich nicht Param 1 angeben und 2 und 3 dann nicht!


``` cpp
#include <iostream>
using namespace std;
 
// A function with default arguments,
// it can be called with
// 2 arguments or 3 arguments or 4 arguments.
int sum(int x, int y, int z = 0, int w = 0)
{
    return (x + y + z + w);
}
 
// Driver Code
int main()
{
    // Statement 1
    cout << sum(10, 15) << endl;
   
    // Statement 2
    cout << sum(10, 15, 25) << endl;
   
    // Statement 3
    cout << sum(10, 15, 25, 30) << endl;
    return 0;
}
```
**Rückgabewert nutzen**

```cpp

int sum (int a, int b);
main() {
    int a = 10;
    int b = 20;
    sum = sum(a, b);

}
int sum(int a, int b) {
    sum = a + b;
    return sum;
}
```

### Funktionen überladen

Mehrere Funktionen mit demselben Namen verwenden, mit unterschiedlichen Parametern.

``` cpp

#include <iostream>
using namespace std;
 
void print(int i) {
  cout << " Here is int " << i << endl;
}
void print(double  f) {
  cout << " Here is float " << f << endl;
}
void print(char const *c) {
  cout << " Here is char* " << c << endl;
}
 
int main() {
  print(10);
  print(10.10);
  print("ten");
  return 0;
}
```

How  Function Overloading works?
* Exact match:- (Function name and Parameter)
* If a not exact match is found:
  * ->Char, Unsigned char, and short are promoted to an int.
  *  ->Float is promoted to double

* If no match found:
  * ->C++ tries to find a match through the standard conversion.

* ELSE ERROR 🙁

Der Rückgabetyp dient nicht der Unterscheidung, float sum() und int sum() sind für den Compiler identisch!

### Gültigkeit und Sichtbarkeit von Variabeln
Wenn innerhalb Anwendungsblock definiert, sind sie nur darin gültig.
```cpp
int foo;        // global variable

int some_function ()
{
  int bar;      // local variable
  bar = 0;
}

int other_function ()
{
  foo = 1;  // ok: foo is a global variable
  bar = 2;  // wrong: bar is not visible from this function
}
```

Wenn mehrere Variabeln gleich heissen, gewinnt die lokalste
``` cpp
// inner block scopes
#include <iostream>
using namespace std;

int main () {
  int x = 10;
  int y = 20;
  {
    int x;   // ok, inner scope.
    x = 50;  // sets value to inner x
    y = 50;  // sets value to (outer) y
    cout << "inner block:\n";
    cout << "x: " << x << '\n';
    cout << "y: " << y << '\n';
  }
  cout << "outer block:\n";
  cout << "x: " << x << '\n';
  cout << "y: " << y << '\n';
  return 0;
}
```

Zugriff auf Globale Variable mit `::variable`

### Referenzen als Parameter

Parameter werden beim Funktionsaufruf als Kopie mitgegeben, somit werden diese in der Funktion nicht verändert.



```cpp
void swap(int& a, int& b);
main() {
    int a = 1;
    int b = 2;

swap(a, b);
}

void swap(int& a, int& b) {
    int temp = a;
    a = b;
    b = temp;
}
```

Spart bei grossen Objekten auch Rechenzeit, da keine kopie erstellt werden muss.

Wenn eine Funktion die parameter als Referenz erhält, diese aber nicht ändern soll, werden Konstanten verwendet.

``` cpp
#include <iostream>
#include <string>
using namespace std;

void myfunction(const string& byconstreference)
{
     cout << "Arguments passed by const reference: " <<
     byconstreference;
}

int main()
{
    string s = "Hello World!";
    myfunction(s);
}
```

### Rückgabe von Referenzen

Das Referenzierte Objekt muss ausserhalb der Funktion existieren.

```cpp
#include <iostream>
#include <ctime>
 
using namespace std;
 
double vals[] = {10.1, 12.6, 33.1, 24.1, 50.0};
 
double& setValues( int i ) {
   return vals[i];   // return a reference to the ith element
}
 
// main function to call above defined function.
int main () {
 
   cout << "Value before change" << endl;
   for ( int i = 0; i < 5; i++ ) {
      cout << "vals[" << i << "] = ";
      cout << vals[i] << endl;
   }
 
   setValues(1) = 20.23; // change 2nd element
   setValues(3) = 70.8;  // change 4th element
 
   cout << "Value after change" << endl;
   for ( int i = 0; i < 5; i++ ) {
      cout << "vals[" << i << "] = ";
      cout << vals[i] << endl;
   }
   return 0;
}
```

```
Value before change
vals[0] = 10.1
vals[1] = 12.6
vals[2] = 33.1
vals[3] = 24.1
vals[4] = 50
Value after change
vals[0] = 10.1
vals[1] = 20.23
vals[2] = 33.1
vals[3] = 70.8
vals[4] = 50
```

### Zeiger als Parameter


```cpp

#include <iostream>
  
using namespace std;
  
int global_Var = 42;
  
// function to change pointer value
void changePointerValue(int* pp)
{
    pp = &global_Var;
}
  
int main()
{
    int var = 23;
    int* ptr_to_var = &var;
  
    cout << "Passing Pointer to function:" << endl;
  
    cout << "Before :" << *ptr_to_var << endl; // display 23
  
    changePointerValue(ptr_to_var);
  
    cout << "After :" << *ptr_to_var << endl; // display 23
  
    return 0;
}
```

Wichtig, als Parameter die Adresse nutzen und in der Funktion den Wert

## Modularisierung und Präprozessor

### Präprozessor Direktiven
Wird vor dem Compiler aktiv, fasst String Literale zusammen, entfernt Kommentare etc. 

Präprozessor Direktiven: 
* Header- und Quelldateien (#include) in den Quelltext kopieren
* symbolische Konstanten definieren (#define)
* bedingte Kompilierung steuern (#ifdef, #elseif)

### #include

Anweisung Quellcode aus anderer Datei einzufügen `#include datei`
Standard Headerdateien werden mit `#inclide <datei>` eingefügt, Bsp.: `#include <iostream>`

-> Dateipfade beachten!

### #define

Ersetzt Quelltext vor der Übersetzung durch andere Texte. Stumpfe Textersetzung

`#define PI 3.1415` definiert PI als Makro

-> Meist in Grossbuchstaben

Konstanten mit const oder constexpr oder enums sind besser und weniger fehleranfällig

Aufheben mit `#undef PI`

### Bedingte Kompilierung

Bedingungen um Quelltext für Compiler ein- und auszublenden.

Bsp. um Code auf mehreren Plattformen zu nutzen.

Schlüsselwort | Beschreibung
---|---
#if ausdruck | wird ausdruck erfüllt (!= 0) wird der folgende Dateinhalt behalten
#ifdef symbol | ist symbol definiert wird der folgende Dateinhalt behalten
#ifndef symbol | ist symbol *nicht* definiert wird der folgende Dateinhalt behalten
#endif | Zeigt das Ende der bedingten kompilierung

Mehrfaches Inkludieren vermeiden

```cpp
//myheader.h
#ifndef MYHEADER_H_     //Include Wächer
#define MYHEADER_H_
//Quellcode
#endif
```

Wenn mehree Headerdateien inkludiert werden, die wiederum andere Inkludieren kann das Kompilieren abgebrochen werden
-> Wächter einfügen!

### Modularisierung
Modul als Sammlung zusammengehöriger Quell- und Headerdateien. 

-> Moudule sollten selbstständig arbeiten!

**Aufteilung**

Privater und öffentlciher Bereich, wobei im öffentlichen die Schnittstellen sind. 

#### Header
endet auf .h oder .hpp

Element | Beispiel
---|---
Aufzählungen| `enumclass RBG {ROT, GRÜN, BLAU};`
bedingte Übersetzung| `#ifdef Bedingung`
Deklarationen von Bezeichnern| `class MyClass`
Funktionsdeklarationen| `int funktion(int *);`
#include Anweisungen| `#include <headeratei>`
Inline-funktionen (Definitionen)| `inline int quadrat(int v) {return v*v;}`
Kommentare| `//Blahblah`
Konstantendefinitionen|`constexpr PI = 3.1415;`
Makros |`#define BLOP 1234`
Namensräume |`namespace bereich {/* ... */}`
Templates (Definitionen) |`template<typename X> class Y {/* ... */};`
Templates (Deklarationen) |`template<typename X> class Y;`
Typdefinitionen |`struct Liste {int var; Liste* next;};`

Standard Header Files And Their Uses: 
 

* #include<stdio.h>: It is used to perform input and output operations using functions scanf() and printf().
* #include<iostream>: It is used as a stream of Input and Output using cin and cout.
* #include<string.h>: It is used to perform various functionalities related to string manipulation like strlen(), strcmp(), strcpy(), size(), etc.
* #include<math.h>: It is used to perform mathematical operations like sqrt(), log2(), pow(), etc.
* #include<iomanip.h>: It is used to access set() and setprecision() function to limit the decimal places in variables.
* #include<signal.h>: It is used to perform signal handling functions like signal() and raise().
* #include<stdarg.h>:It is used to perform standard argument functions like va_start() and va_arg(). It is also used to indicate start of the variable-length argument list and to fetch the arguments from the variable-length argument list in the program respectively.
* #include<errno.h>: It is used to perform error handling operations like errno(), strerror(), perror(), etc.
* #include<fstream.h>: It is used to control the data to read from a file as an input and data to write into the file as an output.
* #include<time.h>: It is used to perform functions related to date() and time() like setdate() and getdate(). It is also used to modify the system date and get the CPU time respectively.
* #include<float.h>: It contains a set of various platform-dependent constants related to floating point values. These constants are proposed by ANSI C. They allow making programs more portable. Some examples of constants included in this header file are- e(exponent), b(base/radix), etc.
* #include<limits.h>: It determines various properties of the various variable types. The macros defined in this header, limits the values of various variable types like char, int, and long. These limits specify that a variable cannot store any value beyond these limits, for example an unsigned character can store up to a maximum value of 255.
* #include<assert.h>: It contains information for adding diagnostics that aid program debugging.
* #include<ctype.h>: It contains function prototypes for functions that test characters for certain properties , and also function prototypes for functions that can be used to convert uppercase letters to lowercase letters and vice versa.
* #include<locale.h>: It contains function prototypes and other information that enables a program to be modified for the current locale on which it’s running. It enable sthe computer system to handle different conventions for expressing data such as times, dates or large numbers throughout the world.
* #include<setjmp.h>: It contains function prototypes for functions that allow bypassing of the usual function call and return sequence.
* #include<stddef.h>: It contains common type definitions used by C for performing calculations.

### Namensräume

Vermeiden Konflikte bei der Benennung und Gruppieren Elemente.

```cpp
namespace VIP {
    int var;
    void print() {
        std::cout << "var: " << var << "\n";
    }
}
```
Nuten mit qualifiziertem Namen `VIP::print()`

Importieren mit `using namespace std;` damit kann ohne Scope Operator aufgerufen werden. 

### Static

Variable bleibt während Dauer der Übersetzungseinheit erhalten. 
Wird der Wert in Funktion definiert, bleibt dieser nach Rücksprung erhalten -> Bsp counter() zählt wie oft Funktion aufgerufen wird mit der Variable count die increments in der Funktion hat. 1. Aufruf = 1, 2. Aufruf = 2 etc.
 
 ### Extern
 @ToDo

 ### constexpr
 Konstante zu Compilezeit erstellt

 ### const
 Konstante während Compilezeit erstellt (wartet bsp zuerst auf Userinput)

 ### Inline
 Statt Funktionsaufruf direkt der generierte Code einsetzen. Nur für simple Sachen.
```cpp
inline int square(int v) {return v*v;}
```

## Strukturen, Aufzählungen und dynamische Speicherobjekte

### Strukturen
Definieren einen neuen Datentyp
Ist weniger sicher als ein Objekt, da Public by default. 

-> Semikolon am Ende!

```cpp
struct Struktur {
    Typ1 Bezeichner1;
    Typ2 Bezeichner2;
    ...
    TypN BezeichnerN;
};
```
**Definieren, Elemente erzeugen und initialisieren**

```cpp
//Definieren
struct Artikel {
    inr nummer;             //Attribut
    string bezeichnung;
    int anzahl;
};

//Neuer Artikel erstellen
Artikel laptop{};                               //Leer initialisieren (int = 0 und Stings = "")
Artikel laptop = {1234, "Laptop 15 Zoll", 10};  //Mit Attributen initialisiert

//Zugriff
cout << laptop.nummer

//Element zuweisen
laptop.anzahl = 9;

//Struktur an Funktion übergeben
void print(const Artikel& laptop)
void print(const Artikel* laptop)

```
Strukturen können wie Strings nicht mit == verglichen werden, hier müssen die einzelnen Attribute verglichen werden.

### Enum

Legt für Datentyp fest, welche Werte er annehmen darf. Kann als Klasse oder Struktur erstellt werden.

```cpp
enum struct Ampel {ROT, GRÜN, GELB};

Ampel ampel{Ampel::ROT};    //Initialisierung
ampel = Ampel::GELB;

//Enum erweitern
enum struct Ampel {ROT, GRÜN, GELB, BLAU};
```
### using
Synonyme erstellen

```cpp
using Byte = unsigned char;
Byte byte = 'x';
//hier kann nun unsigned char, oder Byste verwendet werden
```
### Dynamische Speicherobjekte

System fordert soviel Speicher an, wie der angegebene Datentyp braucht.

For normal variables like “int a”, “char str[10]”, etc, memory is automatically allocated and deallocated. For dynamically allocated memory like “int *p = new int[10]”, it is programmers responsibility to deallocate memory when no longer needed. If programmer doesn’t deallocate memory, it causes memory leak (memory is not deallocated until program terminates). 

```cpp
// C++ program to illustrate dynamic allocation
// and deallocation of memory using new and delete
#include <iostream>
using namespace std;
 
int main ()
{
    // Pointer initialization to null
    int* p = NULL;
 
    // Request memory for the variable
    // using new operator
    p = new(nothrow) int;
    if (!p)
        cout << "allocation of memory failed\n";
    else
    {
        // Store value at allocated address
        *p = 29;
        cout << "Value of p: " << *p << endl;
    }
 
    // Request block of memory
    // using new operator
    float *r = new float(75.25);
 
    cout << "Value of r: " << *r << endl;
 
    // Request block of memory of size n
    int n = 5;
    int *q = new(nothrow) int[n];
 
    if (!q)
        cout << "allocation of memory failed\n";
    else
    {
        for (int i = 0; i < n; i++)
            q[i] = i+1;
 
        cout << "Value store in block of memory: ";
        for (int i = 0; i < n; i++)
            cout << q[i] << " ";
    }
 
    // freed the allocated memory
    delete p;
    delete r;
 
    // freed the block of allocated memory
    delete[] q;
 
    return 0;
}
```

```
Value of p: 29
Value of r: 75.25
Value store in block of memory: 1 2 3 4 5 
```
Allocate block of memory: new operator is also used to allocate a block(an array) of memory of type data-type. 

```cpp
//pointer-variable = new data-type[size];
 int *p = new int[10]
 //Dynamically allocates memory for 10 integers continuously of 
 //type int and returns pointer to the first element of the sequence, 
 //which is assigned to p(a pointer). p[0] refers to first element, p[1] refers to second element and so on. 
```
### Smart Pointer

Problems with Normal Pointers
Take a look at the code below.
```cpp
#include <iostream>
using namespace std;
 
class Rectangle {
private:
    int length;
    int breadth;
};
 
void fun()
{
    // By taking a pointer p and
    // dynamically creating object
    // of class rectangle
    Rectangle* p = new Rectangle();
}
 
int main()
{
    // Infinite Loop
    while (1) {
        fun();
    }
}
```
In function fun, it creates a pointer that is pointing to the Rectangle object. The object Rectangle contains two integers, length and breadth. When the function fun ends, p will be destroyed as it is a local variable. But, the memory it consumed won’t be deallocated because we forgot to use delete p; at the end of the function. That means the memory won’t be free to be used by other resources. But, we don’t need the variable anymore, but we need the memory.

In function main, fun is called in an infinite loop. That means it’ll keep creating p. It’ll allocate more and more memory but won’t free them as we didn’t deallocate it. The memory that’s wasted can’t be used again. Which is a memory leak. The entire heap memory may become useless for this reason. C++11 comes up with a solution to this problem, Smart Pointer.

As we’ve known unconsciously not deallocating a pointer causes a memory leak that may lead to crash of the program. Languages Java, C# has Garbage Collection Mechanisms to smartly deallocate unused memory to be used again. The programmer doesn’t have to worry about any memory leak. C++11 comes up with its own mechanism that’s Smart Pointer. When the object is destroyed it frees the memory as well. So, we don’t need to delete it as Smart Pointer does will handle it.

A Smart Pointer is a wrapper class over a pointer with an operator like * and -> overloaded. The objects of the smart pointer class look like normal pointers. But, unlike Normal Pointers it can deallocate and free destroyed object memory.

The idea is to take a class with a pointer, destructor and overloaded operators like * and ->. *Since the destructor is automatically called when an object goes out of scope*, the dynamically allocated memory would automatically be deleted (or reference count can be decremented). Consider the following simple SmartPtr class.

```cpp

#include <iostream>
using namespace std;
 
class SmartPtr {
    int* ptr; // Actual pointer
public:
    // Constructor: Refer https:// www.geeksforgeeks.org/g-fact-93/
    // for use of explicit keyword
    explicit SmartPtr(int* p = NULL) { ptr = p; }
 
    // Destructor
    ~SmartPtr() { delete (ptr); }
 
    // Overloading dereferencing operator
    int& operator*() { return *ptr; }
};
 
int main()
{
    SmartPtr ptr(new int());
    *ptr = 20;
    cout << *ptr;
 
    // We don't need to call delete ptr: when the object
    // ptr goes out of scope, the destructor for it is automatically
    // called and destructor does delete ptr.
 
    return 0;
}
```
This only works for int. So, we’ll have to create Smart Pointer for every object? No, there’s a solution, Template. In the code below as you can see T can be of any type. 



```cpp
#include <iostream>
using namespace std;
 
// A generic smart pointer class
template <class T>
class SmartPtr {
    T* ptr; // Actual pointer
public:
    // Constructor
    explicit SmartPtr(T* p = NULL) { ptr = p; }
 
    // Destructor
    ~SmartPtr() { delete (ptr); }
 
    // Overloading dereferencing operator
    T& operator*() { return *ptr; }
 
    // Overloading arrow operator so that
    // members of T can be accessed
    // like a pointer (useful if T represents
    // a class or struct or union type)
    T* operator->() { return ptr; }
};
 
int main()
{
    SmartPtr<int> ptr(new int());
    *ptr = 20;
    cout << *ptr;
    return 0;
}
```
Types of Smart Pointers
1. unique_ptr
unique_ptr stores one pointer only. We can assign a different object by removing the current object from the pointer. Notice the code below. First, the unique_pointer is pointing to P1. But, then we remove P1 and assign P2 so the pointer now points to P2.

```cpp
#include <iostream>
using namespace std;
#include <memory>
 
class Rectangle {
    int length;
    int breadth;
 
public:
    Rectangle(int l, int b){
        length = l;
        breadth = b;
    }
 
    int area(){
        return length * breadth;
    }
};
 
int main(){
 
    unique_ptr<Rectangle> P1(new Rectangle(10, 5));
    cout << P1->area() << endl; // This'll print 50
 
    // unique_ptr<Rectangle> P2(P1);
    unique_ptr<Rectangle> P2;
    P2 = move(P1);
 
    // This'll print 50
    cout << P2->area() << endl;
 
    // cout<<P1->area()<<endl;
    return 0;
}
Output: 
50
50
```
2. shared_ptr
By using shared_ptr more than one pointer can point to this one object at a time and it’ll maintain a Reference Counter using use_count() method. 

```cpp
#include <iostream>
using namespace std;
#include <memory>
 
class Rectangle {
    int length;
    int breadth;
 
public:
    Rectangle(int l, int b)
    {
        length = l;
        breadth = b;
    }
 
    int area()
    {
        return length * breadth;
    }
};
 
int main()
{
 
    shared_ptr<Rectangle> P1(new Rectangle(10, 5));
    // This'll print 50
    cout << P1->area() << endl;
 
    shared_ptr<Rectangle> P2;
    P2 = P1;
 
    // This'll print 50
    cout << P2->area() << endl;
 
    // This'll now not give an error,
    cout << P1->area() << endl;
 
    // This'll also print 50 now
    // This'll print 2 as Reference Counter is 2
    cout << P1.use_count() << endl;
    return 0;
}
Output: 
50
50
50
2
```
3. weak_ptr 
It’s much more similar to shared_ptr except it’ll not maintain a Reference Counter. In this case, a pointer will not have a stronghold on the object. The reason is if suppose pointers are holding the object and requesting for other objects then they may form a Deadlock. 

## Klassen

```cpp
class Klasse {
    //Blah
};
```

![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Classes-and-Objects-in-C.png)


### Zugriffskontrolle

Defaultemässig ist alles auf Private.


```cpp
#########class.h##################
class Class
{
    private:
        // data hidden from outside world
        int x;
          
    public:
        // function to set value of 
        // variable x
        void set(int a);
        // function to return value of
        // variable x
        int get();
};

#####class.cpp########
#include class.h
int Class::get() {
    return x;
}

void Class::set(int new_x) {
    x = new_x;
}
```

### Pfeiloperator
Zeiger auf instanzen von Klassen
Objekte zur Laufzeit dynamisch erzeugen
Verwendung von `std::unique_ptr`

```cpp
#include <iostream>
 
using namespace std;

class Box {
   public:
      // Constructor definition
      Box(double l = 2.0, double b = 2.0, double h = 2.0) {
         cout <<"Constructor called." << endl;
         length = l;
         breadth = b;
         height = h;
      }
      double Volume() {
         return length * breadth * height;
      }
      
   private:
      double length;     // Length of a box
      double breadth;    // Breadth of a box
      double height;     // Height of a box
};

int main(void) {
   Box Box1(3.3, 1.2, 1.5);    // Declare box1
   Box Box2(8.5, 6.0, 2.0);    // Declare box2
   Box *ptrBox;                // Declare pointer to a class.

   // Save the address of first object
   ptrBox = &Box1;

   // Now try to access a member using member access operator
   cout << "Volume of Box1: " << ptrBox->Volume() << endl;

   // Save the address of second object
   ptrBox = &Box2;

   // Now try to access a member using member access operator
   cout << "Volume of Box2: " << ptrBox->Volume() << endl;
  
   return 0;
}
```
```cpp
//Dynamisch Speicher für neues Objekt anfordern und indirekt darauf zugreifen
#include <memory>       //für std::unique_ptr
//Speicher für neues Objekt anfordern
std::unique_ptr<Konto> konto_ptr1 = std::make_unique<Konto>();
konto_ptr1->print();

//Varante2
auto konto_ptr2 = std::make_unique<Konto>();
konto_ptr2->set_name("Gehalt");
konto_ptr2->print();
```

### Konstruktoren

* selber Name wie Klasse
* kein Rückgabewert
* Public!

```cpp
//Deklaration in Konto.h
class Konto {
    public:
        //Mehrere Konstruktoren
        Konto();
        Konto(long s, string n);
        Konto(long s);
        Konto(string n);
    private:
        //Attribute
        long stand = 0;
        string name = "Unbekannt";
};

//Definition in Konto.cpp
Klassenname::Klassenname( Typ bezeichner1, Typ bezeichner2)
: attribut1{ausdruck1}, attribut2{ausdruck2}                //Elementinitialisierer
{
    //Anweisungen
}

#include "konto.h"

Konto::Konto() {}                         //Kann auch auf einer Zeile sein
Konto::Konto(long s, string n)
: stand{s}, name{n} {}
Konto::Konto(long s) : stand{s} {}
Konto::Konto(string n) : name{n} {}

//Initialisierung
Konto newKonto{11257, "Brieftasche"}
```
### Copy Konstruktor

Existierendes Objekt als Vorlage für eine neue Instanzierung

```cpp
Konto konto01{200000. "Festgeld"};
Konto konto02{konto01};             //
Konto konto03 = konto01;            //neue Instanz
```
Attribute des Originals werden elementweise kopiert.

Zeiger (rohe und unique) dürfen nicht eifach kopiert werden.

Definition eigener Kopierkonstruktor um Deep Copy zu machen (compiler macht shallow). 
Dabei werden beispielsweise Pointer oder Referenzen auf neue Orte im Memory zeigen, 
bei shallow zeigen diese auf die selben Orte wie das Original (Bild 1).

![](https://media.geeksforgeeks.org/wp-content/uploads/copy-constructor.png)
![](https://media.geeksforgeeks.org/wp-content/uploads/copy-constructor1.png)

```cpp
Klassenname ( const Klassenname &altesObjekt);
 ############## konto.h #####################
 class Konto {
 public:
 
    //Konstruktor
    Konto(long s, string n);

    //Kopierkonstruktor
    Konto(const Konto&rhs);

};

############# Konto.cpp #################
#include "konto.h"
//Konstruktor
Konto::Konto(long s, string n): stand{s}, name{n} {} }

//Kopierkonstruktor
Konto::Konto(const Konto& rhs) : stand{rhs.stand}, name{rhs.name} {}
```

```cpp

#include<iostream>
#include<cstring>
using namespace std;
 
class String
{
private:
    char *s;
    int size;
public:
    String(const char *str = NULL); // constructor
    ~String() { delete [] s;  }// destructor
    String(const String&); // copy constructor
    void print() { cout << s << endl; } // Function to print string
    void change(const char *);  // Function to change
};
 
String::String(const char *str)
{
    size = strlen(str);
    s = new char[size+1];
    strcpy(s, str);
}
 
void String::change(const char *str)
{
    delete [] s;
    size = strlen(str);
    s = new char[size+1];
    strcpy(s, str);
}
 
String::String(const String& old_str)
{
    size = old_str.size;
    s = new char[size+1];
    strcpy(s, old_str.s);
}
 
int main()
{
    String str1("GeeksQuiz");
    String str2 = str1;
 
    str1.print(); // what is printed ?
    str2.print();
 
    str2.change("GeeksforGeeks");
 
    str1.print(); // what is printed now ?
    str2.print();
    return 0;
}

Output:
GeeksQuiz
GeeksQuiz
GeeksQuiz
GeeksforGeeks
```

### Move Constructor
Copy Constructor ist quasi Copy-Paste, Move Cosntructor ist Ausschneiden und einfügen. Nach dem Verschieben ist das Original "leer".

Parameter dürfen hier nicht const sein, da diese ja entnommen werden und das alte Objekt dann leer ist.

```cpp
Klassenname (Klassenname &&)

//Kopierkonstruktor verbieten wenn gewünscht
Konto(const Konto &rhs) = delete;

//Verschiebekonstruktor
Konto(Konto &&rhs);

//Daten für das neue Element
Konto::Konto(Konto &&rhs) : stand{rhs.stand}, name{rhs.name} {
    //Altes Element "leeren"
    rhs.stand = 0;
    rhs.name = "";
}
```
Verschieben
```cpp
Konto konto1{10000, "Vorlage"};
Konto konto2{std::move(konto1)};
Konto konto3 = std::move(konto2);
```
### Destruktor

Baut Objekte Kontrolliert ab. 
Normalerweise vom Compiler generiert, eigener bei Pointern etc nötig.

```cpp
//Deklaration
~Konto();

//Definition
Konto::~Konto() {std::cout << name << " deleted\n"};
```

### inline-Methoden
Funktion aufrufen, Rücksprundadresse auf Stack, Funktion anspringen, lokale Daten anlegen, Wieder freigeben, an Ausgangspunkt zurück

-> Viel Aufwand bei kleinen Funktionen

**Implizites inline:** innerhalb der Klassendefinition kann der Compiler selber inline Funktionen brauchen.

-> Achtung, Headerdatei wird so chaotisch!

**Explitites inline:** 

```cpp
inline long Konto::get_stand() {return stand;}
inline void Konto::set_stand(long s) {stand = s;}
```
### Konstante Methoden

Konstante Instantierung einer Klasse

```cpp
const Konto konstant {100000, "konstante"};
```
Nur noch Methoden aufrufen, die das Objekt nicht verändern (lesend)

Methode als lesend deklarieren:
```cpp
typ methode(parameter) const;

//Deklaration
long get_stand() cosnt;

//Definition
long Konto::get_stand() const {return stand;}
```
So sind beispielsweise Schlaifen über konstante Vektoren möglich.

### This-Zeiger

Methode weiss zu welcher Instanz sie gehört. Interner This-Zeiger
`Klassenname* const this = &Instanz`

Mit dem This-Zeiger kann auf Mitglieder einer Klasse zugegriffen werden `this->Element`
Das Macht der Compiler implizit für "normale Zugriffe".

Beispiel get_name:

```cpp
string Konto::get_name() const {
    return this->name;
}
```
## Objekte und Klassenelemente

### Objekte als Parameter

### Übergabe per Referenz an Funktion
```cpp
//Deklaration
void transfer(Konto& quelle, Konto& ziel, long betrag);
```
Verwendet Referenzen auf Objekte des Typs Konto als Parameter.
```cpp
//Definition
void transfer(Konto& quelle, Konto& ziel, long betrag) {
    quelle.set_stand(quelle.get_stand - betrag);
    ziel.set_stand(ziel.get_stand + betrag);
}
```
Nutzt die Klasse Konto, gehört aber nicht zu ihr, deshalb kein `Konto::`.
Nutzt nur die öffentlichen Methoden der Klasse Konto.

### Übergabe per Referenz an Methode
Bearbeiten von privaten Daten eines Objekts per Methode.

Instanz mit der die Methode aufgerufen wird steht schon fest, daher nur noch Ziel und Betrag definieren. Hier können nun direkt die privaten Attribute bearbeitet werden.

*Eine Methode kann auch auf Attribute einer anderen Instanz der Klasse zugreifen!*
```cpp
//Deklaration
class Konto {
    public:
        //Konstruktoren...
        //Methoden...
        void transfer(Konto& ziel, long betrag);
    private:
        long stand = 0;
        string name = "Unbekannt";
};
```

```cpp
//Definition
void Konto::transfer(Konto& ziel, long betrag) {
    stand -= betrag;        //Zugriff via implizites this (this->stand)
    ziel.stand += betrag;
}
```
### friend Funktion

Zugriff von Funktionen, Methoden oder fremden Klassen auf private Elemente. Mit der friend Funktion wird der Zugriff gewährt.

```cpp
// Prototyp der Friend Funktion
  friend void transfer(Konto& quelle, Konto& ziel, long betrag);
// Im public Bereich deklarieren.
```
```cpp
// Definition der Funktion transfer()
void transfer(Konto& quelle, Konto& ziel, long betrag) {
  quelle.stand -= betrag;
  ziel.stand += betrag;
}
```
### Objekte als Rückgabewerte
Kopie des Objekts als Rückgabewert. 

Zwei konten werden verglichen, da nur lesend wird  der Parameter als Referenz übergeben und das Konto mit dem höchsten Kontostand wird als Kopie zurückgegeben.

```cpp
//Header-datei
//Deklaration der Methode
Konto get_max(const Konto&);
//Prototyp der Funktion
Konto get_max(const Konto& a, const Konto& b);      //Konto als Rückgabetyp

//Definition der Methode
Konto Konto::get_max(const Konto& other) {
  if (stand > other.stand) {
    return *this;                                   //Typische Verwendung des this zeigers (gib Kopie von aktueller Instanz zurück)
  } else {
    return other;
  }
}
//Definition der Funktion
Konto get_max(const Konto& a, const Konto& b) {
  if (a.get_stand() > b.get_stand()) {
    return a;
  } else {
    return b;
  }
}
```
Aufruf

```cpp
#include "konto.h"

int main() {
  Konto konto1{112'57, "Brieftasche"};
  Konto konto2{650'32, "Girokonto"};
  // Aufruf der Hilfsfunktion
  Konto konto3 = get_max(konto1, konto2);
  // Aufruf der Methode
  Konto konto4 = konto1.get_max(konto2);

  // Auch so kann die Hilfsfunktion verwendet werden
  std::cout << get_max(konto1, konto2).get_name()
            << " hat maximalen Stand\n";

  // So geht es aber auch auch mit der Methode
  std::cout << konto1.get_max(konto2).get_name()
            << " hat maximalen Stand\n";

  return EXIT_SUCCESS;
}
```
### Referenz auf Objekte als Rückgabewerte
*Nie eine Referenz auf ein Objekt zurückgeben, dass lokal in einer Methode oder Funktion erzeugt wurde. Immer mit einer Kopie arbeiten!*

```cpp
//Methodendeklaration
Konto& get_max_ref(Konto& other);

// Prototyp der Funktion
Konto& get_max_ref(Konto& a, Konto& b);
```
Rückgabetyp ist nun eine Referenz auf ein Konto `Konto&`


```cpp
//Methodendefinition
Konto& Konto::get_max_ref(Konto& other) {
  if (stand > other.stand) {
    return *this;
  } else {
    return other;
  }
}
// Funktionsdefinition
Konto& get_max_ref(Konto& a, Konto& b) {
  if (a.get_stand() > b.get_stand()) {
    return a;
  } else {
    return b;
  }
}
```
Ganz andere Verwendung möglich:

```cpp
get_max_ref(giro, spar).transfer(brief, 300'00);
giro.get_max_ref(spar).transfer(brief, 50'00);
```
### Arrays von Objekten
Erzeugen von Vektor mit 50 Instanzen der Klasse Konto. Der parameterlose Konstruktor muss hier verwendet werden!
```cpp
std::vector <Konto> kontovector(50);
```
Leeres Array und Step-by-Step füllen:
```cpp
  // Leeres vector-Array
  std::vector<Konto> vkonto;
  // Beispielsweise: Elemente hinten anfügen
  vkonto.push_back(Konto{120'57, "Brieftasche"});
  vkonto.push_back(Konto{"Festgeld"});
  vkonto.push_back(Konto{});
  // Inhalt ausgeben
  for (auto& elem : vkonto) {
    elem.print();
  }
```
### Dynamische Objekte
Dynamisch Objekte in einer Klasse zur Laufzeit reservieren:
```cpp
int main() {
    //Ein Objekt zur Laufzeit vom Heap anfordern
    auto konto_ptr = std::make_unique<Konto>(9999, "make_unique");

    //Bsp roher Pointer (braucht delete)
    //Konto* konto_ptr = new Konto(99999, "raw pointer");

    konto_ptr->print();

    //Fünf Objekte zur Laufzeit vom Heap anfordern
    constexpr int SIZE = 5;
    std::unique_ptr<Konto[]> dynArray1 = std::make_unique<Konto[]>(SIZE);

    //Bsp roher Pointer (braucht delete[])
    //Konto* dynArray1 = new Konto[SIZE];

    dynArray1[0].set_name("Array0");
    dynArray1[0].set_stand(00'00);
    dynArray1[1] = Konto{11'11, "Array1"};
    dynArray1[2] = {22'22, "Array2"};
    dynArray1[3] = *konto_ptr;
    dynArray1[3].set_stand(33'33);
    dynArray1[4] = Konto{44'44, "Array4"};

    // Ausgabe
    for (size_t i = 0; i < SIZE; ++i) {
    dynArray1[i].print();
    }

    // delete konto_ptr;
    // delete[] dynArray1;

    return EXIT_SUCCESS;
}
```

### Klassenobjekte als Klassenattribute
Nicht nur Basisdatentypen sondern auch Klassen als Datenelemente einer Klasse. Bsp Klasse Kunde hat Element Konto.

-> Konstruktoren beachten!

*Wenn für ein eingbettetes Attribut eines Klassendatentyps keinei Intitialisierung vorgesehen wird und kein Kostruktor aufgerufen wird, wird es mit dem Standardkonstruktor initialisiert.*

```cpp
// listings/12/08_classattr/person.h
#ifndef _08__CLASSATTR_PERSON_H_
#define _08__CLASSATTR_PERSON_H_

#include <string>

class Person {
 public:
  Person(std::string vn, std::string nn);

  std::string get_vname() const;
  void set_vname(std::string vn);
  std::string get_nname() const;
  void set_nname(std::string nn);
  void print() const;

 private:
  std::string vname = "";
  std::string nname = "";
};

#endif  // _08__CLASSATTR_PERSON_H_
```

```cpp
// listings/12/08_classattr/person.cpp
#include <iomanip>
#include <iostream>

#include "person.h"

Person::Person(std::string vn, std::string nn)
    : vname{vn}, nname{nn} {}

std::string Person::get_vname() const {
  return vname;
}

void Person::set_vname(std::string vn) {
  vname = vn;
}

std::string Person::get_nname() const {
  return nname;
}

void Person::set_nname(std::string nn) {
  nname = nn;
}

void Person::print() const {
  std::cout << get_vname() << ' ' << get_nname() << '\n';
}
```

```cpp
// listings/12/08_classattr/konto.h
#ifndef _08_CLASSATRR_KONTO_H_
#define _08_CLASSATRR_KONTO_H_

#include <cstdlib>
#include <iomanip>
#include <iostream>
#include <vector>
#include <memory>
#include <sstream>
#include <string>

#include "person.h"

class Konto {
 public:
  // Deklaration der Konstruktoren
  Konto(long s, std::string n, const Person& p);
  Konto(long s, std::string n, std::string vn, std::string nn);

  // Methoden der Klasse "Konto"
  long get_stand() const;
  void set_stand(long s);
  void set_stand(long s) const = delete;
  std::string get_name() const;
  void set_name( std::string n);
  void set_name( std::string n) const = delete;

  void set_inhaber_vname(std::string vn);

  void print() const;
  void print_all() const;

  void transfer(Konto& ziel, long betrag);

 private:
  std::string format_cent(long c) const;
  // Attribute der Klasse "Konto"
  long stand = 0;
  std::string name = "Unbekannt";
  Person inhaber = {"", ""};
};

// Prototyp der Funktion
void transfer(Konto& quelle, Konto& ziel, long betrag);

#endif  // _08_CLASSATRR_KONTO_H_
```

```cpp
// listings/12/08_classattr/konto.cpp

#include <cstdlib>
#include <iomanip>
#include <iostream>
#include <vector>
#include <memory>
#include <sstream>
#include <string>

#include "konto.h"
#include "person.h"

// Definition der Konstruktoren

Konto::Konto(long s, std::string n, const Person& p)    //Konstruktor nimmt auch Daten zu person auf
    : stand{s}, name{n}, inhaber{p} {}                  
Konto::Konto(long s, std::string n, std::string vn,     //Konstruktor nimmt auch Daten zu person auf
             std::string nn)
    : Konto(s, n, {vn, nn}) {}

// Definition der Methoden
long Konto::get_stand() const {
  return stand;
}

void Konto::set_stand(long s) {
  stand = s;
}

std::string Konto::get_name() const {
  return name;
}

void Konto::set_name( std::string n) {
  name = n;
}

void Konto::set_inhaber_vname(std::string vn) {
  inhaber.set_vname(vn);
}

void Konto::print() const {
  std::cout << name << ":\t";
  std::cout << format_cent(stand) << " EUR\n";
}

std::string Konto::format_cent(long c) const {
  std::stringstream stream{};
  stream << std::fixed << std::setprecision(2);
  stream << (c / 100.);
  return stream.str();
}

void Konto::print_all() const {
  std::cout << "Inhaber: ";
  inhaber.print();
  print();
}

// Definition der Funktion
void transfer(Konto& quelle, Konto& ziel, long betrag) {
  quelle.set_stand(quelle.get_stand() - betrag);
  ziel.set_stand(ziel.get_stand() + betrag);
}
```
```cpp
// listings/12/08_classattr/main.cpp
#include <cstdlib>

#include "person.h"
#include "konto.h"
int main() {
  Person tim{"Tim", "Testperson"};
  tim.print();
  std::cout << "Person: " << tim.get_vname() << ' '
            << tim.get_nname() << '\n';

  Konto ktim{2'000'00, "Sparbuch", tim};
  ktim.print_all();

  Person mia{"Mia", "Musterfrau"};
  Konto kmia{5'000'50, "Festgeld", mia};
  kmia.print_all();

  ktim.set_inhaber_vname("Timotheus");
  ktim.print_all();

  return EXIT_SUCCESS;
}
```

### Containerklasse als Klassenattribut
Konto bekommt Vektor in dem transfers gespeichert werden.

```cpp
// listings/12/08_container/konto.h
#ifndef _08_CONTAINER_KONTO_H_
#define _08_CONTAINER_KONTO_H_

#include <string>
#include <vector>

class Konto {
 public:
  // Deklaration der Konstruktoren
  Konto();
  Konto(long s, std::string n);
  Konto(long s);
  Konto(std::string n);

  // Methoden der Klasse "Konto"
  long get_stand() const;
  void set_stand(long s);
  void set_stand(long s) const = delete;
  std::string get_name() const;
  void set_name( std::string n);
  void set_name( std::string n) const = delete;

  void print() const;

  void transfer(Konto& ziel, long betrag);

 private:
  std::string format_cent(long c) const;
  // Attribute der Klasse "Konto"
  long stand = 0;
  std::string name = "Unbekannt";
  std::vector<std::string> vtransfer;           //Transaktionsstrings
};
// Prototyp der Funktion
void transfer(Konto& quelle, Konto& ziel, long betrag);

#endif  //  _08_CONTAINER_KONTO_H_
```


```cpp
// listings/12/08_container/konto.cpp

#include "konto.h"

#include <iomanip>
#include <iostream>
#include <sstream>
#include <string>

// Definition der Konstruktoren
Konto::Konto() : Konto{0, "Unbekannt"} {}
Konto::Konto(long s, std::string n) : stand{s}, name{n} {       //Initialer Kontostand als erster Eintrag
  vtransfer.push_back(format_cent(s) + "<-Konstruktor");
}
Konto::Konto(long s) : Konto{s, "Unbekannt"} {}
Konto::Konto(std::string n) : Konto{0, n} {}

// Definition der Methoden
long Konto::get_stand() const {
  return stand;
}

void Konto::set_stand(long s) {
  stand = s;
}

std::string Konto::get_name() const {
  return name;
}

void Konto::set_name( std::string n) {
  name = n;
}

void Konto::print() const {
  std::cout << name << ":\t";
  std::cout << format_cent(stand) << " EUR\n";
  std::cout << "Liste der Transfers:\n";
  for (const auto& el : vtransfer)
    std::cout << " " << el << '\n';
  std::cout << '\n';
}

void Konto::transfer(Konto& ziel, long betrag) {        //Anhängen einer Transaktion
  stand -= betrag;
  ziel.stand += betrag;
  vtransfer.push_back(format_cent(betrag) + "->" + ziel.name);
  ziel.vtransfer.push_back(format_cent(betrag) + "<-" +
                           this->name);
}

std::string Konto::format_cent(long c) const {
  std::stringstream stream{};
  stream << std::fixed << std::setprecision(2);
  stream << (c / 100.);
  return stream.str();
}
```
### Smart Pointer als Klassenattribut
Vertreter der für ein bestehendes Konto gesetzt und entfernt werden kann.

```cpp
// listings/12/09_smartptr/konto.h
#ifndef _09_SMARTPTR_KONTO_H_
#define _09_SMARTPTR_KONTO_H_

#include <cstdlib>
#include <iomanip>
#include <iostream>
#include <vector>
#include <memory>
#include <sstream>
#include <string>

#include "person.h"

class Konto {
 public:
  // Deklaration der Konstruktoren
  Konto(long s, std::string n, std::string vn, std::string nn);
  Konto(long s, std::string n, const Person& p);
  Konto(const Konto& original);
  // Methoden der Klasse "Konto"
  long get_stand() const;
  void set_stand(long s);
  void set_stand(long s) const = delete;
  std::string get_name() const;
  void set_name( std::string n);
  void set_name( std::string n) const = delete;

  void set_inhaber_vname(std::string vn);
  void set_vertreter(std::string vn, std::string nn);
  void set_vertreter(const Person& p);
  void set_vertreter();
  void print() const;
  void print_all() const;

  void transfer(Konto& ziel, long betrag);

 private:
  std::string format_cent(long c) const;
  // Attribute der Klasse "Konto"
  long stand = 0;
  std::string name = "Unbekannt";
  Person inhaber;
  std::unique_ptr<Person> vertreter = nullptr;      //direkte Initialisierung via Nullpointer
};

// Prototyp der Funktion
void transfer(Konto& quelle, Konto& ziel, long betrag);

#endif  // _09_SMARTPTR_KONTO_H_
```


```cpp
void Konto::set_vertreter(std::string vn, std::string nn) {
  vertreter = std::make_unique<Person>(vn, nn);
}
void Konto::set_vertreter(const Person& p) {
  vertreter = std::make_unique<Person>(p);
}

void Konto::set_vertreter() {       //Löscht vertreter (methode reset())
  vertreter = nullptr;
}
```
set_vertreter() setzt eine Person als Vertreter
Speicher für Objekkt Person wird dynamisch angefordert.
std::make_unique konstruiert Instanz Person und speichert Adresse
Entweder für vor- und Nachname oder direkt mit Personenobjekt

```cpp
void Konto::print_all() const {
  std::cout << "Inhaber: ";
  inhaber.print();
  std::cout << "Vertreter: ";
  if (vertreter) {                  //Smart pointer werden implizit in true umgewandelt wenn kein Nullpointer
    vertreter->print();
  } else {
    std::cout << "(nicht gesetzt)\n";
  }
  print();
}
```

```cpp
// listings/12/09_smartptr/main.cpp
#include <cstdlib>

#include "person.h"
#include "konto.h"
int main() {
  Konto ktim{5'000'50, "Festgeld", "Tim", "Testperson"};
  ktim.set_vertreter("Bente", "Buddy");
  ktim.print_all();
  Person charlie{"Charlie", "Cozeichner"};
  std::cout << "Neue Vertreter setzen\n";
  ktim.set_vertreter(charlie);
  std::cout << "Vertreter entfernen\n";
  ktim.set_vertreter();
  std::cout << "main() beenden\n";

  Konto copy = ktim;
  Konto verschiebung = std::move(ktim);
  return EXIT_SUCCESS;
}
```
Kopieren hier nicht möglich `Konto copy = ktim`, da Smart Pointer kein Copy Constructor haben. Da muss eienr geschrieben werden, oder move() gemacht werden! `Konto verschiebung = std::move(ktim)`

### Statische Klassenelemente
Klassenelemente unabhängig von einer Instanz der Klasse verwenden. Attribute und Methoden mit *static* sind nur einmal im Speicher vorhanden und können verwendet werden, wenn noch keine Instanz der Klasse existiert.

Sie verwalten übergreifende Informationen einer Klasse wie die Anzahl Instanzen oder deren Minimal- und Maximalwerte.
```cpp

```

```cpp

```

```cpp

```

```cpp

```

## Operatoren überladen
```cpp

```


## Vererbung

```cpp

```

## Templates

```cpp

```

## Fehlerbehandlung

```cpp

```

## Ein-/Ausgabestreams
```cpp

```

## Weitere Sprachelemente
```cpp

```

