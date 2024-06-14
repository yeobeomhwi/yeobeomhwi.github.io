---
title: "Kotlin에서 입력 받기: Scanner vs readLine"
date: "2024-06-13"
thumbnail: "/assets/img/thumbnail/Kotlin.png"
---

# Kotlin에서 입력 받기: Scanner vs readLine

## Scanner 클래스와 readLine() 함수 비교

### Scanner 주요 메소드

| 메소드 | 설명 | 비트 크기 |
|------|---|--------|
| next() : String! | String 타입으로 리턴 | -         |
| nextByte() : Byte | Byte 타입으로 리턴 | 8비트     |
| nextShort() : Short | Short 타입으로 리턴 | 16비트    |
| nextInt() : Int  | Int 타입으로 리턴| 32비트    |
| nextLong() : Long | Long 타입으로 리턴 | 64비트    |
| nextFloat() : Float | Float 타입으로 리턴 | 32비트    |
| nextDouble() : Double | Double 타입으로 리턴 | 64비트    |
| nextLine() : String! | '\n'을 포함하는 한 라인을 읽고 '\n'을 버린 나머지 문자열을 String 타입으로 리턴 | -         |

---

## 한가지의 입력을 받는 코드

```kotlin
import java.util.Scanner

fun main(args: Array<String>){
    val sc:Scanner = Scanner(System.`in`)
}
```


## Kotlin에서 여러개의 입력 받는 두 가지 방법

### 1. Scanner 클래스를 이용한 입력 처리

```kotlin
import java.util.Scanner

fun main(args: Array<String>) {
    val sc = Scanner(System.`in`)
    print("입력 : ")
    val value1 = sc.nextInt()
    val value2 = sc.nextInt()
    val value3 = sc.nextInt()
    val value4 = sc.nextInt()
    
    val sum = value1 + value2 + value3 + value4
    println("출력 : $sum")
}

```

### 2. readLine() 함수를 이용한 입력처리

```kotlin
fun main() {
    print("입력 : ")
    val input = readLine() ?: ""
    
    if (input.isBlank()) {
        println("올바른 입력이 아닙니다.")
        return
    }
    
    val numbers = input.split(" ").map { it.toInt() }
    val sum = numbers.sum()
    
    println("출력 : $sum")
}
```
