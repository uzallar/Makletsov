using System.Text.Json.Nodes;

##лекция 1

Console.WriteLine("Hello, World!");//console - это класс
Console.WriteLine("Вы ввели {0}", Console.ReadLine());// 0 - это номер параметра
Console.WriteLine($"Вы ввели {Console.ReadLine()}");




///** 
// * int
// * short
// * long
// * byte
// * char
// * bool
// * float
// * double
// * string
// * void
// */

// Лекция 2
// Классы

/**
 * Структура и класс - это типы данных, составные.
 * Переменные типа класса - это объекты класса (или экземпляры класса).
 *
 * Базовые принципы ООП:
 *   - Инкапсуляция
 *   - Наследование
 *   - Полиморфизм
 *
 * Инкапсуляция - это принцип ООП, при котором все данные и некоторые действия,
 * используемые в классах, закрыты от внешнего доступа.
 */
 * 
 * использование глобальных переменных не безопасно (одна из функций использует переменную,
 * поменяет ее значение, вторая функция может с этим конфликтовать)
 * 
 * 
 * Элементы классов:
 * Переменные(которые описываются внутри классов) - поля классов
 * Функции - методы
 * Свойство - элемент класса предназначенный для контролирования доступа к данным этого класса
 * 
 * 
 * Ключеывые слова (для модитификаторов уровней доступа)
 * private(собственный) - обхявить переменную в классе и спользовать переменную только внутри этого класса
 * protected - 
 * public - в любом месте программного кода
 * 
 * internal - внутренний (только в этом проекте(?))

 */



 //практика 1




////угадайка
///**задумано число от 1 до 100
// * ввести число в этом диапазоне
// * не угадать
// * меньше.больше от компа
// * 7 попыток
// */


//int a = (new Random()).Next(1, 101);//Next - функция random для случайного числа, 100 не входит 1 входит, exclusive - включительный
//int b;
//int n = 0;
//while (n < 7) {
//    Console.Write("Введите число в диапазоне от 1 до 100: ");//просто не переводит ккурсор на новую строку
//    var input = Console.ReadLine();
//    if (int.TryParse(input, out b))
//    {

//        if (b > a)
//        {
//            Console.WriteLine("Нужно ввести число поменьше");
//        }
//        else if (a < b)
//        {
//            Console.WriteLine("Нужно ввести счило побольше");
//        }
//        else {
//            Console.Write("Вы угадали ((");
//            break;
//        }
//    }
//    else
//    {
//        Console.WriteLine("Число вводи!");
//    }
//    n++;
//}
//if (n == 7)
//{
//    Console.WriteLine("лошок, не угадал");
//}


//WORDLE
//string[] words = {"вобла", "допка", "зачет", "билет", "книга", "жизнь"};
//Random rand = new Random();//объект из генератора случайных чисел
//string randWord = words[rand.Next(0, words.Length)];

//Console.WriteLine("Угадывай слово давай!!");
//string guess = Console.ReadLine();
//guess = guess.ToLower();
//if (guess.Length != 5){
//    Console.WriteLine("Неверная длина слова");
//    guess = Console.ReadLine();
//}

//for(var i = 0; i < guess.Length; i++){//большая - буква на сыоем мете, маленькая буква есть но она в другом месте если * - значит буквва не отгадана
//    if (guess[i] == randWord[i])
//        Console.WriteLine(guess[i].ToString().ToUpper());
//    else if (randWord.Contains(guess[i])) Console.WriteLine(guess[i]);
//    else Console.Write("*");
//}



using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Helloworld//название проекта в котором класс
{
    public class Person
    {
        private string _lastname;//при описании полей начинаем названия с _
        private string _firstname;//рекомедуется применять _camelCase
        private int _age;
        private float _salary;

        public string Lasname//получает значение из подя
        {
            get {  return _lastname; }
            set
                {
                if (value != null && value.Length > 0)
                    _lastname = value;

            }
        }

        /*public string Getlasname()//получает значение из подя
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

        public bool Gender { get; set; } = true;//автореализуемое свойство - 

    }
}



using Helloworld;

var p1 = new Person();//создаем объект класса персон
//можем объявить метод в классе чтобы получить доступ к private.
//в setter например можно проверить допустимость значения

//p1.Setlasname("Иванов");
//p1.lastname = "Иванов";//для этого свойства
Console.WriteLine(p1.Getlasname());


init


