# Урок 4: Переменные в C#

В этом уроке мы погрузимся в переменные в C# и разберемся как их правильно именовать.

## Основы синтаксиса C#

C# — это строго типизированный, объектно-ориентированный язык программирования. Это означает, что каждая переменная и объект в программе должны иметь объявленный тип.

## Объявление переменных

Переменные в C# объявляются с использованием следующего синтаксиса:

```csharp
тип имя_переменной;
```

Например, чтобы объявить целочисленную переменную:

```csharp
int myNumber;
```

## Инициализация переменных

Переменные можно инициализировать сразу при объявлении:

```csharp
int myNumber = 5;
```

Можно также присвоить значение переменной позже:

```csharp
int myNumber;
myNumber = 5;
```

## Типы данных

В C# есть несколько основных типов данных:

- **int**: целое число (например, 1, 2, 3)
- **float**: число с плавающей запятой (например, 1.5, 2.5)
- **double**: число с двойной точностью (например, 1.5, 2.5)
- **char**: символ (например, 'a', 'b')
- **string**: строка (например, "hello", "world")
- **bool**: логический тип (например, true, false)

### Примеры

```csharp
int myInt = 10;
float myFloat = 10.5f;
double myDouble = 20.5;
char myChar = 'A';
string myString = "Hello, World!";
bool myBool = true;
```

## Локальные и глобальные переменные

Переменные могут быть объявлены внутри метода или класса.

### Локальные переменные

Локальные переменные объявляются внутри методов и доступны только в пределах этого метода.

```csharp
public void MyMethod()
{
    int localVar = 5; // Локальная переменная
    Console.WriteLine(localVar);
}
```

### Глобальные переменные

Глобальные переменные объявляются внутри класса, но вне методов. Они доступны всем методам этого класса.

```csharp
public class MyClass
{
    int globalVar = 10; // Глобальная переменная

    public void MyMethod()
    {
        Console.WriteLine(globalVar);
    }

    public void AnotherMethod()
    {
        globalVar = 20;
        Console.WriteLine(globalVar);
    }
}
```

## Константы

Константы — это переменные, значение которых не может изменяться после инициализации. Они объявляются с использованием ключевого слова `const`.

```csharp
const int myConst = 100;
```

## Модификаторы доступа

Переменные могут иметь различные уровни доступа:

- **public**: переменная доступна из любого места
- **private**: переменная доступна только внутри класса
- **protected**: переменная доступна внутри класса и его подклассов
- **internal**: переменная доступна внутри той же сборки (assembly)

### Примеры

```csharp
public class MyClass
{
    public int publicVar = 10; // Доступна из любого места
    private int privateVar = 20; // Доступна только внутри этого класса
    protected int protectedVar = 30; // Доступна внутри этого класса и его подклассов
    internal int internalVar = 40; // Доступна внутри той же сборки
}
```

## Именование переменных

- Имена переменных должны начинаться с буквы или символа подчеркивания (_).
- Имена переменных не могут начинаться с цифры.
- Имена переменных не могут совпадать с ключевыми словами C#.
- Принято использовать стиль camelCase для локальных переменных и PascalCase для глобальных переменных и свойств.

### Примеры

```csharp
int myVariable; // camelCase для локальной переменной
public int MyProperty { get; set; } // PascalCase для свойства
private int _myPrivateVar; // _ для приватных переменных
```

## Вывод значений переменных

Для вывода значений переменных можно использовать метод `Console.WriteLine`.

```csharp
int myNumber = 5;
Console.WriteLine("Значение переменной: " + myNumber);
```

Или использовать интерполяцию строк:

```csharp
int myNumber = 5;
Console.WriteLine($"Значение переменной: {myNumber}");
```

## Примеры использования переменных

### Пример 1: Объявление и инициализация

```csharp
int age = 25;
float height = 5.9f;
char initial = 'A';
string name = "Alice";
bool isStudent = true;

Console.WriteLine($"Name: {name}, Age: {age}, Height: {height}, Initial: {initial}, Is Student: {isStudent}");
```

### Пример 2: Арифметические операции

```csharp
int a = 5;
int b = 10;
int sum = a + b;
int difference = b - a;
int product = a * b;
int quotient = b / a;
int remainder = b % a;

Console.WriteLine($"Sum: {sum}, Difference: {difference}, Product: {product}, Quotient: {quotient}, Remainder: {remainder}");
```

### Пример 3: Условные операторы

```csharp
int number = 10;

if (number > 5)
{
    Console.WriteLine("Number is greater than 5");
}
else
{
    Console.WriteLine("Number is less than or equal to 5");
}
```

### Пример 4: Циклы

```csharp
for (int i = 0; i < 5; i++)
{
    Console.WriteLine($"Iteration {i}");
}
```

```csharp
int i = 0;
while (i < 5)
{
    Console.WriteLine($"Iteration {i}");
    i++;
}
```

Это руководство должно помочь вам понять основные концепции работы с переменными в C#.


## Навигатор

- [На главную](../index.md)
- [Следующая  лекция](../B02_L03_Math/README.md)