---
title: "엘리스 Flutter 트랙 Day-5"
date: "2024-08-23"
categories: [Flutter, 엘리스부트캠프]
tags:
  - Flutter
  - 엘리스부트캠프
---
> 22일은 개인사정으로 출석하지 못함 {: .prompt-warning}

## **클래스 상속**

객체 지향 프로그래밍의 중요한 개념 중 하나로, 기존 클래스를 기반으로 새로운 클래스를 만드는 방법입니다. 

이를 통해 코드의 **재사용성**을 높이고, 기존 코드의 기능을 **`확장`**하거나 **`변경`**할 수 있습니다.

- `상속` : 다른 클래스에 있는 데이터 및 함수들을 나의 클래스로 가지고 오는 기능
- `슈퍼 클래스`(부모 클래스) : 상속의 대상이 되는 클래스 
- `서브 클래스`(자식 클래스):상속을 받는 클래스

Dart에서 상속은 extends키워드 사용

```dart
class Animal{
  void eat(){
    print('Animal is eating');
  }
}

class Dog extends Animal{
  void bark(){
    print('Dog is barking');
  }
}

void main(){
  Dog dog = Dog();
  dog.eat(); //Animal is eating
  dog.bark(); //Dog is barking
}
```

### 매서드 재정의(Method Overriding)
서브 클래스에서 슈퍼 클래스의 `메서드를 재정의`하여 자신만은 구현을 제공할 수 있다.
이때 `@override`어노테이션을 사용하여 메서드를 재정의하는 것을 명시한다.

```dart
class Animal{
  void eat(){
    print('Animal is eating');
  }
}

class Dog extends Animal{
  @override
  void eat(){
    print('Dog is eating');
  }
  void bark(){
    print('Dog is barking');
  }
}

void main(){
  Dog dog = Dog();
  dog.eat(); //Dog is eating'
  dog.bark(); //Dog is barking
}
```
### **상속의 제한**

- **단일 상속**
  - Dart에서는 **단일 상속**만 지원합니다.
  - 한 클래스는 하나의 클래스만 상속받을 수 있습니다.
  
- **다형성**
  - 상속을 통해 **다형성**을 구현할 수 있습니다.
  - 동일한 메서드 호출이 객체의 타입에 따라 다르게 동작하게 하는 것을 의미합니다.

### **`super` 키워드**

- **`super`** 키워드를 사용하여 슈퍼 클래스의 생성자나 메서드를 호출할 수 있습니다.

```dart
class Animal{
  void eat(){
    print('Animal is eating');
  }
}

class Dog extends Animal{
  @override
  void eat(){
    super.eat();
    print('Dog is eating');
  }
  void bark(){
    print('Dog is barking');
  }
}

void main(){
  Dog dog = Dog();
  dog.eat(); //Animal is eating \n Dog is eating'
  dog.bark(); //Dog is barking
}
```

### **추상 클래스 (`abstract class`)**
- **인스턴스화할 수 없는 클래스**입니다.
- **하나 이상의 추상 메서드**(구현이 없는 메서드)를 가질 수 있습니다.
- **`abstract`** 키워드를 사용하여 정의합니다.
- 추상 메서드는 **구현 없이 선언만** 합니다.

```dart
abstract class Animal{
  void eat(); // 추상 메서드
  
  void breathe(){
    print('Animal is breathing');
  }
}

class Dog extends Animal{
  @override
  void eat(){
    print('Dog is eating');
  }
}

void main(){
  Dog dog = Dog();
  dog.eat();
  dog.breath();
}
```

### 생성자 초기화 리스트(initializer list)

- 생성자 본체(`body`)가 실행되기 전에 인스턴스 변수를 초기화하는 데 사용됩니다.
- **콜론 (`:`)** 뒤에 오는 부분으로, 생성자가 호출될 때 변수의 초기값을 설정하는 데 유용합니다.
- 생성자 초기화 리스트는 특히 `final` 변수나 상수 생성자를 초기화할 때 많이 사용됩니다.

```dart
cclass Point{
  final int x;
  final int y;

  Point(int x, int y) : x = x, y = y;
}

void main(){
  Ponit p = Pont(3,4);
  print('x: ${p.x}. y: ${p.y}');
}
```