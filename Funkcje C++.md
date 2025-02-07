# 🎯 Ściąga do matury z C++ 💻


## 📌 Typy zmiennych

| 🔴 Typy całkowite | Wielkość (bajty) | Zakres | 
| ------------- | ----------------- | ------- |
| short | 2 | [-32768, 32767]
| int | 4 | [-2147483648, 2147483647]
| long | 4 | [-2147483648, 2147483647]
| long long | 8 | [-9223372036854775808, 9223372036854775807]
| unsigned ... | ... | [0, ...]

| 🔴 Typy rzeczywiste | Wielkość (bajty) | Zakres | 
| ------------- | ----------------- | ------- |
| float | 4 | pojedyncza precyzja - dokładność 6 - 7 cyfr po przecink
| double | 8 | podwójna precyzja - dokładność 15 - 16 cyfr po przecinku
| long double | 12 | liczby z ogromną dokładnością - 19 - 20 cyfr po przecinku

| 🔴 Typy znakowe | Wielkość (bajty) | Zakres | 
| ------------- | ----------------- | ------- |
| char | 1 |  	-128 ÷ 127
| unsigned char | 1 |  	0 ÷ 255


| 🔴 Typ logiczny | Wielkość (bajty) | Zakres | 
| ------------- | ----------------- | ------- |
| bool | 1 | true (1), false (0)

## 📌 Rzutowanie typów

**Przykład:**

```cpp
double a = 30.4853
int b = (int) a;    // Rzutowanie a na typ int. Sposób 1. // 30
int c = int (a);    // Sposób 2.

char znak = 'q';    
cout << znak << ": " << (int) znak; // Rzutowanie litery na int (ASCII)
```

## 📌 Operator trójargumentowy `? :`

``` cpp
WARUNEK ? JEŻELI_PRAWDA : JEŻELI_FAŁSZ
```

**Użycie:**

```cpp
int max = (a > b) ? a : b;  // 10
```

## 📌 Biblioteka `<iostream>` – wejście/wyjście

```cpp
cin >> zmienna;   // Wczytanie danych do zmiennej
cout << zmienna;  // Wypisanie zmiennej na ekran
```

**Typy danych:** `int`, `double`, `char`, `string`

## 📌 Biblioteka `<cmath>` – operacje matematyczne

```cpp
double sqrt(double x);        // Pierwiastek kwadratowy
double pow(double base, double exp); // Potęgowanie
int abs(int x);               // Wartość bezwzględna dla int
double fabs(double x);        // Wartość bezwzględna dla double
```

**Typy danych:** `int`, `double`

## 📌 Biblioteka `<cstdlib>` – losowanie liczb

```cpp
int rand();         // Generuje losową liczbę całkowitą
void srand(unsigned int seed); // Ustawia ziarno generatora losowego
```

**Typy danych:** `int`, `unsigned int`

**Użycie:**

```cpp
srand(time(0)); // Inicjalizacja generatora na podstawie czasu
int liczba = rand() % 100; // Losowa liczba z zakresu 0-99
```

## 📌 Biblioteka `<string>` – operacje na ciągach znaków

```cpp
string napis;              // Deklaracja napisu
int length() const;             // Zwraca długość napisu
string substr(int pos, int len) const; // Wyciąga podciąg
size_t find(const string& str) const; // Znajduje podciąg
```

**Typy danych:** `string`, `int`, `size_t`

**Przykład:**

```cpp
string tekst = "Matura C++";
int dlugosc = tekst.length(); // 10
string slowo = tekst.substr(0, 6); // "Matura"
size_t pozycja = tekst.find("C++"); // 7
```

## 📌 Biblioteka `<vector>` – dynamiczne tablice

```cpp
vector<int> vec;       // Deklaracja wektora liczb całkowitych
void push_back(const T& value); // Dodaje element na końcu
size_t size() const;         // Zwraca ilość elementów
T& at(size_t index);         // Zwraca element na danym indeksie
```

**Typy danych:** `vector<T>`, `size_t`, `T`

**Przykład:**

```cpp
vector<int> liczby;
liczby.push_back(5);
liczby.push_back(10);
int pierwszy = liczby.at(0); // 5
size_t rozmiar = liczby.size(); // 2
```

## 📌 Biblioteka `<algorithm>` – algorytmy

```cpp
void sort(Iterator begin, Iterator end); // Sortowanie rosnące
void reverse(Iterator begin, Iterator end); // Odwrócenie kolejności
template<typename T> Iterator max_element(Iterator begin, Iterator end); // Największy element
```

**Typy danych:** `Iterator`, `T`

**Przykład:**

```cpp
vector<int> liczby = {3, 1, 4, 1, 5};
sort(liczby.begin(), liczby.end()); // {1, 1, 3, 4, 5}
reverse(liczby.begin(), liczby.end()); // {5, 4, 3, 1, 1}
int maxVal = *max_element(liczby.begin(), liczby.end()); // 5
```

## 📌 Biblioteka `<bitset>` - konwersja liczby na system binarny

```cpp
int liczba = 42;
cout << "Liczba dziesiętnie: " << liczba << endl; // 42
cout << "Liczba binarnie: " << bitset<8> (liczba) << endl; // 00101010
```

## 📌 Biblioteka `<iomanip>` – manipulatory strumienia

```cpp
cout << fixed;      // Stała precyzja dziesiętna
cout << setprecision(int n); // Ustawia liczbę miejsc po przecinku
cout << setw(int n); // Ustawia szerokość pola
cout << setfill(char c); // Ustawia znak wypełnienia
cout << hex;        // Liczby w systemie szesnastkowym
cout << dec;        // Liczby w systemie dziesiętnym
cout << oct;        // Liczby w systemie ósemkowym
```

**Typy danych:** `int`, `char`

**Przykład:**

```cpp
cout << fixed << setprecision(2) << 3.14159; // 3.14
cout << setw(5) << setfill('0') << 42; // 00042
cout << hex << 255; // ff
```

## 📌 Biblioteka `<fstream>` – obsługa plików

```cpp
ofstream plikOut("plik.txt"); // Tworzenie i otwieranie pliku do zapisu
plikOut << "Hello, world!";
plikOut.close();

ifstream plikIn("plik.txt"); // Otwieranie pliku do odczytu
string linia;
while (getline(plikIn, linia)) { // Pobranie całej linii
    cout << linia << endl;
}
plikIn.close();

ifstream plikIn("plik.txt"); // Otwieranie pliku do odczytu
string slowo;
while (plikIn >> slowo) { // Pobranie pojedynczego slowa
    cout << slowo << endl;
}
```

**Typy danych:** `string`, `char`, `ifstream`, `ofstream`

🎯 **Z tą ściągą zdasz maturę z informatyki na 100%!**