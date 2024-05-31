# Базы данных

- Типы объектов в БД: схемы, таблицы, индексы, последовательности, представления, пакеты/функции
	- Таблицы
		- нормализация и денормализация
		- партиционирование (секционирование?) и шардирование (разделение по разным экземплярам БД)
	- [[DB indexes]]
		- типы: Hash, B-tree, GIN (полнотекстовый поиск), GiST и SP-GiST (упорядочивание специальных типов данных)
		- кластерный индекс (определяет физическое хранение), некластерный (обычный), cоставной (из нескольких столбцов)
	- Представления: обычные и материализованные
	- Пакеты/функции: курсоры
- Блокировки: оптимистичные и пессимистичные
- SQL
	- LEFT/RIGHT OUTER JOIN & INNER JOIN
	- SELECT COUT(1) FROM users u GROUP BY u.surname HAVING COUT(1) > 1
	- [[CTE]] (Common Table Expressions)
- [[Транзакции]]
	- Уровни изоляции
	- Вложенные транзакции
	- Транзакции в Spring: `@Transactional`, `transactionTemplate = new TransactionTemplate(transactionManager)`

# Java
- Принципы ООП: полиморфизм, наследование, инкапсуляция и абстракция
	- Задача на полиморфизм
- Stream API: `map`, `peek`, `flatMap`
- Функциональный интерфейс: `Predicate`, `Consumer`, `Supplier`, `Function`, `BiFunction`, `UnaryOperator`
- Блоки инициализации
- Абстрактный класс и интерфейс, в чём отличия
- Иммутабельный класс: `Integer`, `Byte`, `Character`, `Short`, `Boolean`, `Long`, `Double`, `Float`, `BigInteger` и `BigDecimal`, `Collections.unmodifiableList`
- Как работает `ArrayList`, `HashMap`, `TreeMap`
- Дженерики, [[Вариантность]]
- [[Effectively Final лямбды]] переменные и лямбды
- [[Equals hashCode]] (hashCode равны, если equals, но если равны hashCode не обязательно equals)
- Шаблоны проектирования GoF
- Многопоточность
	- `volatile` и `synchronized`
	- `java.util.concurrent`: Atomics, Concurrent Collections, Executors, Locks, Queues, Synchronizers

# Spring Boot

- Что происходит после старта SprinngBoot приложения, как происходит под капотом обработка входящего HTTP-запроса

# Брокеры сообщений
- Kafka, RabbitMQ, чем различаются
