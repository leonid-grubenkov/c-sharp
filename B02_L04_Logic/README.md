# Урок 2.4: Логические операторы в C#

В этом уроке мы рассмотрим различные логические операторы, доступные в языке программирования C#.

## Основные логические операторы

Логические операторы используются для выполнения логических операций и возвращают значения типа `bool` (`true` или `false`).

### Операторы И (`&&`) и ИЛИ (`||`)

- `&&` (логическое И): возвращает `true`, если оба операнда истинны.
- `||` (логическое ИЛИ): возвращает `true`, если хотя бы один из операндов истинен.

#### Примеры использования

```csharp
bool a = true;
bool b = false;

bool andResult = a && b;  // false, так как b = false
bool orResult = a || b;   // true, так как a = true
```

### Оператор НЕ (`!`)

- `!` (логическое НЕ): возвращает `true`, если операнд ложен, и `false`, если операнд истинен.

#### Примеры использования

```csharp
bool a = true;

bool notResult = !a;  // false, так как a = true
```

## Логические выражения

Логические операторы часто используются в выражениях и условиях для управления потоком выполнения программы.

### Примеры условий

```csharp
int x = 10;
int y = 20;

if (x < y && y < 30)
{
    Console.WriteLine("Оба условия верны.");
}
else
{
    Console.WriteLine("Одно или оба условия ложны.");
}
```

### Пример с оператором ИЛИ

```csharp
int age = 25;
bool hasPermission = false;

if (age >= 18 || hasPermission)
{
    Console.WriteLine("Доступ разрешен.");
}
else
{
    Console.WriteLine("Доступ запрещен.");
}
```

## Операторы сравнения

Логические операторы часто используются с операторами сравнения для построения сложных условий.

### Основные операторы сравнения

- `==` : равно
- `!=` : не равно
- `>` : больше
- `<` : меньше
- `>=` : больше или равно
- `<=` : меньше или равно

#### Примеры использования

```csharp
int a = 10;
int b = 20;

bool equalResult = (a == b);   // false
bool notEqualResult = (a != b); // true
bool greaterResult = (a > b);  // false
bool lessResult = (a < b);     // true
bool greaterOrEqualResult = (a >= b); // false
bool lessOrEqualResult = (a <= b);    // true
```

### Вывод результатов

```csharp
Console.WriteLine($"Equal: {equalResult}");           // Equal: False
Console.WriteLine($"Not Equal: {notEqualResult}");    // Not Equal: True
Console.WriteLine($"Greater: {greaterResult}");       // Greater: False
Console.WriteLine($"Less: {lessResult}");             // Less: True
Console.WriteLine($"Greater or Equal: {greaterOrEqualResult}"); // Greater or Equal: False
Console.WriteLine($"Less or Equal: {lessOrEqualResult}");       // Less or Equal: True
```

## Логические операторы с числами

Логические операторы могут быть использованы для сравнения числовых значений в условиях.

### Пример

```csharp
int number = 15;

if (number > 10 && number < 20)
{
    Console.WriteLine("Number is between 10 and 20.");
}
else
{
    Console.WriteLine("Number is not between 10 and 20.");
}
```

### Вывод результата

```csharp
// Number is between 10 and 20.
```

## Комбинированные условия

Логические операторы позволяют комбинировать несколько условий в одно сложное условие.

### Пример

```csharp
int temperature = 25;
bool isSunny = true;

if ((temperature > 20 && temperature < 30) && isSunny)
{
    Console.WriteLine("It's a warm and sunny day.");
}
else
{
    Console.WriteLine("The weather is not ideal.");
}
```

### Вывод результата

```csharp
// It's a warm and sunny day.
```

## Краткое замыкание (Short-circuiting)

В C# используется краткое замыкание при оценке логических выражений. Это означает, что если результат выражения может быть определен на основе первого операнда, второй операнд не будет оцениваться.

### Пример с оператором И

```csharp
bool a = false;
bool b = (10 / 0 > 1);  // Это выражение вызовет деление на ноль, если будет оценено

if (a && b)
{
    Console.WriteLine("This will not be printed.");
}
else
{
    Console.WriteLine("This will be printed.");
}
```

### Пример с оператором ИЛИ

```csharp
bool a = true;
bool b = (10 / 0 > 1);  // Это выражение вызовет деление на ноль, если будет оценено

if (a || b)
{
    Console.WriteLine("This will be printed.");
}
else
{
    Console.WriteLine("This will not be printed.");
}
```

### Вывод результата

```csharp
// This will be printed.
```

## Заключение

В этом уроке мы рассмотрели основные логические операторы в C#, такие как `&&`, `||`, и `!`, а также операторы сравнения и их использование в логических выражениях и условиях. Мы узнали, как использовать эти операторы для управления потоком выполнения программы и построения сложных условий. Практикуйтесь с этими операторами, чтобы лучше понять, как они работают и как их можно использовать в различных сценариях программирования.

## Навигатор

- [На главную](../index.md)
- [Предыдущий урок](../B02_L03_Math/README.md)
- [Следующий урок](../B02_L05_Strings/README.md)