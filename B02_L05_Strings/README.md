# Урок 2.5: Работа со строками в C#

В этом уроке мы рассмотрим работу со строками в C#, включая создание строк, основные методы, интерполяцию и конкатенацию строк.

## Создание строк

Строки в C# представляются типом `string`. Строки можно создавать несколькими способами:

### Литералы строк

```csharp
string myString = "Hello, World!";
```

### Пустые и null строки

```csharp
string emptyString = ""; // Пустая строка
string nullString = null; // Строка, не указывающая на объект
```

### Многострочные строки

С версии C# 11 можно использовать многострочные литералы строк:

```csharp
string multiLineString = """
Это многострочная строка
в языке C#.
Она поддерживает несколько строк.
""";
```

## Конкатенация строк

Конкатенация строк — это объединение нескольких строк в одну.

### Использование оператора `+`

```csharp
string firstName = "John";
string lastName = "Doe";
string fullName = firstName + " " + lastName;
Console.WriteLine(fullName); // John Doe
```

### Использование метода `string.Concat`

```csharp
string fullName = string.Concat(firstName, " ", lastName);
Console.WriteLine(fullName); // John Doe
```

### Использование метода `string.Join`

```csharp
string[] words = { "Hello", "world", "from", "C#" };
string sentence = string.Join(" ", words);
Console.WriteLine(sentence); // Hello world from C#
```

## Интерполяция строк

Интерполяция строк позволяет встроить выражения внутрь строковых литералов. Это делается с помощью символа `$`.

```csharp
string name = "Alice";
int age = 30;
string greeting = $"Hello, my name is {name} and I am {age} years old.";
Console.WriteLine(greeting); // Hello, my name is Alice and I am 30 years old.
```

## Основные методы работы со строками

### Метод `Length`

Метод `Length` возвращает длину строки.

```csharp
string myString = "Hello, World!";
int length = myString.Length;
Console.WriteLine(length); // 13
```

### Метод `ToUpper` и `ToLower`

Методы `ToUpper` и `ToLower` преобразуют строку в верхний или нижний регистр соответственно.

```csharp
string lower = "hello";
string upper = lower.ToUpper();
Console.WriteLine(upper); // HELLO

string mixed = "HeLLo WoRLD";
string lowerMixed = mixed.ToLower();
Console.WriteLine(lowerMixed); // hello world
```

### Метод `Trim`

Метод `Trim` удаляет пробелы из начала и конца строки.

```csharp
string spaced = "   hello   ";
string trimmed = spaced.Trim();
Console.WriteLine(trimmed); // "hello"
```

### Метод `Substring`

Метод `Substring` извлекает подстроку из строки.

```csharp
string text = "Hello, World!";
string sub = text.Substring(7, 5);
Console.WriteLine(sub); // World
```

### Метод `Replace`

Метод `Replace` заменяет все вхождения одной строки на другую.

```csharp
string text = "Hello, World!";
string replaced = text.Replace("World", "C#");
Console.WriteLine(replaced); // Hello, C#!
```

### Метод `Contains`

Метод `Contains` проверяет, содержит ли строка указанную подстроку.

```csharp
string text = "Hello, World!";
bool contains = text.Contains("World");
Console.WriteLine(contains); // True
```

### Метод `IndexOf`

Метод `IndexOf` возвращает индекс первого вхождения подстроки.

```csharp
string text = "Hello, World!";
int index = text.IndexOf("World");
Console.WriteLine(index); // 7
```

### Метод `Split`

Метод `Split` разбивает строку на массив подстрок на основе заданного разделителя.

```csharp
string text = "apple,banana,cherry";
string[] fruits = text.Split(',');
foreach (string fruit in fruits)
{
    Console.WriteLine(fruit);
}
// Output:
// apple
// banana
// cherry
```

## StringBuilder

Класс `StringBuilder` из пространства имен `System.Text` используется для построения и изменения строк, особенно если требуется выполнить множество операций над строками.

### Пример использования `StringBuilder`

```csharp
using System.Text;

StringBuilder sb = new StringBuilder();
sb.Append("Hello");
sb.Append(", ");
sb.Append("World!");
string result = sb.ToString();
Console.WriteLine(result); // Hello, World!
```

## Форматирование строк

Метод `string.Format` позволяет форматировать строки с использованием маркеров.

```csharp
string name = "Alice";
int age = 30;
string formatted = string.Format("Name: {0}, Age: {1}", name, age);
Console.WriteLine(formatted); // Name: Alice, Age: 30
```

## Заключение

В этом уроке мы рассмотрели работу со строками в C#, включая создание строк, конкатенацию, интерполяцию, использование различных методов для работы со строками и использование `StringBuilder` для эффективного построения строк. Практикуйтесь с этими инструментами, чтобы лучше понять, как работать со строками в C#.

## Навигатор

- [На главную](../index.md)
- [Предыдущий урок](../B02_L04_Logic/README.md)
- [Следующий урок](../B02_L06_Cycles/README.md)