# Урок 3: Синтаксис в C#

В этом уроке мы рассмотрим основные аспекты синтаксиса языка программирования C#.

## Основные элементы синтаксиса

### Комментарии

Комментарии в C# могут быть однострочными и многострочными.

#### Однострочные комментарии

'''csharp
// Это однострочный комментарий
Console.WriteLine("Hello, World!"); // Комментарий после строки кода
'''

#### Многострочные комментарии

'''csharp
/* Это многострочный
   комментарий */
Console.WriteLine("Hello, World!");
'''

### Переменные

Переменные в C# должны быть объявлены с указанием типа данных.

'''csharp
int myNumber = 10;
string myString = "Hello";
bool myBool = true;
'''

### Константы

Константы объявляются с использованием ключевого слова `const`.

'''csharp
const int myConst = 100;
const string myConstString = "Constant String";
'''

## Операторы

### Арифметические операторы

- `+` : сложение
- `-` : вычитание
- `*` : умножение
- `/` : деление
- `%` : остаток от деления

'''csharp
int a = 10;
int b = 5;
int sum = a + b;        // 15
int difference = a - b; // 5
int product = a * b;    // 50
int quotient = a / b;   // 2
int remainder = a % b;  // 0
'''

### Логические операторы

- `&&` : логическое И
- `||` : логическое ИЛИ
- `!` : логическое НЕ

'''csharp
bool x = true;
bool y = false;

bool andResult = x && y; // false
bool orResult = x || y;  // true
bool notResult = !x;     // false
'''

### Операторы сравнения

- `==` : равно
- `!=` : не равно
- `>` : больше
- `<` : меньше
- `>=` : больше или равно
- `<=` : меньше или равно

'''csharp
int a = 10;
int b = 20;

bool equal = (a == b);        // false
bool notEqual = (a != b);     // true
bool greater = (a > b);       // false
bool less = (a < b);          // true
bool greaterOrEqual = (a >= b); // false
bool lessOrEqual = (a <= b);    // true
'''

## Управляющие конструкции

### Условные операторы

#### if-else

'''csharp
int number = 10;

if (number > 5)
{
    Console.WriteLine("Number is greater than 5");
}
else
{
    Console.WriteLine("Number is less than or equal to 5");
}
'''

#### switch

'''csharp
int day = 3;

switch (day)
{
    case 1:
        Console.WriteLine("Monday");
        break;
    case 2:
        Console.WriteLine("Tuesday");
        break;
    case 3:
        Console.WriteLine("Wednesday");
        break;
    default:
        Console.WriteLine("Other day");
        break;
}
'''

### Циклы

#### for

'''csharp
for (int i = 0; i < 5; i++)
{
    Console.WriteLine($"Iteration {i}");
}
'''

#### while

'''csharp
int i = 0;

while (i < 5)
{
    Console.WriteLine($"Iteration {i}");
    i++;
}
'''

#### do-while

'''csharp
int i = 0;

do
{
    Console.WriteLine($"Iteration {i}");
    i++;
} while (i < 5);
'''

#### foreach

'''csharp
string[] fruits = { "Apple", "Banana", "Cherry" };

foreach (string fruit in fruits)
{
    Console.WriteLine(fruit);
}
'''

## Функции и методы

### Объявление и вызов методов

'''csharp
public void SayHello()
{
    Console.WriteLine("Hello!");
}

SayHello(); // Вызов метода
'''

### Возврат значения

'''csharp
public int Add(int a, int b)
{
    return a + b;
}

int result = Add(5, 3); // 8
Console.WriteLine(result);
'''

### Параметры методов

Методы могут принимать параметры и возвращать значения.

'''csharp
public int Multiply(int x, int y)
{
    return x * y;
}

int product = Multiply(4, 5); // 20
Console.WriteLine(product);
'''

## Классы и объекты

### Объявление класса

'''csharp
public class Person
{
    public string Name;
    public int Age;

    public void SayHello()
    {
        Console.WriteLine($"Hello, my name is {Name} and I am {Age} years old.");
    }
}
'''

### Создание объекта

'''csharp
Person person = new Person();
person.Name = "Alice";
person.Age = 30;
person.SayHello(); // Hello, my name is Alice and I am 30 years old.
'''

## Наследование

### Объявление базового и производного класса

'''csharp
public class Animal
{
    public void Eat()
    {
        Console.WriteLine("Eating...");
    }
}

public class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Barking...");
    }
}
'''

### Использование наследования

'''csharp
Dog myDog = new Dog();
myDog.Eat();  // Eating...
myDog.Bark(); // Barking...
'''

## Интерфейсы

### Объявление интерфейса

'''csharp
public interface IMovable
{
    void Move();
}
'''

### Реализация интерфейса

'''csharp
public class Car : IMovable
{
    public void Move()
    {
        Console.WriteLine("The car is moving.");
    }
}
'''

### Использование интерфейса

'''csharp
Car myCar = new Car();
myCar.Move(); // The car is moving.
'''

## Пространства имен

Пространства имен используются для организации кода и предотвращения конфликтов имен.

### Объявление пространства имен

'''csharp
namespace MyNamespace
{
    public class MyClass
    {
        public void MyMethod()
        {
            Console.WriteLine("Hello from MyNamespace.MyClass");
        }
    }
}
'''

### Использование пространства имен

'''csharp
using MyNamespace;

MyClass myClass = new MyClass();
myClass.MyMethod(); // Hello from MyNamespace.MyClass
'''

## Обработка исключений

### Использование try-catch-finally

'''csharp
try
{
    int[] numbers = { 1, 2, 3 };
    Console.WriteLine(numbers[10]);
}
catch (IndexOutOfRangeException ex)
{
    Console.WriteLine($"Exception caught: {ex.Message}");
}
finally
{
    Console.WriteLine("This block is always executed.");
}
'''

### Вывод результата

'''csharp
// Exception caught: Index was outside the bounds of the array.
// This block is always executed.
'''

## Заключение

В этом уроке мы рассмотрели основные аспекты синтаксиса языка программирования C#. Вы узнали, как объявлять переменные и константы, использовать операторы и управляющие конструкции, создавать и вызывать методы, работать с классами и объектами, использовать наследование и интерфейсы, организовывать код с помощью пространств имен и обрабатывать исключения. Эти знания являются фундаментом для дальнейшего изучения и использования C# в различных приложениях.

## Навигатор

- [На главную](../index.md)
- [Следующая  лекция](../B02_L02_Vars/README.md)