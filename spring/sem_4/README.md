1. Механизм позднего связывания
  - Что такое? Слово virtual вам о чём-нибудь говорит?  
!()[1.jpg]  
_“virtual перед объявлением метода говорит, что решение о том, какую версию
метода выбрать, должно быть принято во время исполнения программы (позднее
связывание), а не на этапе компиляции (раннее связывание).”_

  - А зачем ?

Реальный тип объект может быть неизвестен на момент компиляции
  - Виртуальный деструктор
  - override & final
  - Чисто виртуальные функции и абстрактный класс

2. **dynamic_cast**
  - (Какой крутой гитхаб с техаными билетами по с++ (мб не мфти))[https://github.com/egorSheremetov02/cpp-exam-summer-2021/tree/master]
  - (С лекции момент)[https://disk.yandex.ru/d/GEZBar7nI7n8DA/2-04]
  - (Все виды кастов)[https://habr.com/ru/articles/266747/]

3. *Для тех кто думает что всё знает и хочет чего-то весёлого:

Создаём свою игру мморпг:

1. Надо реализовать генератор случайных чисел, из него сделать функцию “игральный кубик” - дискретное равномерное распределение 1-6

2. (Сегодня) Наследование

2 рода структур - 1-е класс персонажа, 2-е вещь

Поля у структур персонажей:
1.Здоровье
2.Атака
3.Ловкость 
(Защита)      // всё инты 
4.Массив вещей (размер 10 сразу завели)


У каждого персонажа 2 метода - атаковать и уклониться. 
Атаковать == просуммировать свою атаку по всем вещам + базовую, тоже самое с ловкостью (и защитой)
Уклониться == только ловкость просуммировать  
(хорошо бы при создании персонажа выводить - я родился, и при смерти - я проиграл)

Поля у стуктур вещей  
1.Прибавка к здоровью
2.Прибавка к атаке
3.Прибавка к ловкости
4.*метод - проверка на  живучесть == шанс сломаться == для каждой вещи свой метод, со своей вероятностью сломаться 
(надо понимать когда вещь сломалась)



Цель на сегодня - реализовать базовый класс персонаж и несколько типов персонажей, танк, берсерк, лучник… реализовать базовый класс и несколько типов вещей, хилка, ботинки, меч… 


3, 4 итд - если понравится - продолжим


Идея получения персонажа и вещей - 
рандом класс (через кубик) и ему 3-4 рандом вещи (нужна map связи вещи по номеру и класса тоже)


Идея боёвки - персонаж 1 атакует персонажа 2
у 1 атака А1, ловкость B1, у 2 - аналогично A2 B2 
проверяет если А2 > А1, то всё, не получилась атака
если же А1 > А2, то проверяем ловкость у 2 на уклонение
если В2 > В1, то он уклонился и всё, не получилась атака
если В1 > В2, но В1 - В2 = Х < 6, то бросаем кубик, если выпало число > Х, то 2 уклонился, иначе - нет

Если атака прошла, то от здоровья 2 отнимается разность А1 и А2.

Играется боёвка по очереди, пока не кончится хп у одного из персонажей. После каждого раунда боёвки бросаются кубики на поломку вещей (в метод вещи).*