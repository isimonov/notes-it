Набор коллекций для работы в многопоточной среде. Вместо базовых обёрток (`Collections.synchronizedCollection`, `Collections.synchronizedList`, `Collections.synchronizedMap`, `Collections.synchronizedSet` и др.) с блокированием доступа ко всей коллекции, используются блокировки по сегментам данных или используются wait-free алгоритмы для параллельного чтения данных.

# CopyOnWriteArrayList

 Потокобезопасный аналог `ArrayList`, реализованный на основе *CopyOnWrite* алгоритмов. Операции `add`, `set`, `remove` в данной коллекции приводят к созданию новой копии внутреннего массива. Это гарантирует то, что мы не словим `ConcurrentModificationException`. Лучше использовать в случаях с минимальным количеством write операций.

# CopyOnWriteArraySet

Реализация интерфейса Set, использующая за основу `CopyOnWriteArrayList`.

# ConcurrentMap

Улучшенные реализации `HashMap` и `TreeMap` с поддержкой многопоточности и масштабируемости. Итераторы не кидают `ConcurrentModificationException` и представляют данные на определенный отрезок времени.

## ConcurrentHashMap

Данные представлены в виде сегментов, которые разбиты по hash'ам ключей. По итогу, если вам нужен доступ, то блокируется сегмент, а не объект.

## ConcurrentNavigableMap

Расширяет интерфейс _NavigableMap_ и возвращает _ConcurrentNavigableMap_.

## ConcurrentSkipListMap

Является аналогом `TreeMap` для многопоточности. Данные сортируются по ключу и гарантируется усредненная производительность log(N) для `containsKey`, `get`, `put`, `remove` и других похожих операций.

## ConcurrentSkipListSet

Имплементация интерфейса `Set` на основе `ConcurrentSkipListMap`.