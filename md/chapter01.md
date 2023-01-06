# Chapter 01. Kotlin: what and why

## This chapter covers

- A basic demonstration of Kotlin
- The main traits of the Kotlin language
- Possibilities for Android and server-side development
- What distinguishes Kotlin from other languages
- Writing and running code in Kotlin

## 1.1. A taste of Kotlin

- [code](../src/main/kotlin/chapter01/01.kt)

## 1.2. Kotlin’s primary traits

### 1.2.1 Target platforms: server-side, Android, anywhere Java runs, and more

The primary goal of Kotlin is to provide a more concise, more productive, safer alternative to Java
that’s suitable in all contexts where Java is used today.

As you can see, Kotlin’s target is quite broad. It gives you an excellent level of integration with
libraries that support specific domains or programming paradigms.

### 1.2.2 Static typing makes Kotlin performant, reliable, and maintainable

- statically typed vs dynamically typed

| statically typed               | dynamically typed                                                |
|--------------------------------|------------------------------------------------------------------|
| type is known at compile time  | type is known at runtime -> leads runtime errors                 |
| longer code and strict syntax  | shorter code and greater flexibility in creating data structures |

- **type inference**
    ```kotlin
    // Kotlin automatically determines that its type is Int
    val x = 1
    ``` 
    - Performance
        - Calling methods is faster because there’s no need to figure out at runtime which method
          needs to be called.
    - Reliability
        - The compiler verifies the correctness of the program, so there are fewer chances for
          crashes at runtime.
    - Maintainability
        - Working with unfamiliar code is easier because you can see what kind of objects the code
          is working with.
    - Tool support
        - Static typing enables reliable refactorings, precise code completion, and other IDE
          features.
- OOP
    - Class
    - Interface
    - Generics
- **nullable types**
    - more reliable
- **function types**
    - functional programming

### 1.2.3 Combining functional and object-oriented makes Kotlin safe and flexible

**The key concepts of functional programming(함수형 프로그래밍)**

- First-class functions(일급 시민인 함수)
    - You work with functions (pieces of behavior) as values. You can store them in variables, pass
      them as parameters, or return them from other functions.
- Immutability(불변성)
    - You work with immutable objects, which guarantees that their state can’t change after their
      creation.
- No side effects(부작용 없음)
    - You use pure functions that return the same result given the same inputs and don’t modify the
      state of other objects or interact with the outside world.

**Benefits of functional programming(함수형 프로그래밍)**

1. conciseness(간결성)
    1. abstraction(추상화)
        1. lambda expressions
   ```kotlin
    fun findAlice() = findPerson { it.name == "Alice" }
    fun findPersonAged29() = findPerson { it.age == 29 }
    ```
2. safe concurrency(안전한 동시성)
    1. by immutable data structures + pure functions
3. easier testing(쉬운 테스트)
    1. no side effects
    2. can be tested in isolation without requiring a lot of environment setup

Kotlin has a rich set of features to support functional programming from the get-go.

- Function types
    - allowing functions to receive other functions as parameters or return other functions
- Lambda expressions
    - letting you pass around blocks of code with minimum boilerplate
- Data classes
    - providing a concise syntax for creating classes that can hold immutable data
- A rich set of APIs in the standard library
    - for working with objects and collections in the functional style

### 1.2.4 Concurrent and asynchronous code becomes natural and structured with coroutines

Needs of concurrent and asynchronous programming

- User interfaces need to remain responsive while long-running computations are running in the
  background.
- applications often need to make more than one request at a time
- server-side applications are expected to keep serving incoming requests, even when a single
  request is taking much longer than usual.
- applications need to operate concurrently, working on more than one thing at a time.

**Coroutines**

With Coroutines, Kotlin approaches the problem of concurrent and asynchronous programming using
suspendable computations, where code can suspend its execution, and resume its work at a later
point.

`authenticate`, `upload`, and `postProcess` executions are suspended where needed, leaving the
application free to do other tasks in the meantime.

```kotlin
fun uploadFile(f: File) {
    launch {
        val token = authenticate()
        val uploadedFile = upload(token, item)
        postProcess(uploadedFile)
    }
}

suspend fun authenticate(): Token { /* . . . */
}
// . . .
```

Kotlin coroutines

- very lightweight abstraction
- powerful tool for building concurrent applications.
    - structured concurrency
    - cold and hot flows
    - channels

### 1.2.5 Kotlin can be used for any purpose: it’s free and open source

## 1.3 Areas in which Kotlin is often used

### 1.3.1 Powering backends: server-side development with Kotlin

**Server-side programming**

- based on JVM
    - Web applications that return HTML pages to a browser
    - Backends for mobile or single-page applications that expose a JSON API over HTTP
    - Microservices that communicate with other microservices over an RPC protocol or message bus

There’s almost always an existing system that is being extended, improved, or replaced, and new code
has to integrate with existing parts of the system, which may have been written many years ago.

**Profits**

- Interoperability(상호 운용성) with existing Java code
    - Java -> Kotlin
        - Kotlin will fit right in.
    - more compact, more reliable, and easier to maintain
- Reliability(안정성)
    - Type system, with its precise tracking of `null` values
        - `NullPointerException` fails to compile in Kotlin
        - ensure that you fix the error before the application gets to the production environment
- Frameworks(프레임워크)
    - Spring
        - first-class support
        - additional extensions

Listing 1.2. Writing Spring Boot applications in Kotlin

```kotlin
@SpringBootApplication
class DemoApplication

fun main(args: Array<String>) {
    runApplication<DemoApplication>(*args)
}

@RestController
class GreetingResource {
    @GetMapping
    fun index(): List<Greeting> = listOf(
        Message("1", "Hello!"),
        Message("2", "Bonjour!"),
        Message("3", "Guten Tag!"),
    )
}

data class Greeting(val id: String?, val text: String)
```

- Ever-growing ecosystem
    - DSL(Domain-Specific Language)
        - Ktor

      Listing 1.3. A Ktor app uses a DSL to route HTTP requests

      ```kotlin
      fun main() {
          embeddedServer(Netty, port = 8000) {
              routing {
                  get("/world") {
                      call.respondText("Hello, world!")
                  }
                  route("/greet") {
                      get { /* . . . */ }
                      post("/{entityId}") { /* . . . */ }
                  }
              }
          }.start(wait = true)
      }    
      ```

    - ORM(Object-Relational Mapping)
        - objects <-> database representation
    - http4k
        - provide simple and uniform abstractions for requests and responses

### 1.3.2 Mobile Development: Android is Kotlin-first

### 1.3.3 Multiplatform: Sharing business logic and minimizing duplicate work on iOS, JVM, JS and beyond

## 1.4 The philosophy of Kotlin

### 1.4.1 Kotlin is a pragmatic language designed to solve real-world problems

### 1.4.2 Kotlin is concise, making the intent of your code clear while reducing boilerplate

### 1.4.3 Kotlin is safe, protecting you from whole categories of errors

### 1.4.4 Kotlin is interoperable, allowing reuse of existing Java code to the highest degree

## 1.5 Using the Kotlin tools

### 1.5.1 Compiling Kotlin code

### 1.5.2 Plug-in for IntelliJ IDEA and Android Studio

### 1.5.3 Quickly try out Kotlin code with the interactive shell

### 1.5.4 Try Kotlin without installation with the Kotlin online playground

### 1.5.5 Move code automatically with the Java-to-Kotlin converter

## 1.6 Summary
