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

