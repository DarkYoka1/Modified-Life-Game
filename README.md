# Life_game
Это модифицированная игра жизнь, в которой учитываются расширенные соседи, еда и возраст.

Отрисовка происходит на движке pygame.

За основу этого проекта была взята обычная игра жизнь, в которой учитываются только 8 клеток вокруг. Теперь в начальный момент клетки не заполняются единицами,
а заполняются объектами класса "Node", в которой есть сама жизнь, количество еды и возраст клетки (если она там есть).

А это модифицированная игра жизнь, в которой учитываются:
1. 28 клеток вокруг одной клетки:
При этом, если в данной клетке есть сосед, то добавляется не просто единичка, а увеличивается на определенный коэффициент,
который, можно сказать, является качеством соседа.
Я ввел 4 кэффициента для подсчета соседей:
к11 - это коэффициент, который увеличивается во время подсчета сохранения жизни клетки во внутреннем квадрате, т.е. увеличивается переменная "count_save";
к12 - это коэффициент, который увеличивается во время подсчета сохранения жизни клетки во внешнем квадрате, т.е. увеличивается переменная "count_save";
к21 - это коэффициент, который увеличивается во время подсчета зарождения жизни клетки во внутреннем квадрате, т.е. увеличивается переменная "count_born";
к22 - это коэффициент, который увеличивается во время подсчета зарождения жизни клетки во внешнем квадрате, т.е. увеличивается переменная "count_born";
Если min_save <= count_save <= max_save, то клетка остается жива.
Если min_born <= count_born <= max_born, то клетка зарождается.

2. Была добавлена еда (food):
В начальный момент времени параметр "food" объекта "Node" заполняется едой от nn единиц до nn единиц рандомным образом.
Каждая клетка съедает "how_to_eat" количество еды за такт времени, а если там нет жизни, то каждый момент времени еда в данной клетке увеличивается на "increasing_food".
Если клетка умирвает, то также увеличивается еда на "increasing_food".

3. Был добавлен возраст (age):
В начальный момент времени всем клеткам присваивается возраст 1.
Каждый такт времени возраст увеличивается на 1.
Если клетка достигает определенного возраста "max_live", то она погибает (параметр "age" = 0)

Основной целью было подобрать коэффициенты, при которых жизнь будет стабильной (не вымирает, не разростается очень быстро).
После подбора начальных условий автоматическим способом происходит тест игры на разных условиях в цикле, тест "Жизни" по 50 эпох 100 раз на 100 разных коэффициентах,
которые меняются автоматически в цикле. В итоге получаем матрицу процентов заполнения поля клетками (процент живых клеток по отношению ко всему полю).







