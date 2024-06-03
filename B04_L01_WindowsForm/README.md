# Урок 4.1: Windows Forms

В этом уроке мы рассмотрим основы разработки приложений Windows Forms на языке C#. Windows Forms - это платформа для создания настольных приложений с графическим интерфейсом пользователя (GUI) для Windows.

## Создание Windows Forms проекта

Чтобы создать проект Windows Forms в Visual Studio, выполните следующие шаги:
1. Откройте Visual Studio.
2. Выберите "Создать новый проект".
3. В списке шаблонов выберите "Windows Forms App (.NET Framework)".
4. Укажите имя и расположение проекта и нажмите "Создать".

## Основные элементы Windows Forms

### Форма (Form)

Форма является основным контейнером для других элементов управления.

#### Пример создания формы

```csharp
public partial class MainForm : Form
{
    public MainForm()
    {
        InitializeComponent();
    }
}
```

### Кнопка (Button)

Кнопка позволяет пользователю выполнять действие при нажатии.

#### Пример добавления кнопки на форму

```csharp
public partial class MainForm : Form
{
    private Button button1;

    public MainForm()
    {
        InitializeComponent();
        InitializeCustomComponents();
    }

    private void InitializeCustomComponents()
    {
        button1 = new Button();
        button1.Text = "Click Me";
        button1.Location = new Point(50, 50);
        button1.Click += Button1_Click;
        Controls.Add(button1);
    }

    private void Button1_Click(object sender, EventArgs e)
    {
        MessageBox.Show("Button clicked!");
    }
}
```

### Текстовое поле (TextBox)

Текстовое поле позволяет пользователю вводить текст.

#### Пример добавления текстового поля на форму

```csharp
public partial class MainForm : Form
{
    private TextBox textBox1;

    public MainForm()
    {
        InitializeComponent();
        InitializeCustomComponents();
    }

    private void InitializeCustomComponents()
    {
        textBox1 = new TextBox();
        textBox1.Location = new Point(50, 100);
        Controls.Add(textBox1);
    }
}
```

### Метка (Label)

Метка используется для отображения текста на форме.

#### Пример добавления метки на форму

```csharp
public partial class MainForm : Form
{
    private Label label1;

    public MainForm()
    {
        InitializeComponent();
        InitializeCustomComponents();
    }

    private void InitializeCustomComponents()
    {
        label1 = new Label();
        label1.Text = "Enter your name:";
        label1.Location = new Point(50, 80);
        Controls.Add(label1);
    }
}
```

## Пример 1: Простое приложение Windows Forms

### Описание

Простое приложение с кнопкой и текстовым полем. При нажатии кнопки отображается сообщение с введенным текстом.

### Код

```csharp
public partial class MainForm : Form
{
    private Button button1;
    private TextBox textBox1;
    private Label label1;

    public MainForm()
    {
        InitializeComponent();
        InitializeCustomComponents();
    }

    private void InitializeCustomComponents()
    {
        label1 = new Label();
        label1.Text = "Enter your name:";
        label1.Location = new Point(50, 50);
        Controls.Add(label1);

        textBox1 = new TextBox();
        textBox1.Location = new Point(50, 80);
        Controls.Add(textBox1);

        button1 = new Button();
        button1.Text = "Show Message";
        button1.Location = new Point(50, 110);
        button1.Click += Button1_Click;
        Controls.Add(button1);
    }

    private void Button1_Click(object sender, EventArgs e)
    {
        string name = textBox1.Text;
        MessageBox.Show($"Hello, {name}!");
    }
}
```

## Пример 2: Калькулятор

### Описание

Простое приложение-калькулятор с двумя текстовыми полями и кнопками для выполнения операций сложения, вычитания, умножения и деления.

### Код

```csharp
public partial class MainForm : Form
{
    private TextBox textBox1;
    private TextBox textBox2;
    private Label label1;
    private Label label2;
    private Button addButton;
    private Button subtractButton;
    private Button multiplyButton;
    private Button divideButton;
    private Label resultLabel;

    public MainForm()
    {
        InitializeComponent();
        InitializeCustomComponents();
    }

    private void InitializeCustomComponents()
    {
        label1 = new Label();
        label1.Text = "Number 1:";
        label1.Location = new Point(50, 20);
        Controls.Add(label1);

        textBox1 = new TextBox();
        textBox1.Location = new Point(120, 20);
        Controls.Add(textBox1);

        label2 = new Label();
        label2.Text = "Number 2:";
        label2.Location = new Point(50, 50);
        Controls.Add(label2);

        textBox2 = new TextBox();
        textBox2.Location = new Point(120, 50);
        Controls.Add(textBox2);

        addButton = new Button();
        addButton.Text = "Add";
        addButton.Location = new Point(50, 80);
        addButton.Click += AddButton_Click;
        Controls.Add(addButton);

        subtractButton = new Button();
        subtractButton.Text = "Subtract";
        subtractButton.Location = new Point(130, 80);
        subtractButton.Click += SubtractButton_Click;
        Controls.Add(subtractButton);

        multiplyButton = new Button();
        multiplyButton.Text = "Multiply";
        multiplyButton.Location = new Point(230, 80);
        multiplyButton.Click += MultiplyButton_Click;
        Controls.Add(multiplyButton);

        divideButton = new Button();
        divideButton.Text = "Divide";
        divideButton.Location = new Point(330, 80);
        divideButton.Click += DivideButton_Click;
        Controls.Add(divideButton);

        resultLabel = new Label();
        resultLabel.Text = "Result:";
        resultLabel.Location = new Point(50, 120);
        Controls.Add(resultLabel);
    }

    private void AddButton_Click(object sender, EventArgs e)
    {
        if (double.TryParse(textBox1.Text, out double num1) && double.TryParse(textBox2.Text, out double num2))
        {
            double result = num1 + num2;
            resultLabel.Text = $"Result: {result}";
        }
        else
        {
            MessageBox.Show("Please enter valid numbers.");
        }
    }

    private void SubtractButton_Click(object sender, EventArgs e)
    {
        if (double.TryParse(textBox1.Text, out double num1) && double.TryParse(textBox2.Text, out double num2))
        {
            double result = num1 - num2;
            resultLabel.Text = $"Result: {result}";
        }
        else
        {
            MessageBox.Show("Please enter valid numbers.");
        }
    }

    private void MultiplyButton_Click(object sender, EventArgs e)
    {
        if (double.TryParse(textBox1.Text, out double num1) && double.TryParse(textBox2.Text, out double num2))
        {
            double result = num1 * num2;
            resultLabel.Text = $"Result: {result}";
        }
        else
        {
            MessageBox.Show("Please enter valid numbers.");
        }
    }

    private void DivideButton_Click(object sender, EventArgs e)
    {
        if (double.TryParse(textBox1.Text, out double num1) && double.TryParse(textBox2.Text, out double num2))
        {
            if (num2 != 0)
            {
                double result = num1 / num2;
                resultLabel.Text = $"Result: {result}";
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
```

## Пример 3: Приложение с ListBox и DataGridView

### Описание

Приложение, которое отображает список элементов в ListBox и позволяет добавлять их в DataGridView.

### Код

```csharp
public partial class MainForm : Form
{
    private ListBox listBox;
    private DataGridView dataGridView;
    private Button addButton;
    private TextBox inputTextBox;

    public MainForm()
    {
        InitializeComponent();
        InitializeCustomComponents();
    }

    private void InitializeCustomComponents()
    {
        listBox = new ListBox();
        listBox.Location = new Point(20, 20);
        listBox.Size = new Size(200, 150);
        Controls.Add(listBox);

        dataGridView = new DataGridView();
        dataGridView.Location = new Point(240, 20);
        dataGridView.Size = new Size(300, 150);
        dataGridView.Columns.Add("Item", "Item");
        Controls.Add(dataGridView);

        inputTextBox = new TextBox();
        inputTextBox.Location = new Point(20, 180);
        inputTextBox.Size = new Size(200, 30);
        Controls.Add(inputTextBox);

        addButton = new Button();
        addButton.Text = "Add to ListBox";
        addButton.Location = new Point(20, 220);
        addButton.Click += AddButton_Click;
        Controls.Add(addButton);

        Button addToGridButton = new Button();
        addToGridButton.Text = "Add to DataGridView";
        addToGridButton.Location = new Point(130, 220);
        addToGridButton.Click += AddToGridButton_Click;
        Controls.Add(addToGridButton);
    }

    private void AddButton_Click(object sender, EventArgs e)
    {
        string item = inputTextBox.Text;
        if (!string.IsNullOrWhiteSpace(item))
        {
            listBox.Items.Add(item);
            inputTextBox.Clear();
        }
    }

    private void AddToGridButton_Click(object sender, EventArgs e)
    {
        if (listBox.SelectedItem != null)
        {
            dataGridView.Rows.Add(listBox.SelectedItem.ToString());
        }
    }
}
```

## Заключение

В этом уроке мы рассмотрели основы создания приложений Windows Forms на языке C#. Мы узнали, как создавать и инициализировать формы, добавлять элементы управления, такие как кнопки, текстовые поля, метки, а также как создавать простое приложение-калькулятор и приложение с ListBox и DataGridView. Практикуйтесь с этими примерами, чтобы лучше понять, как создавать настольные приложения с графическим интерфейсом пользователя на C#.


## Навигатор

- [На главную](../index.md)
- [Предыдущий урок](../B03_L03_Interface/README.md)
- [Следующий урок](../B04_L02_WPF/README.md)