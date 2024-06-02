# Урок 4: Арифметические операции и операторы в C#

В этом уроке мы рассмотрим различные арифметические операции и операторы, доступные в языке программирования C#.

## Основные арифметические операторы

C# поддерживает стандартные арифметические операторы:

- `+` : сложение
- `-` : вычитание
- `*` : умножение
- `/` : деление
- `%` : остаток от деления (модуль)

### Примеры использования

```csharp
int a = 10;
int b = 5;

int sum = a + b;        // Сложение: 15
int difference = a - b; // Вычитание: 5
int product = a * b;    // Умножение: 50
int quotient = a / b;   // Деление: 2
int remainder = a % b;  // Остаток от деления: 0
```

### Вывод результатов

```csharp
Console.WriteLine($"Sum: {sum}");           // Sum: 15
Console.WriteLine($"Difference: {difference}"); // Difference: 5
Console.WriteLine($"Product: {product}");       // Product: 50
Console.WriteLine($"Quotient: {quotient}");     // Quotient: 2
Console.WriteLine($"Remainder: {remainder}");   // Remainder: 0
```

## Операторы увеличения и уменьшения

C# предоставляет операторы для увеличения и уменьшения значения переменной на единицу:

- `++` : инкремент (увеличение на 1)
- `--` : декремент (уменьшение на 1)

### Примеры использования

```csharp
int x = 5;

x++; // Инкремент: x становится 6
x--; // Декремент: x становится 5
```

### Префиксная и постфиксная форма

Операторы инкремента и декремента имеют префиксную и постфиксную форму:

- Префиксная: значение увеличивается/уменьшается перед использованием в выражении.
- Постфиксная: значение увеличивается/уменьшается после использования в выражении.

```csharp
int y = 5;
int prefixResult = ++y; // y становится 6, затем присваивается prefixResult (6)
int postfixResult = y--; // y присваивается postfixResult (6), затем y уменьшается (5)
```

### Вывод результатов

```csharp
Console.WriteLine($"Prefix Result: {prefixResult}");   // Prefix Result: 6
Console.WriteLine($"Postfix Result: {postfixResult}"); // Postfix Result: 6
Console.WriteLine($"Current y Value: {y}");            // Current y Value: 5
```

## Составные операторы присваивания

C# поддерживает составные операторы, которые объединяют арифметическую операцию и присваивание:

- `+=` : прибавление с присваиванием
- `-=` : вычитание с присваиванием
- `*=` : умножение с присваиванием
- `/=` : деление с присваиванием
- `%=` : остаток от деления с присваиванием

### Примеры использования

```csharp
int z = 10;

z += 5;  // Эквивалентно z = z + 5; z становится 15
z -= 3;  // Эквивалентно z = z - 3; z становится 12
z *= 2;  // Эквивалентно z = z * 2; z становится 24
z /= 4;  // Эквивалентно z = z / 4; z становится 6
z %= 4;  // Эквивалентно z = z % 4; z становится 2
```

### Вывод результатов

```csharp
Console.WriteLine($"z after += 5: {z}");   // z after += 5: 15
Console.WriteLine($"z after -= 3: {z}");   // z after -= 3: 12
Console.WriteLine($"z after *= 2: {z}");   // z after *= 2: 24
Console.WriteLine($"z after /= 4: {z}");   // z after /= 4: 6
Console.WriteLine($"z after %= 4: {z}");   // z after %= 4: 2
```

## Приоритет операций

Операции в C# выполняются в порядке приоритета. Скобки можно использовать для изменения порядка выполнения.

### Приоритет операций

1. Постфиксные: `x++`, `x--`
2. Префиксные: `++x`, `--x`
3. Мультипликативные: `*`, `/`, `%`
4. Аддитивные: `+`, `-`

### Примеры

```csharp
int a = 2;
int b = 3;
int c = 4;

int result = a + b * c;    // Умножение выполняется первым: 2 + (3 * 4) = 2 + 12 = 14
int resultWithBrackets = (a + b) * c; // Скобки изменяют порядок: (2 + 3) * 4 = 5 * 4 = 20
```

### Вывод результатов

```csharp
Console.WriteLine($"Result without brackets: {result}");       // Result without brackets: 14
Console.WriteLine($"Result with brackets: {resultWithBrackets}"); // Result with brackets: 20
```

## Операции с вещественными числами

Арифметические операции могут выполняться с числами с плавающей точкой (`float`, `double`, `decimal`).

### Примеры

```csharp
float floatA = 5.5f;
float floatB = 2.2f;

float floatSum = floatA + floatB;         // Сложение
float floatDifference = floatA - floatB;  // Вычитание
float floatProduct = floatA * floatB;     // Умножение
float floatQuotient = floatA / floatB;    // Деление

double doubleA = 5.5;
double doubleB = 2.2;

double doubleSum = doubleA + doubleB;         // Сложение
double doubleDifference = doubleA - doubleB;  // Вычитание
double doubleProduct = doubleA * doubleB;     // Умножение
double doubleQuotient = doubleA / doubleB;    // Деление
```

### Вывод результатов

```csharp
Console.WriteLine($"Float Sum: {floatSum}");             // Float Sum: 7.7
Console.WriteLine($"Float Difference: {floatDifference}");   // Float Difference: 3.3
Console.WriteLine($"Float Product: {floatProduct}");     // Float Product: 12.1
Console.WriteLine($"Float Quotient: {floatQuotient}");   // Float Quotient: 2.5

Console.WriteLine($"Double Sum: {doubleSum}");           // Double Sum: 7.7
Console.WriteLine($"Double Difference: {doubleDifference}"); // Double Difference: 3.3
Console.WriteLine($"Double Product: {doubleProduct}");   // Double Product: 12.1
Console.WriteLine($"Double Quotient: {doubleQuotient}"); // Double Quotient: 2.5
```

## Операции с decimal

Тип `decimal` часто используется для финансовых расчетов из-за его высокой точности.

### Примеры

```csharp
decimal decimalA = 5.5m;
decimal decimalB = 2.2m;

decimal decimalSum = decimalA + decimalB;         // Сложение
decimal decimalDifference = decimalA - decimalB;  // Вычитание
decimal decimalProduct = decimalA * decimalB;     // Умножение
decimal decimalQuotient = decimalA / decimalB;    // Деление
```

### Вывод результатов

```csharp
Console.WriteLine($"Decimal Sum: {decimalSum}");             // Decimal Sum: 7.7
Console.WriteLine($"Decimal Difference: {decimalDifference}");   // Decimal Difference: 3.3
Console.WriteLine($"Decimal Product: {decimalProduct}");     // Decimal Product: 12.1
Console.WriteLine($"Decimal Quotient: {decimalQuotient}");   // Decimal Quotient: 2.5
```

## Заключение

В этом уроке мы рассмотрели основные арифметические операции и операторы в C#. Теперь вы знаете, как выполнять сложение, вычитание, умножение, деление и операции с остатком. Также вы узнали о приоритетах операций и работе с различными типами данных, включая целые числа и числа с плавающей точкой. Вы научились использовать составные операторы присваивания и работу с инкрементом и декрементом. 

Практикуйтесь с этими операторами, чтобы укрепить свои навыки программирования на C#.


## Навигатор

- [На главную](../index.md)
- [Следующая  лекция](../B02_L04_Logic/README.md)