# Урок 4.2: XAML для WPF

В этом уроке мы рассмотрим основы XAML (eXtensible Application Markup Language) для разработки приложений на платформе Windows Presentation Foundation (WPF).

## Введение в XAML

XAML (eXtensible Application Markup Language) — это декларативный язык разметки, который используется для создания пользовательских интерфейсов в WPF. XAML позволяет описывать элементы управления, макеты и другие аспекты пользовательского интерфейса в формате XML.

### Пример простой XAML-разметки

```xml
<Window x:Class="WpfApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="MainWindow" Height="350" Width="525">
    <Grid>
        <Button Content="Click Me" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Grid>
</Window>
```

## Основные элементы XAML

### Корневой элемент

Корневой элемент XAML-документа определяется типом окна или пользовательского элемента управления, например, `<Window>`, `<UserControl>` и т.д.

### Пример

```xml
<Window x:Class="WpfApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="MainWindow" Height="350" Width="525">
    <!-- Содержимое окна -->
</Window>
```

### Элементы управления

Элементы управления представляют собой компоненты интерфейса, такие как кнопки, текстовые поля, метки и т.д.

### Пример

```xml
<Window x:Class="WpfApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="MainWindow" Height="350" Width="525">
    <Grid>
        <Button Content="Click Me" Width="100" Height="50" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Grid>
</Window>
```

### Атрибуты

Атрибуты определяют свойства элементов управления. Они указываются внутри тега элемента.

### Пример

```xml
<Button Content="Click Me" Width="100" Height="50" HorizontalAlignment="Center" VerticalAlignment="Center"/>
```

## Макеты

WPF поддерживает различные панели для организации макета элементов управления. Наиболее часто используемые панели включают:

### Grid

Grid представляет собой сетку, состоящую из строк и столбцов.

### Пример

```xml
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="Auto"/>
        <ColumnDefinition Width="*"/>
    </Grid.ColumnDefinitions>
    <Button Content="Button 1" Grid.Row="0" Grid.Column="0"/>
    <Button Content="Button 2" Grid.Row="0" Grid.Column="1"/>
    <Button Content="Button 3" Grid.Row="1" Grid.Column="0"/>
    <Button Content="Button 4" Grid.Row="1" Grid.Column="1"/>
</Grid>
```

### StackPanel

StackPanel выстраивает элементы в один ряд горизонтально или вертикально.

### Пример

```xml
<StackPanel Orientation="Vertical">
    <Button Content="Button 1" Width="100" Height="50"/>
    <Button Content="Button 2" Width="100" Height="50"/>
    <Button Content="Button 3" Width="100" Height="50"/>
</StackPanel>
```

### DockPanel

DockPanel выравнивает элементы по краям контейнера.

### Пример

```xml
<DockPanel>
    <Button Content="Top" DockPanel.Dock="Top"/>
    <Button Content="Bottom" DockPanel.Dock="Bottom"/>
    <Button Content="Left" DockPanel.Dock="Left"/>
    <Button Content="Right" DockPanel.Dock="Right"/>
    <Button Content="Center"/>
</DockPanel>
```

### WrapPanel

WrapPanel выстраивает элементы в ряд и переносит на следующую строку или столбец, когда места недостаточно.

### Пример

```xml
<WrapPanel>
    <Button Content="Button 1" Width="100" Height="50"/>
    <Button Content="Button 2" Width="100" Height="50"/>
    <Button Content="Button 3" Width="100" Height="50"/>
    <Button Content="Button 4" Width="100" Height="50"/>
</WrapPanel>
```

## Привязка данных (Data Binding)

Привязка данных позволяет связать элементы управления с данными. Это мощный механизм, который позволяет отделить логику представления от логики данных.

### Пример

#### MainWindow.xaml

```xml
<Window x:Class="WpfApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="MainWindow" Height="350" Width="525">
    <Grid>
        <TextBox Text="{Binding Name}" Width="200" Height="30" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Grid>
</Window>
```

#### MainWindow.xaml.cs

```csharp
using System.Windows;

namespace WpfApp
{
    public partial class MainWindow : Window
    {
        public string Name { get; set; }

        public MainWindow()
        {
            InitializeComponent();
            Name = "John Doe";
            DataContext = this;
        }
    }
}
```

## Ресурсы

Ресурсы в XAML позволяют определять стили, шаблоны и другие повторно используемые элементы.

### Пример

#### Определение ресурсов

```xml
<Window.Resources>
    <SolidColorBrush x:Key="PrimaryBrush" Color="LightBlue"/>
</Window.Resources>
```

#### Использование ресурсов

```xml
<Button Content="Styled Button" Background="{StaticResource PrimaryBrush}" Width="200" Height="50" HorizontalAlignment="Center" VerticalAlignment="Center"/>
```

## Стилей

Стили позволяют задавать внешний вид элементов управления и применять их повторно.

### Пример

#### Определение стиля

```xml
<Window.Resources>
    <Style x:Key="ButtonStyle" TargetType="Button">
        <Setter Property="Background" Value="LightBlue"/>
        <Setter Property="Foreground" Value="White"/>
        <Setter Property="Width" Value="200"/>
        <Setter Property="Height" Value="50"/>
    </Style>
</Window.Resources>
```

#### Применение стиля

```xml
<Button Content="Styled Button" Style="{StaticResource ButtonStyle}" HorizontalAlignment="Center" VerticalAlignment="Center"/>
```

## Триггеры

Триггеры позволяют изменять свойства элементов управления в ответ на изменения других свойств.

### Пример

#### Определение стиля с триггером

```xml
<Window.Resources>
    <Style x:Key="ButtonStyle" TargetType="Button">
        <Setter Property="Background" Value="LightBlue"/>
        <Setter Property="Foreground" Value="White"/>
        <Setter Property="Width" Value="200"/>
        <Setter Property="Height" Value="50"/>
        <Style.Triggers>
            <Trigger Property="IsMouseOver" Value="True">
                <Setter Property="Background" Value="LightGreen"/>
            </Trigger>
        </Style.Triggers>
    </Style>
</Window.Resources>
```

#### Применение стиля с триггером

```xml
<Button Content="Hover Over Me" Style="{StaticResource ButtonStyle}" HorizontalAlignment="Center" VerticalAlignment="Center"/>
```

## Шаблоны данных

Шаблоны данных позволяют определять, как данные должны отображаться в элементах управления.

### Пример

#### Определение шаблона данных

```xml
<Window.Resources>
    <DataTemplate x:Key="PersonTemplate">
        <StackPanel>
            <TextBlock Text="{Binding Name}" FontWeight="Bold"/>
            <TextBlock Text="{Binding Age}"/>
        </StackPanel>
    </DataTemplate>
</Window.Resources>
```

#### Использование шаблона данных

```xml
<ListBox ItemTemplate="{StaticResource PersonTemplate}" ItemsSource="{Binding People}"/>
```

#### MainWindow.xaml.cs

```csharp
using System.Collections.ObjectModel;
using System.Windows;

namespace WpfApp
{
    public partial class MainWindow : Window
    {
        public ObservableCollection<Person> People { get; set; }

        public MainWindow()
        {
            InitializeComponent();
            People = new ObservableCollection<Person>
            {
                new Person { Name = "John Doe", Age = 30 },
                new Person { Name = "Jane Doe", Age = 28 }
            };
            DataContext = this;
        }
    }

    public class Person
    {
        public string Name { get; set; }
        public int Age { get; set; }
    }
}
```

## Заключение

В этом уроке мы рассмотрели основы работы с XAML в WPF, включая создание элементов управления, использование макетов, привязку данных, стили, триггеры и шаблоны данных. XAML предоставляет мощные возможности для создания гибких и многофункциональных пользовательских интерфейсов в WPF. Практикуйтесь с этими примерами, чтобы лучше понять, как использовать XAML для создания настольных приложений на платформе WPF.

## Навигатор

- [На главную](../index.md)
- [Предыдущий урок](../B04_L01_WindowsForm/README.md)
- [Следующий урок](../B04_L03_WPF/README.md)