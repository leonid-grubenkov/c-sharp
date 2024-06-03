# Урок 2.8: Работа с функциями в C#

В этом уроке мы рассмотрим работу с функциями в C#, включая объявление и вызов функций, параметры и возвращаемые значения, перегрузку функций, а также локальные функции и функции высшего порядка.

## Основы функций

### Объявление функции

Функции в C# объявляются с указанием типа возвращаемого значения, имени функции и параметров (если они есть).

#### Синтаксис

```csharp
тип_возвращаемого_значения ИмяФункции(параметры)
{
    // Тело функции
}
```

### Пример

```csharp
public int Add(int a, int b)
{
    return a + b;
}
```

### Вызов функции

Функции вызываются по их имени с указанием аргументов в круглых скобках.

```csharp
int result = Add(3, 4); // Вызов функции Add с аргументами 3 и 4
Console.WriteLine(result); // 7
```

## Параметры функций

Функции могут принимать параметры, которые передаются им при вызове.

### Параметры по значению

По умолчанию параметры передаются по значению, что означает, что изменения параметров внутри функции не влияют на их значения снаружи.

```csharp
public void Increment(int number)
{
    number++;
}

int myNumber = 5;
Increment(myNumber);
Console.WriteLine(myNumber); // 5
```

### Параметры по ссылке

Параметры могут быть переданы по ссылке с использованием ключевого слова `ref`. Это позволяет функции изменять значения параметров.

```csharp
public void Increment(ref int number)
{
    number++;
}

int myNumber = 5;
Increment(ref myNumber);
Console.WriteLine(myNumber); // 6
```

### Выходные параметры

Выходные параметры используются для возврата нескольких значений из функции. Они объявляются с использованием ключевого слова `out`.

```csharp
public void GetValues(out int a, out int b)
{
    a = 10;
    b = 20;
}

GetValues(out int x, out int y);
Console.WriteLine($"x = {x}, y = {y}"); // x = 10, y = 20
```

### Параметры по умолчанию

Функции могут иметь параметры по умолчанию, которые используются, если соответствующие аргументы не были переданы.

```csharp
public void Greet(string name = "Guest")
{
    Console.WriteLine($"Hello, {name}!");
}

Greet(); // Hello, Guest!
Greet("Alice"); // Hello, Alice!
```

## Возвращаемые значения

Функции могут возвращать значения, используя ключевое слово `return`.

### Пример

```csharp
public int Multiply(int a, int b)
{
    return a * b;
}

int result = Multiply(3, 4);
Console.WriteLine(result); // 12
```

### Возврат нескольких значений

Для возврата нескольких значений можно использовать кортежи.

```csharp
public (int, int) GetCoordinates()
{
    return (10, 20);
}

var coordinates = GetCoordinates();
Console.WriteLine($"x = {coordinates.Item1}, y = {coordinates.Item2}"); // x = 10, y = 20
```

## Перегрузка функций

Перегрузка функций позволяет объявлять несколько функций с одним и тем же именем, но с разными параметрами.

### Пример

```csharp
public void Print(int number)
{
    Console.WriteLine($"Number: {number}");
}

public void Print(string text)
{
    Console.WriteLine($"Text: {text}");
}

Print(5); // Number: 5
Print("Hello"); // Text: Hello
```

## Локальные функции

Локальные функции объявляются внутри других функций и могут использовать их параметры и локальные переменные.

### Пример

```csharp
public void OuterFunction()
{
    int outerVariable = 10;

    void InnerFunction()
    {
        Console.WriteLine($"Outer variable: {outerVariable}");
    }

    InnerFunction();
}

OuterFunction(); // Outer variable: 10
```

## Функции высшего порядка

Функции высшего порядка принимают другие функции в качестве параметров или возвращают функции.

### Пример

```csharp
public void ExecuteAction(Action action)
{
    action();
}

void SayHello()
{
    Console.WriteLine("Hello!");
}

ExecuteAction(SayHello); // Hello!
```

## Анонимные функции и лямбда-выражения

### Анонимные функции

Анонимные функции создаются с использованием ключевого слова `delegate`.

```csharp
Action greet = delegate
{
    Console.WriteLine("Hello from anonymous function!");
};

greet(); // Hello from anonymous function!
```

### Лямбда-выражения

Лямбда-выражения представляют собой короткий синтаксис для создания анонимных функций.

```csharp
Action greet = () => Console.WriteLine("Hello from lambda!");
greet(); // Hello from lambda!

Func<int, int, int> add = (a, b) => a + b;
int result = add(3, 4);
Console.WriteLine(result); // 7
```

## Рекурсивные функции

Рекурсивные функции вызывают сами себя. Важно, чтобы рекурсивная функция имела условие выхода, чтобы избежать бесконечной рекурсии.

### Пример

Функция для вычисления факториала числа.

```csharp
public int Factorial(int n)
{
    if (n <= 1)
        return 1;
    else
        return n * Factorial(n - 1);
}

int result = Factorial(5);
Console.WriteLine(result); // 120
```

## Заключение

В этом уроке мы рассмотрели основные аспекты работы с функциями в C#, включая объявление и вызов функций, параметры и возвращаемые значения, перегрузку функций, локальные функции, функции высшего порядка, анонимные функции и лямбда-выражения, а также рекурсивные функции. Эти знания являются фундаментальными для разработки приложений на C# и позволяют создавать эффективный и модульный код.

## Навигатор

- [На главную](../index.md)
- [Предыдущий урок](../B02_L07_Arrays/README.md)
- [Следующий урок](../B02_L09_Ref_Out/README.md)