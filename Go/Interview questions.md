# Горутины

- Горутины, отличие от потоков, сама программа Go - горутина
- Что такое каналы как устроены, буферизированный и небуферезированный
- Отличие слайсов и массивов
- Мютексы, вейтгруппы, once, и синхронизация
- Указатель и как передаются значения
- Что такое контекст и для чего нужен

# ООП в Go

- Наследование нет, можно заменить композицией
- Инкапсуляция - нет модификаторов, но есть написание с маленькой для приватных и с большой для публичных свойств
- Полиморфизм через интерфейс
- Можно ли присвоить переменной одного интерфейса тип другого? Да из за утиной типизации.
- Как определить тип: Через свитч и через рефлексию геттип

# Память

- На стеке можно разместить массив объемом 10 MB.
- Слайсы до 64 KB могут быть размещены на стеке. 
- в Go массивы передаются по значению, т.е. передавая массив в какую-либо функцию она получает копию массива (для передачи его указателя нужно явно это указывать, т.е. foo(&a)).
- Как работает GC
- Слайсы передаются "по ссылке" (фактически будет передана копия структуры slice со своими len и cap, но указатель на массив array будет тот-же самый). Для защиты слайса от изменений следует передавать его копию:

# Map
- хеш-функция
- бакет - в Go данные внутри бакета хранятся в массиве


# Дженерики

- Обобщение дженерики появились 1.18
- Можно ли определить тип дженерика в рантайме?

# Разное

Что такое cap - capacity у слайса, можем ли мы его задать и каким образом. Чем отличается от len - length.
Как работает append в слайсе?

Мапы всегда передаются по ссылке 

В Go не бывает ссылок, невозможно создать 2 переменные с 1 адресом, как в С++ например; но зато можно создать 2 переменные, указывающие на один адрес — но это уже указатели). Если же быть точнее, то мапа в Go — это просто указатель на структуру hmap




