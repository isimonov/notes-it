Итератор шаблон проектирования, который обеспечивает интерфейс для итерирования коллекции, позволяя абстрагироваться от деталей её реализации. В Java `Iterator` это именно интерфейс.
# Интерфейс Iterator\<E>

- `boolean hasNext()`
- `E next()`
- `void remove()`
# Интерфейс Iterator\<E>

Его должны реализовывать все коллекции, которые поддерживают итератор. У него есть единственный метод `Iterator<T> iterator()`.