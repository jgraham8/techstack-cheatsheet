## 1. Creating Streams

```java
List<String> names = List.of("Alice", "Bob", "Charlie");
names.stream()
     .filter(name -> name.startsWith("A"))
     .forEach(System.out::println);
```

## 2. Collecting Results

```java
List<String> filtered = names.stream()
                             .filter(name -> name.length() > 3)
                             .collect(Collectors.toList());
```

## 3. Parallel Streams

```java
List<Integer> numbers = IntStream.range(1, 1000).boxed().toList();
numbers.parallelStream()
       .map(n -> n * 2)
       .forEach(System.out::println);
```

