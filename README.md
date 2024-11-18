
# Лекция 1

`Console.WriteLine("Hello, World!");console - это класс`  
`Console.WriteLine("Вы ввели {0}", Console.ReadLine()); 0 - это номер параметра`  
`Console.WriteLine($"Вы ввели {Console.ReadLine()}");
`
* int
* short
* long
* byte
* char
* bool
* float
* double
* string
* void

# Лекция 2
**Классы**
 * Структура и класс - это типы данных, составные.
 * Переменные типа класса - это объекты класса (или экземпляры класса).

 * Базовые принципы ООП:  
   _Инкапсуляция  
   Наследование  
   Полиморфизм_
 
 * Инкапсуляция - это принцип ООП, при котором все данные и некоторые действия, используемые в классах, закрыты от внешнего доступа.

 *  Использование глобальных переменных не безопасно (одна из функций использует переменную, поменяет ее значение, вторая функция может с этим конфликтовать)
   
 * Элементы классов:
   _Переменные_(которые описываются внутри классов) - поля классов
   _Функции_ - методы
   _Свойство_ - элемент класса предназначенный для контролирования доступа к данным этого класса  
   
   
 Ключевые слова (для модитификаторов уровней доступа):
 * `private`(собственный) - обхявить переменную в классе и спользовать переменную только внутри этого класса
 * `protected` - 
 * `public` - в любом месте программного кода
   
 *` internal` - внутренний (только в этом проекте(?))


 # практика 1




**угадайка**
_задумано число от 1 до 100
ввести число в этом диапазоне
не угадать
меньше.больше - сообщение от компа
 7 попыток_



```{
int a = (new Random()).Next(1, 101); //Next - функция random для случайного числа, 100 не входит 1 входит, exclusive - включительный
int b;
int n = 0;
while (n < 7) {
    Console.Write("Введите число в диапазоне от 1 до 100: ");//просто не переводит курсор на новую строку
    var input = Console.ReadLine();
    if (int.TryParse(input, out b))
    {

        if (b > a)
        {
            Console.WriteLine("Нужно ввести число поменьше");
        }
        else if (a < b)
        {
            Console.WriteLine("Нужно ввести счило побольше");
        }
        else {
            Console.Write("Вы угадали ((");
            break;
        }
    }
    else
    {
        Console.WriteLine("Число вводи!");
    }
    n++;
}
if (n == 7)
{
    Console.WriteLine("лошок, не угадал");
}
}
```
## WORDLE
```
string[] words = {"вобла", "допка", "зачет", "билет", "книга", "жизнь"};
Random rand = new Random();объект из генератора случайных чисел
string randWord = words[rand.Next(0, words.Length)];

Console.WriteLine("Угадывай слово давай!!");
string guess = Console.ReadLine();
guess = guess.ToLower();
if (guess.Length != 5){
    Console.WriteLine("Неверная длина слова");
    guess = Console.ReadLine();
}

for(var i = 0; i < guess.Length; i++){большая - буква на сыоем мете, маленькая буква есть но она в другом месте если * - значит буквва не отгадана
    if (guess[i] == randWord[i])
        Console.WriteLine(guess[i].ToString().ToUpper());
    else if (randWord.Contains(guess[i])) Console.WriteLine(guess[i]);
    else Console.Write("*");
}
```

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Helloworldназвание проекта в котором класс
{
    public class Person
    {
        private string _lastname;при описании полей начинаем названия с _
        private string _firstname;рекомедуется применять _camelCase
        private int _age;
        private float _salary;

        public string Lasnameполучает значение из подя
        {
            get {  return _lastname; }
            set
                {
                if (value != null && value.Length > 0)
                    _lastname = value;

            }
        }

        /*public string Getlasname()получает значение из подя
        {
            return _lastname;
        }

        public string Setlasname()
        {
            if (value != null && value.Length > 0)
                _lastname = value;
        }
        */

        public string Firstname
        {
            get => _firstname;
            /*private*/ set => _firstname = (value != null && value.Length > 0) ? value :  "<Неизвестно>");

        }

        public int Age => _age;

        public float Salary
        {
            get => _salary;
            set => _salary = Math.Abs(value);
        }

        public bool Gender { get; set; } = true;автореализуемое свойство - 

    }
}
```


`var p1 = new Person();` - создаем объект класса персон
можем объявить метод в классе чтобы получить доступ к private.
в setter например можно проверить допустимость значения

```
p1.Setlasname("Иванов");
p1.lastname = "Иванов";для этого свойства
Console.WriteLine(p1.Getlasname());

init
```


# Практика 2

**complex.cs**
```
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Practice2
{
    public class Complex//ctrl+RR - refactoring
    {
        public double Re { get; set; }
        public double Im { get; set; }//если ссылочный тип - то NULL по умолчанию
        //если тип значение - то по дефолту значение равно 0
        public double AbsoluteValue => Math.Sqrt(Re * Re + Im * Im);
        public Complex Conjugate => new Complex(Re, -Im);
        public Complex(double re, double im) {
            Re = re;
            Im = im;
        }
        public Complex() { }
        public override string ToString() //переопределение метода, потому что у предка-класса обджект есть уже этот метод
        {
            var sb = new StringBuilder();
            if (Re != 0 || Im ==0) 
            {
                sb.Append(Re);
            }
            if (Im != 0)
            {
                if (Im > 0 && Re != 0)
                {
                    sb.Append("+");
                }
                else
                {
                    sb.Append("-");
                }
                if (Math.Abs(Im) != 1)
                {
                    sb.Append(Math.Abs(Im));
                }
                sb.Append('i');
            }
            return sb.ToString();

        }
    }
}

```

**Program.cs**
```

using Practice2;
using System.Security.Cryptography.X509Certificates;

var z1 = new Complex();
var z2 = new Complex()
{
    Re = 3,
    Im = 4

};
var z3 = new Complex(0, -1);

Console.WriteLine(z1);
Console.WriteLine(z1.AbsoluteValue);
Console.WriteLine(z1.Conjugate);
Console.WriteLine(z2);
Console.WriteLine(z2.AbsoluteValue);
Console.WriteLine(z2.Conjugate);
Console.WriteLine(z3);
Console.WriteLine(z3.AbsoluteValue);
Console.WriteLine(z3.Conjugate);


//конструктор класса - спциальный метод коорый вызывается при создании класса называется точно так же как сам класс
//любой класс содержит зотя бы один конструктор 
//конструктор без параметров - конструктор по умолчанию

```



### ДОМАШКА - ДЕДЛАЙН 28 НОЯБРЯ
 **разработать класс для работы с римскими числами**  
 * класс должен позволять производить вычисления с римскими числами (деление целочисленное)в виде операторов  
   диапазон поддерживаемых значений - до MMMCMXCIX (3999 включительно)  
 * правила записи римских значений -  классика  
 * цифры располагаютсся в порядке от больших к меньшим, цифры повторяются не более 3 раз подряд, меньшая записывается перед большей -
   вычитается из числа - только из тех, которая обозначается через единички
 *  одно число задать как римское и сложить его с обычным интом(без вещественных)
 *  результат - класс должен давать возможность узнать и римскую, и арбаскую запись  

