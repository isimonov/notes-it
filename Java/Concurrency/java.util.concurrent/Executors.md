`ExecutorService` исполняет асинхронный код в одном или нескольких потоках. Создание инстанса ExecutorService'а делается либо вручную через конкретные имплементации (`ScheduledThreadPoolExecutor` или `ThreadPoolExecutor`), но проще будет использовать фабрики класса `Executors`.

# ThreadPoolExecutor

```java
ExecutorService service1 = Executors.newFixedThreadPool(2);
ExecutorService service3 = Executors.newSingleThreadExecutor();
ExecutorService service2 = Executors.newCachedThreadPool();
ExecutorService service4 = Executors.newScheduledThreadPool(3);
```

## fixedThreadPool

*fixedThreadPool* - обычный фиксированный пул потоков.

## singleThreadExecutor

- Сервис выполняет за раз только одну задачу.
- Если мы отправляем N задач на исполнение, все N задач одна за другой будет выполняться одним потоком.
- Если поток будет прерван, то создастся новый поток для выполнения остальных задач.

## cachedThreadExecutor

*cachedThreadExecutor* - кэширует потоки, отсюда и название. Он держит активными (но не используемыми) потоки в течение ограниченного количества времени, для того чтобы использовать эти потоки для выполнения новых задач.

```java
public static ExecutorService newCachedThreadPool() {
	return new ThreadPoolExecutor(0, Integer.MAX_VALUE, 60L, TimeUnit.SECONDS, new SynchronousQueue<Runnable>());
}
```

# ScheduledThreadPoolExecutor

*ScheduledThreadPoolExecutor* - выполнение задач по расписанию.

```java
ExecutorService service = Executors.newScheduledThreadPool(3);
Runnable task = () -> { System.out.println(Thread.currentThread().getName()); };
// after 1 second every 2 seconds
service.scheduleAtFixedRate(task, 1, 2, TimeUnit.SECONDS);
```
