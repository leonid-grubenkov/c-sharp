# Урок 2.10: Работа с коллекциями в C#

В этом уроке мы рассмотрим основные коллекции, доступные в C#, включая `List`, `Dictionary`, `Stack` и `Queue`.

## List

`List` — это динамический массив, который может изменять свой размер. Он предоставляет методы для добавления, удаления и управления элементами.

### Объявление и инициализация

```csharp
List<int> numbers = new List<int>();
```

### Добавление элементов

```csharp
numbers.Add(1);
numbers.Add(2);
numbers.Add(3);
```

### Доступ к элементам

```csharp
int firstNumber = numbers[0];
Console.WriteLine(firstNumber); // 1
```

### Перебор элементов

```csharp
foreach (int number in numbers)
{
    Console.WriteLine(number);
}
```

### Удаление элементов

```csharp
numbers.Remove(2); // Удаляет первое вхождение значения 2
numbers.RemoveAt(0); // Удаляет элемент по индексу 0
```

### Пример использования `List`

```csharp
List<string> names = new List<string> { "Alice", "Bob", "Charlie" };
names.Add("David");

foreach (string name in names)
{
    Console.WriteLine(name);
}
```

## Dictionary

`Dictionary` представляет собой коллекцию пар "ключ-значение". Ключи должны быть уникальными.

### Объявление и инициализация

```csharp
Dictionary<int, string> students = new Dictionary<int, string>();
```

### Добавление элементов

```csharp
students.Add(1, "Alice");
students.Add(2, "Bob");
students[3] = "Charlie"; // Альтернативный способ добавления
```

### Доступ к элементам

```csharp
string studentName = students[1];
Console.WriteLine(studentName); // Alice
```

### Перебор элементов

```csharp
foreach (KeyValuePair<int, string> student in students)
{
    Console.WriteLine($"ID: {student.Key}, Name: {student.Value}");
}
```

### Удаление элементов

```csharp
students.Remove(2); // Удаляет элемент с ключом 2
```

### Пример использования `Dictionary`

```csharp
Dictionary<string, int> phoneBook = new Dictionary<string, int>
{
    { "Alice", 123456 },
    { "Bob", 654321 }
};

phoneBook["Charlie"] = 987654;

foreach (var entry in phoneBook)
{
    Console.WriteLine($"{entry.Key}: {entry.Value}");
}
```

## Stack (FILO)

`Stack` (стек) — это коллекция, работающая по принципу "последний пришел — первый ушел" (FILO).

### Объявление и инициализация

```csharp
Stack<int> stack = new Stack<int>();
```

### Добавление элементов (Push)

```csharp
stack.Push(1);
stack.Push(2);
stack.Push(3);
```

### Извлечение элементов (Pop)

```csharp
int topElement = stack.Pop();
Console.WriteLine(topElement); // 3
```

### Просмотр верхнего элемента (Peek)

```csharp
int peekElement = stack.Peek();
Console.WriteLine(peekElement); // 2
```

### Перебор элементов

```csharp
foreach (int element in stack)
{
    Console.WriteLine(element);
}
```

### Пример использования `Stack`

```csharp
Stack<string> books = new Stack<string>();
books.Push("Book 1");
books.Push("Book 2");
books.Push("Book 3");

Console.WriteLine($"Top book: {books.Peek()}"); // Top book: Book 3

while (books.Count > 0)
{
    Console.WriteLine(books.Pop());
}
```

## Queue (FIFO)

`Queue` (очередь) — это коллекция, работающая по принципу "первый пришел — первый ушел" (FIFO).

### Объявление и инициализация

```csharp
Queue<int> queue = new Queue<int>();
```

### Добавление элементов (Enqueue)

```csharp
queue.Enqueue(1);
queue.Enqueue(2);
queue.Enqueue(3);
```

### Извлечение элементов (Dequeue)

```csharp
int firstElement = queue.Dequeue();
Console.WriteLine(firstElement); // 1
```

### Просмотр первого элемента (Peek)

```csharp
int peekElement = queue.Peek();
Console.WriteLine(peekElement); // 2
```

### Перебор элементов

```csharp
foreach (int element in queue)
{
    Console.WriteLine(element);
}
```

### Пример использования `Queue`

```csharp
Queue<string> line = new Queue<string>();
line.Enqueue("Person 1");
line.Enqueue("Person 2");
line.Enqueue("Person 3");

Console.WriteLine($"First in line: {line.Peek()}"); // First in line: Person 1

while (line.Count > 0)
{
    Console.WriteLine(line.Dequeue());
}
```

## Заключение

В этом уроке мы рассмотрели основные коллекции в C#:
- `List`: динамический массив для хранения элементов.
- `Dictionary`: коллекция пар "ключ-значение".
- `Stack`: коллекция с принципом "последний пришел — первый ушел" (FILO).
- `Queue`: коллекция с принципом "первый пришел — первый ушел" (FIFO).

Эти коллекции предоставляют гибкость и мощные инструменты для управления данными в приложениях. Практикуйтесь с этими коллекциями, чтобы лучше понять их работу и применение в различных сценариях программирования.

## Навигатор

- [На главную](../index.md)
- [Предыдущий урок](../B02_L09_Ref_Out/README.md)
- [Следующий урок](../B03_L01_Classes/README.md)