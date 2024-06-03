# Урок 3.2: Наследование и полиморфизм

В этом уроке мы рассмотрим основные концепции наследования и полиморфизма в языке программирования C#.

## Наследование

Наследование позволяет создавать новые классы на основе существующих. Новый класс (производный или подкласс) наследует члены существующего класса (базового или суперкласса), что позволяет повторно использовать код и упрощать его.

### Основы наследования

Для объявления наследования используется двоеточие `:` после имени производного класса.

### Пример

```csharp
public class Animal
{
    public string Name { get; set; }

    public void Eat()
    {
        Console.WriteLine($"{Name} is eating.");
    }
}

public class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine($"{Name} is barking.");
    }
}

public class Cat : Animal
{
    public void Meow()
    {
        Console.WriteLine($"{Name} is meowing.");
    }
}

Dog dog = new Dog();
dog.Name = "Buddy";
dog.Eat(); // Buddy is eating.
dog.Bark(); // Buddy is barking.

Cat cat = new Cat();
cat.Name = "Whiskers";
cat.Eat(); // Whiskers is eating.
cat.Meow(); // Whiskers is meowing.
```

### Модификаторы доступа и наследование

Члены класса с модификатором доступа `private` не наследуются производными классами. Члены с модификаторами `protected`, `internal` и `public` наследуются.

### Пример

```csharp
public class Animal
{
    private int age;
    protected string Name { get; set; }

    public void SetAge(int age)
    {
        this.age = age;
    }

    public void GetInfo()
    {
        Console.WriteLine($"Name: {Name}, Age: {age}");
    }
}

public class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine($"{Name} is barking.");
    }
}

Dog dog = new Dog();
dog.SetAge(3);
dog.GetInfo(); // Name: null, Age: 3
```

## Полиморфизм

Полиморфизм позволяет использовать объекты производных классов через ссылки на базовый класс, что позволяет вызывать переопределенные методы.

### Виртуальные методы и переопределение

Для создания полиморфного поведения методы в базовом классе объявляются как `virtual`, а в производном классе они переопределяются с помощью ключевого слова `override`.

### Пример

```csharp
public class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("The animal makes a sound.");
    }
}

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

Animal myDog = new Dog();
Animal myCat = new Cat();

myDog.MakeSound(); // The dog barks.
myCat.MakeSound(); // The cat meows.
```

### Абстрактные классы и методы

Абстрактные классы не могут быть инстанцированы и служат только для создания базовых классов. Абстрактные методы не имеют реализации в базовом классе и должны быть переопределены в производных классах.

### Пример

```csharp
public abstract class Animal
{
    public string Name { get; set; }
    public abstract void MakeSound();
}

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

Animal myDog = new Dog { Name = "Buddy" };
Animal myCat = new Cat { Name = "Whiskers" };

myDog.MakeSound(); // The dog barks.
myCat.MakeSound(); // The cat meows.
```

## Преобразование типов и оператор `is`

Оператор `is` используется для проверки совместимости объекта с определенным типом. Преобразование типов позволяет явно приводить объекты одного типа к другому, если они находятся в иерархии наследования.

### Пример

```csharp
Animal animal = new Dog { Name = "Buddy" };

if (animal is Dog)
{
    Dog dog = (Dog)animal;
    dog.Bark(); // Buddy is barking.
}
```

### Оператор `as`

Оператор `as` используется для безопасного преобразования типов. Если преобразование невозможно, он возвращает `null`.

### Пример

```csharp
Animal animal = new Cat { Name = "Whiskers" };

Dog dog = animal as Dog;
if (dog != null)
{
    dog.Bark();
}
else
{
    Console.WriteLine("The animal is not a dog.");
}
```

## Интерфейсы

Интерфейсы определяют контракт, который должен быть реализован классами. Интерфейсы позволяют добиться полиморфизма без использования наследования.

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

## Пример полиморфизма с интерфейсами

Интерфейсы позволяют использовать различные реализации через один и тот же интерфейс.

### Пример

```csharp
public interface IAnimal
{
    void Speak();
}

public class Dog : IAnimal
{
    public void Speak()
    {
        Console.WriteLine("The dog barks.");
    }
}

public class Cat : IAnimal
{
    public void Speak()
    {
        Console.WriteLine("The cat meows.");
    }
}

public class Bird : IAnimal
{
    public void Speak()
    {
        Console.WriteLine("The bird sings.");
    }
}

IAnimal[] animals = new IAnimal[] { new Dog(), new Cat(), new Bird() };

foreach (IAnimal animal in animals)
{
    animal.Speak();
}
```

## Заключение

В этом уроке мы рассмотрели основные концепции наследования и полиморфизма в C#. Мы узнали, как создавать базовые и производные классы, использовать виртуальные и абстрактные методы, проверять и преобразовывать типы, а также реализовывать интерфейсы. Эти концепции являются фундаментом объектно-ориентированного программирования и позволяют создавать гибкие и расширяемые приложения. Практикуйтесь с этими примерами, чтобы лучше понять их применение в различных сценариях программирования.

## Навигатор

- [На главную](../index.md)
- [Предыдущий урок](../B03_L01_Classes/README.md)
- [Следующий урок](../B03_L03_Interface/README.md)