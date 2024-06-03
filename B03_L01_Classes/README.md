# Урок 3.1: Классы и объекты

В этом уроке мы рассмотрим основные концепции классов и объектов в языке программирования C#.

## Введение

Классы и объекты являются основой объектно-ориентированного программирования (ООП) в C#. Класс — это шаблон или чертеж для создания объектов. Объект — это экземпляр класса.

## Объявление классов

Класс объявляется с использованием ключевого слова `class`, за которым следует имя класса. Тело класса заключено в фигурные скобки.

### Пример

```csharp
public class Person
{
    // Поля
    public string Name;
    public int Age;

    // Метод
    public void SayHello()
    {
        Console.WriteLine($"Hello, my name is {Name} and I am {Age} years old.");
    }
}
```

## Создание объектов

Объект создается с использованием ключевого слова `new`, за которым следует имя класса и круглые скобки.

### Пример

```csharp
Person person = new Person();
person.Name = "Alice";
person.Age = 30;
person.SayHello(); // Hello, my name is Alice and I am 30 years old.
```

## Конструкторы

Конструктор — это специальный метод, который вызывается при создании объекта. Он инициализирует поля и свойства объекта.

### Пример

```csharp
public class Person
{
    public string Name;
    public int Age;

    // Конструктор
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    public void SayHello()
    {
        Console.WriteLine($"Hello, my name is {Name} and I am {Age} years old.");
    }
}

Person person = new Person("Bob", 25);
person.SayHello(); // Hello, my name is Bob and I am 25 years old.
```

## Свойства

Свойства позволяют управлять доступом к полям класса. Они состоят из методов доступа (геттер и сеттер).

### Пример

```csharp
public class Person
{
    private string name;
    private int age;

    public string Name
    {
        get { return name; }
        set { name = value; }
    }

    public int Age
    {
        get { return age; }
        set
        {
            if (value > 0)
            {
                age = value;
            }
        }
    }

    public void SayHello()
    {
        Console.WriteLine($"Hello, my name is {Name} and I am {Age} years old.");
    }
}

Person person = new Person();
person.Name = "Charlie";
person.Age = 35;
person.SayHello(); // Hello, my name is Charlie and I am 35 years old.
```

## Модификаторы доступа

Модификаторы доступа определяют уровень доступа к членам класса (полям, методам, свойствам).

- `public`: доступен из любого места.
- `private`: доступен только внутри текущего класса.
- `protected`: доступен внутри текущего класса и подклассов.
- `internal`: доступен внутри текущей сборки (assembly).
- `protected internal`: доступен внутри текущей сборки и из производных классов.

### Пример

```csharp
public class Person
{
    private string name;
    protected int age;
    public string Name { get; set; }

    public void Display()
    {
        Console.WriteLine($"Name: {Name}, Age: {age}");
    }
}

public class Employee : Person
{
    public int EmployeeId { get; set; }

    public void ShowDetails()
    {
        Console.WriteLine($"Employee ID: {EmployeeId}, Name: {Name}, Age: {age}");
    }
}
```

## Наследование

Наследование позволяет создать новый класс на основе существующего. Новый класс наследует члены базового класса.

### Пример

```csharp
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    public void SayHello()
    {
        Console.WriteLine($"Hello, my name is {Name} and I am {Age} years old.");
    }
}

public class Employee : Person
{
    public int EmployeeId { get; set; }

    public void Work()
    {
        Console.WriteLine($"Employee {Name} is working.");
    }
}

Employee employee = new Employee();
employee.Name = "Diana";
employee.Age = 28;
employee.EmployeeId = 12345;
employee.SayHello(); // Hello, my name is Diana and I am 28 years old.
employee.Work(); // Employee Diana is working.
```

## Полиморфизм

Полиморфизм позволяет использовать методы производных классов через ссылку на базовый класс.

### Пример

```csharp
public class Person
{
    public virtual void Greet()
    {
        Console.WriteLine("Hello!");
    }
}

public class Student : Person
{
    public override void Greet()
    {
        Console.WriteLine("Hi, I'm a student.");
    }
}

public class Teacher : Person
{
    public override void Greet()
    {
        Console.WriteLine("Good morning, I'm a teacher.");
    }
}

Person student = new Student();
Person teacher = new Teacher();

student.Greet(); // Hi, I'm a student.
teacher.Greet(); // Good morning, I'm a teacher.
```

## Абстрактные классы и методы

Абстрактные классы не могут быть инстанцированы. Они предназначены для создания базовых классов, которые должны быть унаследованы. Абстрактные методы не имеют реализации и должны быть переопределены в производных классах.

### Пример

```csharp
public abstract class Animal
{
    public abstract void MakeSound();
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Bark!");
    }
}

public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Meow!");
    }
}

Animal dog = new Dog();
Animal cat = new Cat();

dog.MakeSound(); // Bark!
cat.MakeSound(); // Meow!
```

## Интерфейсы

Интерфейс — это контракт, который определяет набор методов и свойств, которые должны быть реализованы классом. Интерфейсы не содержат реализацию.

### Пример

```csharp
public interface IMovable
{
    void Move();
}

public class Car : IMovable
{
    public void Move()
    {
        Console.WriteLine("The car is moving.");
    }
}

public class Person : IMovable
{
    public void Move()
    {
        Console.WriteLine("The person is walking.");
    }
}

IMovable car = new Car();
IMovable person = new Person();

car.Move(); // The car is moving.
person.Move(); // The person is walking.
```

## Заключение

В этом уроке мы рассмотрели основные концепции классов и объектов в C#. Мы узнали, как объявлять классы, создавать объекты, использовать конструкторы, свойства, модификаторы доступа, наследование, полиморфизм, абстрактные классы и методы, а также интерфейсы. Эти концепции являются основой объектно-ориентированного программирования и позволяют создавать гибкие и масштабируемые приложения. Практикуйтесь с этими примерами, чтобы лучше понять их применение в различных сценариях программирования.


## Навигатор

- [На главную](../index.md)
- [Предыдущий урок](../B02_L10_Collections/README.md)
- [Следующий урок](../B03_L02_Extends/README.md)