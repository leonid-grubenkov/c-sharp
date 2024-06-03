# Урок 3.3: Интерфейсы и абстрактные классы

В этом уроке мы рассмотрим концепции интерфейсов и абстрактных классов в C#, их различия, использование и примеры кода.

## Интерфейсы

Интерфейс — это контракт, который определяет набор методов и свойств, которые должны быть реализованы классом. Интерфейсы не содержат реализации методов.

### Объявление интерфейса

Интерфейсы объявляются с использованием ключевого слова `interface`.

### Пример

```csharp
public interface IMovable
{
    void Move();
}
```

### Реализация интерфейса

Класс, который реализует интерфейс, должен реализовать все его методы и свойства.

### Пример

```csharp
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

### Интерфейсы с несколькими методами

Интерфейс может содержать несколько методов и свойств.

### Пример

```csharp
public interface IAnimal
{
    void Speak();
    void Eat();
}

public class Dog : IAnimal
{
    public void Speak()
    {
        Console.WriteLine("The dog barks.");
    }

    public void Eat()
    {
        Console.WriteLine("The dog eats.");
    }
}

public class Cat : IAnimal
{
    public void Speak()
    {
        Console.WriteLine("The cat meows.");
    }

    public void Eat()
    {
        Console.WriteLine("The cat eats.");
    }
}

IAnimal dog = new Dog();
IAnimal cat = new Cat();

dog.Speak(); // The dog barks.
dog.Eat();   // The dog eats.

cat.Speak(); // The cat meows.
cat.Eat();   // The cat eats.
```

### Наследование интерфейсов

Интерфейсы могут наследовать другие интерфейсы.

### Пример

```csharp
public interface IMovable
{
    void Move();
}

public interface IFlyable : IMovable
{
    void Fly();
}

public class Bird : IFlyable
{
    public void Move()
    {
        Console.WriteLine("The bird is moving.");
    }

    public void Fly()
    {
        Console.WriteLine("The bird is flying.");
    }
}

IFlyable bird = new Bird();
bird.Move(); // The bird is moving.
bird.Fly();  // The bird is flying.
```

## Абстрактные классы

Абстрактные классы используются для создания базовых классов, которые могут содержать реализацию некоторых методов, но не могут быть инстанцированы. Абстрактные методы не имеют реализации и должны быть переопределены в производных классах.

### Объявление абстрактного класса

Абстрактные классы объявляются с использованием ключевого слова `abstract`.

### Пример

```csharp
public abstract class Animal
{
    public string Name { get; set; }

    public void Sleep()
    {
        Console.WriteLine($"{Name} is sleeping.");
    }

    public abstract void MakeSound();
}
```

### Реализация абстрактного класса

Класс, который наследует абстрактный класс, должен реализовать все его абстрактные методы.

### Пример

```csharp
public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("The dog barks.");
    }
}

public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("The cat meows.");
    }
}

Dog dog = new Dog { Name = "Buddy" };
Cat cat = new Cat { Name = "Whiskers" };

dog.MakeSound(); // The dog barks.
dog.Sleep();     // Buddy is sleeping.

cat.MakeSound(); // The cat meows.
cat.Sleep();     // Whiskers is sleeping.
```

### Абстрактные методы

Абстрактные методы объявляются без реализации в абстрактном классе и должны быть реализованы в производных классах.

### Пример

```csharp
public abstract class Shape
{
    public abstract double GetArea();
    public abstract double GetPerimeter();
}

public class Circle : Shape
{
    public double Radius { get; set; }

    public Circle(double radius)
    {
        Radius = radius;
    }

    public override double GetArea()
    {
        return Math.PI * Radius * Radius;
    }

    public override double GetPerimeter()
    {
        return 2 * Math.PI * Radius;
    }
}

public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public Rectangle(double width, double height)
    {
        Width = width;
        Height = height;
    }

    public override double GetArea()
    {
        return Width * Height;
    }

    public override double GetPerimeter()
    {
        return 2 * (Width + Height);
    }
}

Circle circle = new Circle(5);
Console.WriteLine($"Circle area: {circle.GetArea()}"); // Circle area: 78.53981633974483
Console.WriteLine($"Circle perimeter: {circle.GetPerimeter()}"); // Circle perimeter: 31.41592653589793

Rectangle rectangle = new Rectangle(4, 7);
Console.WriteLine($"Rectangle area: {rectangle.GetArea()}"); // Rectangle area: 28
Console.WriteLine($"Rectangle perimeter: {rectangle.GetPerimeter()}"); // Rectangle perimeter: 22
```

## Сравнение интерфейсов и абстрактных классов

| Характеристика       | Интерфейсы                               | Абстрактные классы                         |
|----------------------|------------------------------------------|-------------------------------------------|
| Множественное наследование | Класс может реализовать несколько интерфейсов | Класс может наследовать только один абстрактный класс |
| Реализация методов   | Не содержит реализацию                   | Может содержать реализацию методов         |
| Конструкторы         | Не может содержать конструкторы          | Может содержать конструкторы              |

### Пример: Интерфейсы и абстрактные классы вместе

```csharp
public interface IMovable
{
    void Move();
}

public abstract class Animal : IMovable
{
    public string Name { get; set; }

    public abstract void MakeSound();

    public void Move()
    {
        Console.WriteLine($"{Name} is moving.");
    }
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("The dog barks.");
    }
}

Dog dog = new Dog { Name = "Buddy" };
dog.Move();      // Buddy is moving.
dog.MakeSound(); // The dog barks.
```

## Заключение

В этом уроке мы рассмотрели основные концепции интерфейсов и абстрактных классов в C#. Мы узнали, как объявлять и реализовывать интерфейсы, а также как использовать абстрактные классы и методы. Интерфейсы и абстрактные классы позволяют создавать гибкие и масштабируемые архитектуры, обеспечивая при этом полиморфизм и повторное использование кода. Практикуйтесь с этими примерами, чтобы лучше понять их применение в различных сценариях программирования.

## Навигатор

- [На главную](../index.md)
- [Предыдущий урок](../B03_L02_Extends/README.md)
- [Следующий урок](../B03_L03_Interface/README.md)