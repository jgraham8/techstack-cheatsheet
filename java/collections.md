## Table of Contents
- [Table of Contents](#table-of-contents)
- [Overview of Common Collections](#overview-of-common-collections)
- [1. List Operations](#1-list-operations)
- [2. Map](#2-map)
- [3. Set](#3-set)
- [4. Queue](#4-queue)
- [5. PriorityQueue (Heap)](#5-priorityqueue-heap)
- [6. Stack](#6-stack)

---

## Overview of Common Collections

- **List**: Ordered collection that allows duplicates.
- **Set**: Unordered collection that does not allow duplicates.
- **Map**: Collection of key-value pairs.
- **Queue**: Collection used for holding elements prior to processing (FIFO).
- **Stack**: Last-in, first-out data structure.
- **PriorityQueue (Heap)**: A special kind of queue where elements are ordered by priority.

---

## 1. List Operations

```java
List<String> list = new ArrayList<>();
list.add("Java");
list.add("Spring");
list.forEach(System.out::println);
```
- ArrayList: When you need fast random access and are okay with slower insertions/removals.
- LinkedList: When you need fast insertions/removals but can tolerate slower access.

---

## 2. Map

```java
Map<String, Integer> map = new HashMap<>();
map.put("Java", 17);
map.put("Spring", 5);
map.forEach((key, value) -> System.out.println(key + " -> " + value));
```
- HashMap: Best for quick lookups.
- TreeMap: Use when you need keys to be in sorted order.
- LinkedHashMap: Maintains insertion order.

---

## 3. Set

```java
Set<String> set = new HashSet<>(List.of("Java", "Spring", "Docker"));
set.add("Kubernetes");
System.out.println(set);
```
- HashSet: Best for fast access with no duplicates.
- TreeSet: Use when you need a sorted set.
- LinkedHashSet: Maintains insertion order.

---

## 4. Queue

```java
Queue<String> queue = new LinkedList<>();
queue.add("First");
queue.add("Second");
System.out.println(queue.poll()); // Removes and returns the head
```
- LinkedList: Implements Queue for general use.
- PriorityQueue: Use when you need elements ordered by priority.

---

## 5. PriorityQueue (Heap)

```java
PriorityQueue<Integer> pq = new PriorityQueue<>();
pq.add(3);
pq.add(1);
pq.add(2);
System.out.println(pq.poll()); // Removes and returns the smallest element
```
- PriorityQueue: When you need an element with the highest or lowest priority.

---

## 6. Stack

```java
Stack<Integer> stack = new Stack<>();
stack.push(10);
stack.push(20);
System.out.println(stack.pop()); // Removes and returns the top element
```
- Stack: When you need LIFO operations.

