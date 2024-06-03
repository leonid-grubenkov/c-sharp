# Урок 4.3: WPF (Windows Presentation Foundation)

В этом уроке мы рассмотрим основы работы с WPF в C#. WPF — это мощная платформа для создания настольных приложений с графическим интерфейсом пользователя (GUI) на Windows.

## Создание WPF проекта

Чтобы создать проект WPF в Visual Studio, выполните следующие шаги:
1. Откройте Visual Studio.
2. Выберите "Создать новый проект".
3. В списке шаблонов выберите "WPF App (.NET Framework)".
4. Укажите имя и расположение проекта и нажмите "Создать".

## Основные элементы WPF

### XAML

XAML (eXtensible Application Markup Language) используется для определения пользовательского интерфейса в WPF. Это декларативный язык разметки, который позволяет описывать элементы управления и их свойства.

### Пример простой WPF формы

#### MainWindow.xaml

```xml
<Window x:Class="WpfApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="MainWindow" Height="350" Width="525">
    <Grid>
        <Button Name="myButton" Content="Click Me" Width="100" Height="50" HorizontalAlignment="Center" VerticalAlignment="Center" Click="MyButton_Click"/>
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
        public MainWindow()
        {
            InitializeComponent();
        }

        private void MyButton_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Button clicked!");
        }
    }
}
```

### Пример с несколькими элементами управления

#### MainWindow.xaml

```xml
<Window x:Class="WpfApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="MainWindow" Height="350" Width="525">
    <Grid>
        <StackPanel>
            <TextBlock Text="Enter your name:" Margin="10"/>
            <TextBox Name="nameTextBox" Margin="10"/>
            <Button Content="Submit" Margin="10" Click="SubmitButton_Click"/>
            <TextBlock Name="greetingTextBlock" Margin="10"/>
        </StackPanel>
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
        public MainWindow()
        {
            InitializeComponent();
        }

        private void SubmitButton_Click(object sender, RoutedEventArgs e)
        {
            string name = nameTextBox.Text;
            greetingTextBlock.Text = $"Hello, {name}!";
        }
    }
}
```

## Пример 1: Простое приложение WPF

### Описание

Простое приложение с кнопкой и текстовым полем. При нажатии кнопки отображается сообщение с введенным текстом.

### MainWindow.xaml

```xml
<Window x:Class="WpfApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="MainWindow" Height="350" Width="525">
    <Grid>
        <StackPanel>
            <TextBlock Text="Enter your name:" Margin="10"/>
            <TextBox Name="nameTextBox" Margin="10"/>
            <Button Content="Show Message" Margin="10" Click="ShowMessageButton_Click"/>
        </StackPanel>
    </Grid>
</Window>
```

### MainWindow.xaml.cs

```csharp
using System.Windows;

namespace WpfApp
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void ShowMessageButton_Click(object sender, RoutedEventArgs e)
        {
            string name = nameTextBox.Text;
            MessageBox.Show($"Hello, {name}!");
        }
    }
}
```

## Пример 2: Калькулятор

### Описание

Простое приложение-калькулятор с двумя текстовыми полями и кнопками для выполнения операций сложения, вычитания, умножения и деления.

### MainWindow.xaml

```xml
<Window x:Class="WpfApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Calculator" Height="400" Width="400">
    <Grid>
        <StackPanel>
            <TextBlock Text="Number 1:" Margin="10"/>
            <TextBox Name="number1TextBox" Margin="10"/>
            <TextBlock Text="Number 2:" Margin="10"/>
            <TextBox Name="number2TextBox" Margin="10"/>
            <StackPanel Orientation="Horizontal" HorizontalAlignment="Center">
                <Button Content="Add" Margin="5" Click="AddButton_Click"/>
                <Button Content="Subtract" Margin="5" Click="SubtractButton_Click"/>
                <Button Content="Multiply" Margin="5" Click="MultiplyButton_Click"/>
                <Button Content="Divide" Margin="5" Click="DivideButton_Click"/>
            </StackPanel>
            <TextBlock Name="resultTextBlock" Margin="10" FontWeight="Bold"/>
        </StackPanel>
    </Grid>
</Window>
```

### MainWindow.xaml.cs

```csharp
using System;
using System.Windows;

namespace WpfApp
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void AddButton_Click(object sender, RoutedEventArgs e)
        {
            if (double.TryParse(number1TextBox.Text, out double num1) && double.TryParse(number2TextBox.Text, out double num2))
            {
                double result = num1 + num2;
                resultTextBlock.Text = $"Result: {result}";
            }
            else
            {
                MessageBox.Show("Please enter valid numbers.");
            }
        }

        private void SubtractButton_Click(object sender, RoutedEventArgs e)
        {
            if (double.TryParse(number1TextBox.Text, out double num1) && double.TryParse(number2TextBox.Text, out double num2))
            {
                double result = num1 - num2;
                resultTextBlock.Text = $"Result: {result}";
            }
            else
            {
                MessageBox.Show("Please enter valid numbers.");
            }
        }

        private void MultiplyButton_Click(object sender, RoutedEventArgs e)
        {
            if (double.TryParse(number1TextBox.Text, out double num1) && double.TryParse(number2TextBox.Text, out double num2))
            {
                double result = num1 * num2;
                resultTextBlock.Text = $"Result: {result}";
            }
            else
            {
                MessageBox.Show("Please enter valid numbers.");
            }
        }

        private void DivideButton_Click(object sender, RoutedEventArgs e)
        {
            if (double.TryParse(number1TextBox.Text, out double num1) && double.TryParse(number2TextBox.Text, out double num2))
            {
                if (num2 != 0)
                {
                    double result = num1 / num2;
                    resultTextBlock.Text = $"Result: {result}";
                }
                else
                {
                    MessageBox.Show("Cannot divide by zero.");
                }
            }
            else
            {
                MessageBox.Show("Please enter valid numbers.");
            }
        }
    }
}
```

## Пример 3: Приложение с ListBox и DataGridView

### Описание

Приложение, которое отображает список элементов в ListBox и позволяет добавлять их в DataGridView.

### MainWindow.xaml

```xml
<Window x:Class="WpfApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="ListBox and DataGrid Example" Height="400" Width="600">
    <Grid>
        <StackPanel>
            <StackPanel Orientation="Horizontal">
                <ListBox Name="listBox" Width="200" Height="200" Margin="10"/>
                <DataGrid Name="dataGrid" Width="300" Height="200" Margin="10"/>
            </StackPanel>
            <StackPanel Orientation="Horizontal">
                <TextBox Name="inputTextBox" Width="200" Margin="10"/>
                <Button Content="Add to ListBox" Margin="10" Click="AddToListBoxButton_Click"/>
                <Button Content="Add to DataGrid" Margin="10" Click="AddToDataGridButton_Click"/>
            </StackPanel>
        </StackPanel>
    </Grid>
</Window>
```

### MainWindow.xaml.cs

```csharp
using System.Windows;
using System.Windows.Controls;

namespace WpfApp
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
            dataGrid.Columns.Add(new DataGridTextColumn { Header = "Item", Binding = new System.Windows.Data.Binding("Content") });
        }

        private void AddToListBoxButton_Click(object sender, RoutedEventArgs e)
        {
            string item = inputTextBox.Text;
            if (!string.IsNullOrWhiteSpace(item))
            {
                listBox.Items.Add(item);
                inputTextBox.Clear();
            }
        }

        private void AddToDataGridButton_Click(object sender, RoutedEventArgs e)
        {
            if (listBox.SelectedItem != null)
            {
                dataGrid.Items.Add(listBox.SelectedItem);
            }
        }
    }
}
```

## Заключение

В этом уроке мы рассмотрели основы создания приложений WPF на языке C#. Мы узнали, как создавать и инициализировать элементы управления с помощью XAML, добавлять обработчики событий и связывать элементы управления с кодом. Мы также создали простые приложения, такие как калькулятор и приложение с ListBox и DataGrid. Практикуйтесь с этими примерами, чтобы лучше понять, как создавать настольные приложения с графическим интерфейсом пользователя на платформе WPF.


## Навигатор

- [На главную](../index.md)
- [Предыдущий урок](../B04_L02_xaml/README.md)