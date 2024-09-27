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
	- Триггеры
- Блокировки: оптимистичные и пессимистичные
- SQL
	- LEFT/RIGHT OUTER JOIN & INNER JOIN
	- `SELECT u.surname, GROUP_CONCAT(u.id), COUT(1) FROM users u GROUP BY u.surname HAVING COUT(1) > 1`
	- [[CTE]] (Common Table Expressions)
- [[Транзакции]]
	- Уровни изоляции
	- Вложенные транзакции
	- Транзакции в Spring: `@Transactional`, `transactionTemplate = new TransactionTemplate(transactionManager)`
- Пул соединений к БД

# HTTP
- Методы: 
	- GET
	- POST - создание (единственный неидемпотентный)
	- PUT - обновление, 
	- PATCH, 
	- DELETE, 
	- OPTIONS - получения параметров для ресурса или для сервера в целом, не затрагивает ресурс 
	- HEAD - проверка существования ресурса, пустое тело ответа, затрагивает ресурс
- REST vs SOAP: OpenAPI (Swagger), WSDL (XSD)
- Nginx
- TLS - transport layer security
- что происходит когда вводишь HTTP запрос 

# Java
- String vs StringBulder vs StringBuffer
- Принципы ООП: полиморфизм, наследование, инкапсуляция и абстракция
	- Задача на полиморфизм
- Stream API: `map`, `peek`, `flatMap`
- Функциональный интерфейс: `Predicate`, `Consumer`, `Supplier`, `Function`, `BiFunction`, `UnaryOperator`
- Блоки инициализации
- Абстрактный класс и [[Интерфейс]], в чём отличия
- [[Immutable]] класс: `Integer`, `Byte`, `Character`, `Short`, `Boolean`, `Long`, `Double`, `Float`, `BigInteger` и `BigDecimal`, `Collections.unmodifiableList`
- Как работает `ArrayList`, `HashMap`, `TreeMap`
- Дженерики, [[Вариантность]]
- [[Effectively Final лямбды]] переменные и лямбды
- [[Equals hashCode]] (hashCode равны, если equals, но если равны hashCode не обязательно equals)
- Шаблоны проектирования GoF
	- **Порождающие**: Абстрактная фабрика (Abstract Factory), Строитель (Builder), Фабричный метод (Factory Method), Прототип (Prototype), Одиночка (Singleton)
	- **Структурные**: Адаптер (Adapter), Мост (Bridge), Компоновщик (Composite), Декоратор (Decorator), Фасад (Facade), Приспособленец (Flyweight), Заместитель (Proxy)
	- **Поведенческие**: Цепочка обязанностей (Chain of responsibility), Команда (Command), Интерпретатор (Interpreter), Итератор (Iterator), Посредник (Mediator), Хранитель (Memento), Наблюдатель (Observer), Состояние (State), Стратегия (Strategy), Шаблонный метод (Template method), Посетитель (Visitor)
- Многопоточность
	- что такое монитор объекта
	- `java.util.concurrent`: Atomics, Concurrent Collections, Executors, Locks, Queues, Synchronizers
	- `volatile` и `synchronized`
	- wait notify notifyall
- Исключения unchecked `RuntimeException` и `Error`, остальные checked
# Spring Boot

- Starters:
	- spring-boot-starter-parent
	- spring-boot-starter
	- spring-boot-starter-aop
	- spring-boot-starter-data-jpa
	- spring-boot-starter-security
	- spring-boot-starter-test
	- spring-boot-starter-web - Spring vs Spring Boot, что такое сервлет, контейнер сервлетов, сервер приложений
	- spring-boot-starter-actuator - prometeus
- Логирование в спринг SLF4J, Logback, трассировка логов, MDC.
- Свой стартер: @EnableAutoConfiguration(exclude = DataSourceAutoConfiguration.class)
- Register a Custom Auto-Configuration _META-INF/spring.factories_ org.springframework.boot.autoconfigure.EnableAutoConfiguration=com.baeldung.autoconfigure.CustomAutoConfiguration
- Тестирование: интеграционные и модульные тесты. Компоненты spring-boot-starter-test: JUnit, Mockito и отдельно библиотеку утверждений: AssertJ, Hamcrest, JsonPath
- Как поменять порт по умолчанию в Spring Boot?
- Какие встроенные сервера поддерживает Spring Boot,и как изменить используемый по умолчанию? Spring MVC поддерживает Tomcat, Jetty, and Undertow. 
- Профили: возможность поделить конфигурацию на части
- Что происходит после старта SprinngBoot приложения, как происходит под капотом обработка входящего HTTP-запроса
- Как устроен механизм проксирования бинов в Spring. Spring AOP использует _JDK dynamic proxies_ (если есть интерфейс) или _CGLIB_ (если интерфейса нет).
- BOM
- Области видимости бинов: singleton, prototype, request, session, global-session

# Docker & k8s

Чем отличается контейнер от образа
Команды
- docker images
- docker ps
- docker ps -a
Кубер
- ingress controller
- deployment
- node
- pod - обёртка над контейнером(ами)

# Брокеры сообщений
- Kafka, RabbitMQ, чем различаются
