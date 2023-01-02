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

### 1.2.1. Target platforms: server-side, Android, anywhere Java runs

The primary goal of Kotlin is to provide a more concise, more productive, safer alternative to Java
that’s suitable in all contexts where Java is used today.

As you can see, Kotlin’s target is quite broad. It gives you an excellent level of integration with
libraries that support specific domains or programming paradigms.

### 1.2.2. Statically typed

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

### 1.2.3. Functional and object-oriented

### 1.2.4. Free and open source

## 1.3. Kotlin applications

### 1.3.1. Kotlin on the server side

### 1.3.2. Kotlin on Android

## 1.4. The philosophy of Kotlin

### 1.4.1. Pragmatic(실용성)

### 1.4.2. Concise(간결성)

### 1.4.3. Safe(안전성)

### 1.4.4. Interoperable(상호운용성)

## 1.5. Using the Kotlin tools

### 1.5.1. Compiling Kotlin code

### 1.5.2. Plug-in for IntelliJ IDEA and Android Studio

### 1.5.3. Interactive shell

### 1.5.4. Eclipse plug-in

### 1.5.5. Online playground

### 1.5.6. Java-to-Kotlin converter

## 1.6. Summary
