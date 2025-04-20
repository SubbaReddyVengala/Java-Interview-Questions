# Java-Interview-Questions

## **What is the difference between Stack and Heap Memory Area in Java**

In Java, Stack and Heap are two important memory areas used for different purposes during the execution of a program. Here's a clear and concise comparison between the two:

### ✅ Stack Memory vs Heap Memory in Java

![image](https://github.com/user-attachments/assets/a64d4699-e0f1-4e74-b748-5fc6d40b6cc3)

## Dependency Injection in spring 

### ✅ What is Dependency Injection in Spring?

Dependency Injection (DI) is a design pattern used in Spring to loose couple the classes by injecting dependent objects at runtime rather than creating them manually inside the class.

### 🔧 Why use Dependency Injection?

Promotes loose coupling.

Improves testability and maintainability.

Makes the code more flexible and scalable

### 💡 Types of Dependency Injection in Spring:

![image](https://github.com/user-attachments/assets/ba6a3042-aa7a-4b35-9fa9-c6dd7e835881)

### 🧪 Common Annotations Used in Spring DI:

![image](https://github.com/user-attachments/assets/1eebd124-b814-4092-8e6b-ac226ac626f7)


### ✅ **1. What is the difference between constructor and setter injection?**

**Answer:**

> In Spring, **constructor injection** injects dependencies through a class constructor, whereas **setter injection** uses public setter methods to inject dependencies after the object is constructed.
> 
> Constructor injection is preferred when the dependency is **mandatory**, while setter injection is suitable for **optional** dependencies.

----------

### ✅ **2. Which injection type is preferred and why?**

**Answer:**

> **Constructor injection** is generally preferred in Spring because:
> 
> -   It ensures that the object is always created with all its required dependencies.
>     
> -   It supports **immutability** and promotes **testability**.
>     
> -   It makes the code more **robust** by avoiding the risk of partially initialized beans.
>     

----------

### ✅ **3. Can you inject a bean into another bean?**

**Answer:**

> Yes, Spring allows injecting one bean into another using **Dependency Injection**. This is commonly done using annotations like `@Autowired`, `@Inject`, or via constructor/setter injection.
> 
> For example, if `StudentService` needs `StudentRepository`, Spring will automatically inject it if both are marked as Spring beans.

----------

### ✅ **4. What happens if multiple beans of the same type exist?**

**Answer:**

> If multiple beans of the same type exist in the Spring context, Spring will throw a **NoUniqueBeanDefinitionException** during injection.
> 
> To resolve this, we can:
> 
> -   Use `@Qualifier("beanName")` to specify which bean to inject.
>     
> -   Use `@Primary` to mark one bean as the default.
>     

----------

### ✅ **5. How does Spring know which dependency to inject?**

**Answer:**

> Spring uses **type-based autowiring** by default. It scans the application context and injects the dependency based on the **type**.
> 
> If multiple beans of the same type are available, Spring uses:
> 
> -   `@Qualifier` for explicit bean selection.
>     
> -   `@Primary` for default bean selection.
>     
> 
> Also, Spring supports **constructor-based autowiring** where parameter names and types help it resolve the correct dependency.


### ✅ **1. What are HTTP status codes?**

**Answer:**

> HTTP status codes are **3-digit codes** returned by the server in response to a client's request. They indicate whether the request was successful, failed, or needs further action. These codes are grouped into different categories based on their first digit.

----------

### ✅ **2. Can you name and explain the different categories of HTTP status codes?**

**Answer:**

Category

Range

Meaning

1xx

100–199

Informational – Request received, continuing process.

2xx

200–299

Success – Request was successful.

3xx

300–399

Redirection – Further action needed.

4xx

400–499

Client Error – Request had issues.

5xx

500–599

Server Error – Server failed to fulfill request.

----------

### ✅ **3. What are the most commonly used HTTP status codes in REST APIs?**

**Answer:**

-   `200 OK`: Request was successful.
    
-   `201 Created`: Resource was successfully created.
    
-   `204 No Content`: Request was successful, no data returned.
    
-   `400 Bad Request`: Client sent an invalid request.
    
-   `401 Unauthorized`: Authentication is required or failed.
    
-   `403 Forbidden`: Client does not have access rights.
    
-   `404 Not Found`: Requested resource does not exist.
    
-   `409 Conflict`: Conflict occurred (e.g., duplicate data).
    
-   `500 Internal Server Error`: Server encountered an error.
    
-   `503 Service Unavailable`: Server is down or overloaded.
    

----------

### ✅ **4. What’s the difference between 401 and 403 status codes?**

**Answer:**

> `401 Unauthorized` means the user is not authenticated (missing or invalid credentials).  
> `403 Forbidden` means the user is authenticated but **not authorized** to access the resource.

----------

### ✅ **5. When should you return 204 No Content?**

**Answer:**

> `204 No Content` should be returned when a request is successful, but there's **no need to return any data**. For example, after a successful DELETE operation.

----------

### ✅ **6. What status code should be returned for validation errors?**

**Answer:**

> Usually, **`400 Bad Request`** is used for validation errors.  
> If you want to provide more details, you can return a **custom error body** with field-specific messages

# Transaction 

## ✅ **1. What is a transaction in Spring?**

**Answer:**

> A **transaction** in Spring is a **sequence of operations** performed as a single unit of work. It ensures that either **all operations succeed** or **none are applied**, maintaining **data integrity** and **consistency**.

----------

## ✅ **2. What are the key properties of a transaction (ACID)?**

Property

Description

**A - Atomicity**

All operations in a transaction are completed; if one fails, all are rolled back.

**C - Consistency**

The database remains in a consistent state before and after the transaction.

**I - Isolation**

Transactions are isolated from each other; intermediate states are not visible.

**D - Durability**

Once a transaction is committed, the changes are permanent.

----------

## ✅ **3. How does Spring manage transactions?**

**Answer:**

> Spring provides **declarative transaction management** using the `@Transactional` annotation.
> 
> It uses **AOP (Aspect-Oriented Programming)** to create proxies around methods and handles commit or rollback based on exceptions.

----------

## ✅ **4. What is `@Transactional` and how is it used?**

**Answer:**

> `@Transactional` is a Spring annotation used to mark methods or classes where **transactional behavior** is required.  
> When applied, Spring starts a transaction before the method runs and **commits** it if it completes successfully, or **rolls back** if an exception is thrown.

java

CopyEdit

`@Service  public  class  PaymentService { @Transactional  public  void  transferMoney(...) { // DB operations }
}` 

----------

## ✅ **5. What are propagation and isolation in Spring transactions?**

**Answer:**

> -   **Propagation** defines how transactions behave when called from another transactional method. Common types:
>     
>     -   `REQUIRED` (default): Join existing or create new transaction.
>         
>     -   `REQUIRES_NEW`: Always creates a new transaction.
>         
>     -   `NESTED`: Executes within a nested transaction.
>         

> -   **Isolation** defines how data accessed by one transaction is **isolated** from others. Common levels:
>     
>     -   `READ_COMMITTED`, `READ_UNCOMMITTED`, `REPEATABLE_READ`, `SERIALIZABLE`.
>         

----------

## ✅ **6. When does Spring roll back a transaction by default?**

**Answer:**

> By default, Spring only rolls back a transaction when an **unchecked exception** (`RuntimeException` or `Error`) is thrown.
> 
> To roll back on **checked exceptions**, you need to configure `@Transactional` like:


`@Transactional(rollbackFor = SomeCheckedException.class)` 

----------

## ✅ **7. Can we use `@Transactional` on private methods?**

**Answer:**

> No, `@Transactional` does **not work on private methods** because Spring uses **proxies**, and private methods cannot be intercepted

# Microservices

## ✅ **1. What are Microservices?**

**Answer:**

> Microservices is an architectural style where an application is **broken into small, independent services**, each responsible for a specific business function.  
> These services **communicate via APIs (usually REST or messaging systems like Kafka)** and are **independently deployable and scalable**.

----------

## ✅ **2. What are the main benefits of Microservices?**

**Answer:**

-   **Scalability** – Scale individual components independently.
    
-   **Flexibility in Tech Stack** – Each service can use a different language/tech.
    
-   **Independent Deployment** – Less risk while deploying changes.
    
-   **Resilience** – One service failure doesn't crash the entire app.
    
-   **Faster Development** – Small teams can work in parallel on different services.
    

----------

## ✅ **3. What are some challenges in Microservices?**

**Answer:**

-   **Distributed system complexity**
    
-   **Data consistency**
    
-   **Service discovery and communication**
    
-   **Centralized logging and monitoring**
    
-   **Security across services**
    

----------

## ✅ **4. How do Microservices communicate with each other?**

**Answer:**

> Services can communicate using:

-   **Synchronous** protocols like **REST (HTTP)** or **gRPC**.
    
-   **Asynchronous** protocols using **messaging queues** (e.g., **Kafka**, **RabbitMQ**).
    

----------

## ✅ **5. What is Service Discovery?**

**Answer:**

> In microservices, services are dynamic (scale up/down), so **Service Discovery** allows services to register themselves and discover each other.  
> Tools: **Eureka (Netflix OSS)**, **Consul**, **Zookeeper**.

----------

## ✅ **6. How do you handle API Gateway in Microservices?**

**Answer:**

> API Gateway is a single entry point for clients to interact with multiple services.  
> It handles:

-   Request routing
    
-   Authentication & authorization
    
-   Rate limiting
    
-   Logging and monitoring
    

📌 Example: **Spring Cloud Gateway**, **Kong**, **Zuul**

----------

## ✅ **7. How do you manage configuration in Microservices?**

**Answer:**

> Use a **centralized configuration server**, like **Spring Cloud Config**, to manage configs across services.  
> This avoids hardcoding values and enables dynamic updates.

----------

## ✅ **8. How do you ensure fault tolerance in Microservices?**

**Answer:**

> Tools and techniques:

-   **Circuit Breaker** (e.g., Resilience4j, Hystrix)
    
-   **Retry and Timeout**
    
-   **Fallback methods**
    
-   **Bulkheads and Rate Limiting**
    

----------

## ✅ **9. How is data handled in Microservices?**

**Answer:**

> Each microservice has its **own database** (Database per service pattern) to ensure loose coupling and data ownership.  
> Data consistency is handled via **eventual consistency**, not transactions.

----------

## ✅ **10. How do you monitor Microservices?**

**Answer:**

> Use Observability tools like:

-   **Micrometer** for metrics
    
-   **Prometheus + Grafana** for monitoring
    
-   **ELK Stack / Splunk** for logs

- **Zipkin / Jaeger** for distributed tracing
  
# ✅ Java 8


### 🔹 **1. What are the main features introduced in Java 8?**

**Answer:**

-   **Lambda Expressions**
    
-   **Functional Interfaces**
    
-   **Stream API**
    
-   **Default and Static Methods in Interfaces**
    
-   **Optional Class**
    
-   **Date and Time API (java.time)**
    
-   **Collectors and enhanced Map operations**
    
-   **Method References and Constructor References**
    
-   **Parallel Streams**
    
-   **Nashorn JavaScript Engine (removed in Java 15)**
    

----------

### 🔹 **2. What is a Lambda Expression?**

**Answer:**

> A Lambda expression is an anonymous function that allows passing behavior as data.  
> It’s mainly used to implement functional interfaces in a concise way.
```
`(int a, int b) -> a + b` 
```
----------

### 🔹 **3. What is a Functional Interface?**

**Answer:**

> An interface with exactly **one abstract method** is called a functional interface.

Examples:

-   `Runnable`
    
-   `Callable`
    
-   `Comparator`
    
-   `Function<T, R>`
    
-   `Predicate<T>`
    
```
`@FunctionalInterface  public  interface  MyInterface { void  test();
}
```
----------

### 🔹 **4. What is the Stream API?**

**Answer:**

> Stream API is used to **process collections in a functional and declarative way**, using operations like `filter`, `map`, `reduce`, `collect`, etc.
```
`List<String> names = list.stream()
                         .filter(s -> s.startsWith("A"))
                         .collect(Collectors.toList());` 
```
----------

### 🔹 **5. Difference between map() and flatMap()?**

**Answer:**

Feature

`map()`

`flatMap()`

Output

Stream of elements

Flattened Stream

Use case

Transform each element

Flatten nested structure
```

`list.stream().map(String::toUpperCase)
list.stream().flatMap(List::stream)` 
```
----------

### 🔹 **6. What are Intermediate and Terminal operations in Streams?**

**Answer:**

-   **Intermediate**: Returns another stream → `map()`, `filter()`, `sorted()`
    
-   **Terminal**: Produces result → `collect()`, `count()`, `forEach()`
    

----------

### 🔹 **7. What are Collectors? Give examples.**

**Answer:** `Collectors` is a utility class used with streams for reducing data.

Examples:

-   `toList()`
    
-   `toSet()`
    
-   `groupingBy()`
    
-   `partitioningBy()`
    
-   `joining()`
    
-   `summarizingInt()`
    
-   `counting()`
    
```

list.stream().collect(Collectors.groupingBy(String::length))` 
```
----------

### 🔹 **8. What is Optional in Java 8?**

**Answer:** `Optional<T>` is a container object which may or may not contain a non-null value.  
It helps **avoid null checks and NullPointerExceptions**.




`Optional<String> name = Optional.of("Subba");
name.ifPresent(System.out::println);` 

----------

### 🔹 **9. Difference between orElse(), orElseGet(), and orElseThrow()?**

**Answer:**

-   `orElse(value)` → always evaluates the value
    
-   `orElseGet(Supplier)` → evaluates only when Optional is empty
    
-   `orElseThrow()` → throws exception if value is missing
    

----------

### 🔹 **10. What are Default and Static Methods in Interfaces?**

**Answer:**

> Java 8 allows us to add methods with **implementation** in interfaces using `default` or `static`.


`default  void  log() {
    System.out.println("logging...");
} static  void  print() {
    System.out.println("printing...");
}` 

----------

### 🔹 **11. Can two interfaces have the same default method?**

**Answer:**

> Yes, but if a class implements both, it must override the method to resolve the conflict.

----------

### 🔹 **12. What are Method References?**

**Answer:**

> A shorter syntax for calling existing methods using `::`.


`list.forEach(System.out::println); // Static list.stream().map(String::toUpperCase); // Instance method` 

----------

### 🔹 **13. What is the new Date and Time API in Java 8?**

**Answer:**

> Java 8 introduced `java.time` package to replace `java.util.Date`.

Classes:

-   `LocalDate`
    
-   `LocalTime`
    
-   `LocalDateTime`
    
-   `ZonedDateTime`
    
-   `Period`, `Duration`
    


`LocalDate  now  = LocalDate.now();` 

----------

### 🔹 **14. What is the use of `Predicate`, `Function`, `Consumer`, and `Supplier`?**

**Answer:**

Interface

Method

Purpose

Predicate<T>

test()

Takes T, returns boolean

Function<T,R>

apply()

Takes T, returns R

Consumer<T>

accept()

Takes T, returns nothing

Supplier<T>

get()

Takes nothing, returns T

----------

### 🔹 **15. How do you sort a list using Streams and Lambda?**

**Answer:**

`list.stream()
    .sorted((s1, s2) -> s1.compareTo(s2))
    .collect(Collectors.toList());` 

Or use method reference:

`list.stream().sorted(Comparator.naturalOrder())`

## ✅ **What is Garbage Collection in Java?**

**Answer:**

> **Garbage Collection (GC)** in Java is the **automatic process of identifying and reclaiming memory** used by objects that are **no longer reachable or needed**, to **free up heap memory**.

Java uses **automatic garbage collection**, so developers don't need to manually deallocate memory (unlike C/C++).

### 🔹 Interview Tip:

> "Garbage Collection is key to Java's memory management. It boosts performance, avoids memory leaks, and allows developers to focus on writing logic instead of worrying about memory cleanup."


## ✅ What is **Dynamic Binding** in Java?

> **Dynamic Binding** (also called **Late Binding**) means that the **method call is resolved at runtime** rather than compile time.


### 🔹 When does it happen?

-   Occurs with **method overriding** (not overloading).
    
-   Applies to **instance methods**, not static, private, or final methods.

```
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Test {
    public static void main(String[] args) {
        Animal a = new Dog();  // Upcasting
        a.sound();  // Dynamic Binding
    }
}
```
🔸 Output:
```
Dog barks
```
🔍 Although the reference type is Animal, the actual object is a Dog, so the Dog's sound() method is executed at runtime.

![image](https://github.com/user-attachments/assets/367df1d2-da1f-40b0-b1b7-a24350596410)

## ✅ **Java String Interview Questions & Answers**

----------

### 1. **What is a String in Java?**

> A `String` is an immutable sequence of characters. It is a class in `java.lang` package and represents text

```
String str = "Hello";

```


### 2. **Why are Strings immutable in Java?**

> Once a `String` is created, it cannot be changed. This helps:

-   String pooling
    
-   Thread-safety
    
-   Caching hash code
    
-   Security (e.g., in class loading, file paths)
    

----------

### 3. **What is the difference between `==` and `.equals()` for Strings?**

Operator

Checks for

`==`

Reference (memory address) equality

`.equals()`

Content/value equality

```
String a = "hello";
String b = new String("hello");
System.out.println(a == b);       // false
System.out.println(a.equals(b));  // true

```

### 4. **What is String Pool in Java?**

> A special memory area in heap where Java stores **String literals** to save memory.
```
String a = "Java";
String b = "Java";
System.out.println(a == b); // true → both refer to same object in pool
```
### 5. **How to create a mutable String in Java?**

> Use `StringBuilder` or `StringBuffer`.

-   `StringBuilder` → faster, not thread-safe.
    
-   `StringBuffer` → slower, thread-safe.
  
6. **Difference between `StringBuilder` and `StringBuffer`?**

![image](https://github.com/user-attachments/assets/a370b480-54c8-48e6-8c7d-f5e0db719e30)


### 7. **Why should we use `StringBuilder` over `String` for string concatenation in loops?**

> `String` is immutable, so every concat creates a new object.  
> `StringBuilder` is mutable, hence more efficient.
----------

### 8. **How does `substring()` work internally in Java 8+?**

> Creates a **new String** with a copy of the characters from the original. In Java 6–7, it used to share the same char array (causing memory leaks if not handled).

----------

### 9. **Is `String` thread-safe?**

> ✅ Yes, because it's **immutable**. But operations like concatenation are **not atomic**.

----------

### 10. **Can we use `String` in switch statements?**

> ✅ Yes, since Java 7.
```
String command = "start";
switch (command) {
  case "start": System.out.println("Started"); break;
}
```
----------
11. **Common String methods (and what they do)?**

![image](https://github.com/user-attachments/assets/59e1cb40-d597-4b59-96d4-62f6b78b4927)


### 12. **How to convert:**

-   `String` → `int`: `Integer.parseInt(str)`
    
-   `int` → `String`: `String.valueOf(num)`
    
-   `String` → `char[]`: `str.toCharArray()`
    
-   `char[]` → `String`: `new String(charArray)`
--------
### 13. **How is memory managed for Strings in Java?**

-   **String literals** go into **String Pool**.
    
-   `new String("Java")` creates a new object in the heap, **not pooled** unless interned.
    
-   Use `str.intern()` to move string to pool.
--------
### 14. **What is `intern()` method in String?**

> `intern()` returns the canonical representation from the String pool.
```
String s1 = new String("Java").intern();
String s2 = "Java";
System.out.println(s1 == s2); // true
```

15. **Write a program to count number of occurrences of a character in a String.**
```
String input = "java";
char target = 'a';
long count = input.chars().filter(ch -> ch == target).count();
System.out.println(count);  // Output: 2

```
--------

## ✅ **Multithreading in Java – Interview Questions & Answers**

----------

### 1. **What is multithreading in Java?**

> Multithreading is a process of executing **multiple threads simultaneously** to maximize CPU utilization and improve performance in concurrent programs.

----------

### 2. **What is the difference between a process and a thread?**
![image](https://github.com/user-attachments/assets/eafe128e-4849-4703-bddd-46025698db88)

----------

### 3. **How to create a thread in Java?**

✅ **Two ways:**
```
// 1. Extend Thread
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running...");
    }
}

// 2. Implement Runnable
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable running...");
    }
}

```
Then:
```
new MyThread().start();
new Thread(new MyRunnable()).start();

```
----------
### 4. **What is the lifecycle of a thread?**

-   New
    
-   Runnable
    
-   Running
    
-   Blocked/Waiting
    
-   Terminated
----------
5. **What is the difference between `start()` and `run()` method?**

![image](https://github.com/user-attachments/assets/c21dd21b-fc03-4f22-9ecb-5ff381bfba5a)

## Example to Clarify:
```
class MyThread extends Thread {
    public void run() {
        System.out.println("Running in a new thread");
    }
}

public class ThreadExample {
    public static void main(String[] args) {
        MyThread thread = new MyThread();

        thread.run();   // Runs in the main thread, no new thread is created
        thread.start(); // Creates a new thread and calls run() in that thread
    }
}
```
Output:
```
Running in a new thread    // (when start() is used)
Running in a new thread    // (when run() is directly called in the main thread)

```
----------
### 6. **What is thread synchronization?**

> Synchronization is used to **control access to shared resources** by multiple threads to prevent data inconsistency or race conditions.
```
synchronized void print() {
    // Only one thread can access this at a time
}
```
### 🔐 **Why is synchronization needed?**

When two or more threads try to modify the same resource simultaneously, it can lead to:

-   Corrupted data
    
-   Unexpected behavior
    
-   Bugs that are hard to reproduce
  
## 💡 Real-Life Analogy:

Think of a toilet in a public place (shared resource). Only one person (thread) can use it at a time, and others must wait until it's free — that’s synchronization!

----------
### 7. **What is a deadlock?**

> Deadlock is a situation where two or more threads are **waiting for each other to release resources**, and none of them can proceed.
--------

8. **What is the difference between `synchronized method` and `synchronized block`?**
   
![image](https://github.com/user-attachments/assets/ce3b98e4-f785-4444-9fad-8f6064b311fb)

--------



--------

### ✅ **What is the `volatile` keyword in Java?**

**Answer:**  
The `volatile` keyword in Java is used to **mark a variable as being stored in main memory**. When a variable is declared `volatile`, every **read** of that variable will be done **from main memory**, and every **write** will be immediately **written to main memory**. This ensures **visibility** of changes across threads.

### 🔄 **Why is it needed?**

In a multithreaded environment, threads may **cache variables locally**. Without `volatile`, one thread's updates **may not be visible** to others, leading to stale or inconsistent data.

```
class MyThread extends Thread {
    volatile boolean running = true;

    public void run() {
        while (running) {
            // do something
        }
    }

    public void stopRunning() {
        running = false; // change is immediately visible to other threads
    }
}
```
--------
### 10. **What is the use of `join()` method?**

> `join()` causes the current thread to **wait until another thread finishes execution**.
--------
### 11. **What is the use of `sleep()` method?**

> Pauses the current thread for a specified time.
```
Thread.sleep(1000); // 1 second

```
--------

### ✅ join() vs sleep() vs isAlive() in Java

![image](https://github.com/user-attachments/assets/78e7ff24-cf17-4666-b325-db4ec0c50871)


🔹 `join()` – Wait for another thread to finish
```
Thread t = new Thread(() -> {
    System.out.println("Thread running...");
});
t.start();
t.join();  // Main thread waits for t to finish
```
**Use case:** When thread A should wait for thread B to complete before proceeding.
🔹 `sleep()` – Pause current thread
```
Thread.sleep(1000); // Pauses for 1 second
```
**Use case:** To simulate delay or wait before next action.

🔹 `isAlive()` – Check thread status
```
Thread t = new Thread(() -> System.out.println("Run"));
t.start();
System.out.println(t.isAlive());  // true or false depending on state
```
**Use case:** Check if a thread is still running before taking action.
## 🧠 **Quick Summary Flashcards**

**📌 `join()`**  
➡️ Waits for a thread to finish execution.

**📌 `sleep()`**  
➡️ Pauses current thread for a fixed time.

**📌 `isAlive()`**  
➡️ Returns true if thread has started and not yet finished.

## 💡 Real-World Analogy

-   🛑 `sleep()` → You take a nap — no one else is affected.
    
-   ⏳ `join()` → You wait for your friend to finish eating before leaving together.
    
-   🔍 `isAlive()` → You check if your friend is still at the table.

----------

## ✅ **12. What are Thread Priorities in Java?**

**Answer:**  
In Java, each thread has a **priority** ranging from **1 (MIN_PRIORITY)** to **10 (MAX_PRIORITY)**, with the **default being 5 (NORM_PRIORITY)**. The thread scheduler can use these priorities to decide the **order of thread execution** — threads with **higher priority may get more CPU time** than lower-priority ones. However, **priority-based scheduling is not guaranteed** as it is **JVM and OS dependent**.

💡 Analogy:

Imagine you’re in a queue, and someone has a VIP pass (priority 10) — they may get in earlier, but only if the bouncer (scheduler) decides to honor the pass.


### 13. **What are Daemon threads?**

> Threads that run in the background and die when all user threads finish.  
> Example: Garbage Collector thread.
> Daemon threads are **background threads** that provide **supportive services** to user threads. They run continuously **in the background** and are **terminated automatically** by the JVM **once all user (non-daemon) threads finish execution**.
```
thread.setDaemon(true);
```
### 🧠 **Key Points:**

-   Daemon threads are **low-priority background workers**.
    
-   JVM **does not wait** for daemon threads to finish.
    
-   They are typically used for **housekeeping tasks**.
    
-   A thread can be marked as daemon **only before starting** it using `setDaemon(true)`.
```
public class DaemonExample {
    public static void main(String[] args) {
        Thread t = new Thread(() -> {
            while (true) {
                System.out.println("Daemon thread running...");
                try { Thread.sleep(500); } catch (InterruptedException e) {}
            }
        });
        t.setDaemon(true); // Must be set before start()
        t.start();

        System.out.println("Main thread finished.");
    }
}

```
**Output:**  
"Daemon thread running..." (may or may not print depending on how fast main finishes)

### 💡 Real-World Analogy:

Think of a **janitor (daemon thread)** in an office who cleans up when everyone leaves. Once the main staff (user threads) go home, **he also stops working** — **even if cleanup isn’t done.**

-------


## ✅ **How does the `synchronized` keyword work internally in Java?**

**Answer:**  
The `synchronized` keyword in Java works by using **intrinsic locks (also known as monitors)** to control access to code blocks or methods. When a thread enters a `synchronized` block or method, it **acquires the monitor lock** associated with the object or class. Other threads are **blocked** until the lock is released.

### 💡 Real-world Analogy:

Imagine a **toilet stall with a lock** (monitor). When one person (thread) enters and locks it, no one else can use it until it's unlocked (lock released).

-----------------
