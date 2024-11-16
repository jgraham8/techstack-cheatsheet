## 1. Using CompletableFuture

```java
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> "Hello, Future!")
                                                    .thenApply(String::toUpperCase);
future.thenAccept(System.out::println);
```

## 2. ExecutorService

```java
ExecutorService executor = Executors.newFixedThreadPool(3);
executor.submit(() -> {
    System.out.println("Running in a separate thread");
});
executor.shutdown();
```

