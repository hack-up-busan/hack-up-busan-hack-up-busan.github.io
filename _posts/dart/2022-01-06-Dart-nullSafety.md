---
layout: single
title: Flutter/Dart 핵심만 쏙 - null safety
categories:
  - Dart
tags:
  - [nullSafety]
toc: true
date: 2023-01-06
---

## Flutter 2.0 과 null safety
사실 Null Safety라는 개념은 2021년초에 flutter 2.0과 함께 등장한 개념이다. 그런 개념을 2023년 flutter 3.0이 나온 지금
시점에서 다루는 이유는 여전히 이 개념이 도입되지 않은 코드들이 인터넷에 많이 돌아다니기 때문이다. 
당장 필요한 개념을 찾기 위해 flutter 관련된 내용을 다루는 블로그를 많이 볼 수 있는데 2021년 이전에 작성된 
글들은 아직 null safety 개념이 도입되기 이전의 코드가 많기 때문이다. 


## null safety란?

프로그램을 개발하다 보면 런타임 프로그램 실행 중 null 참조 에러가 많이 발생한다.   null safety는 말 그대로 null 에게서 안전한 프로그램 코드를 작성하자는 말이다. 여기서 주의 해야 할 점은 null safety가 null을 쓰지 말자는 것이 아니라는 점이다.  (null도 엄연히 실존하는 자료형).  중요한 것은 null 자체가 아니라 예상치 못한 null 에 대응하지 못하는 함수이다. null safety는 이 문제를 코드가 실행되기 전 컴파일러가 해당 버그를 잡아줌으로써 예상치 못한 상황을 대비할 수 있게 해준다. 이러한 타입 체크는 즉각적으로 에러 여부를 알 수 있어 빠르게 에러에 대응할 수 있도록 해준다. 

## flutter null 관련 문법
null safey가 들어오면서 들어온 문법에 대해 알아보자
1. 변수명 뒤에 ?를 붙이면 해당 변수는 null 사용이 가능하다. 
```dart
String canBeNull? = null; 
```
2. 변수명 뒤에 !을 붙이면 null이 아님을 단언
```dart
String cantBeNull! = 'NotNull';
```
3. late 키워드를 붙이면 생성할 때 변수 초기화를 안 해도 됨
<iframe src="https://dartpad.dev/embed-dart.html?id=07998808a07eda8fec2269710036cf7f" style="width:120%; height:700px"></iframe>

일반적으로 클래스는 생성자등으로 변수를 초기화 해주지 않으면 컴파일 에러가 발생하지만 late를 붙이면 
실제로 그 변수를 사용하기 전에만 변수에 값이 할당되면 된다. 이 때 주의할 점은 null은 할당될 수 없다. 

## null safety 도입 이후 생성자 규칙의 변화
사실 이것이 내가 이 글을 쓰게된 이유라고 할 수 있다.

1. null이 가능한 변수

```dart
class ReusableCard extends StatelessWidget {  
  const ReusableCard({super.key, required this.colour, this.cardChild});  
  final Color colour;  
  final Widget cardChild;  	// Error
  @override  
  Widget build(BuildContext context) {  
    return Expanded(  
      child: Container(  
        margin: const EdgeInsets.all(15),  
		  decoration: BoxDecoration(  
          color: colour,  
		  borderRadius: BorderRadius.circular(10),  
	    ),  
	  ),  
    );  
  }  
}
```

이전에는 class의 field를 nullable로 지정하지 않으면 저절로 null로 지정되기 때문에 저 코드가 문제가 되지 않았지만
null safety가 들어온 이 후에는 저렇게 class를 만들면 runtime error가 발생한다. 그렇다면 required가 아닌 cardChild를
올바르게 작성하는 방법은 무엇일까? 
```dart
class ReusableCard extends StatelessWidget {
  const ReusableCard({super.key, required this.colour, this.cardChild});
  final Color colour;
  final Widget? cardChild;
  @override
  Widget build(BuildContext context) {
    return Expanded(
      child: Container(
        margin: const EdgeInsets.all(15),
        decoration: BoxDecoration(
          color: colour,
          borderRadius: BorderRadius.circular(10),
        ),
      ),
    );
  }
}
```
정답은 뒤에 ?를 붙여 nullable로 지정해주는 것이다. 

2. 생성될때 초기화되지 않는 변수처리

```dart
import 'dart:math';

class CalculatorBrain{
  CalculatorBrain({required this.height, required this.weight});
  final int height;
  final int weight;
  final double _bmi;	//	Error
  String calculateBMI(){
    double _bmi = weight / pow(height/100, 2);
    return _bmi.toStringAsFixed(1);
  }
  String getResult(){
    if(_bmi >= 25){
      return 'OverWeight';
    } else if(_bmi > 18){
      return'Normal';
    } else {
      return 'UnderWeight';
    }
  }
}
```

또한 이전에는 생성자에서 초기화되지 않은 변수를 내부 메소드에서 초기화 할 때 별다른 조치가 필요없었다.

```dart
import 'dart:math';

class CalculatorBrain{
  CalculatorBrain({required this.height, required this.weight});
  final int height;
  final int weight;
  late final double _bmi;
  String calculateBMI(){
    _bmi = weight / pow(height/100, 2);
    return _bmi.toStringAsFixed(1);
  }
  String getResult(){
    if(_bmi >= 25){
      return 'OverWeight';
    } else if(_bmi > 18){
      return'Normal';
    } else {
      return 'UnderWeight';
    }
  }
}
```

하지만 지금은 late를 사용하여 나중에 값이 할당될 변수임을 명시해야 한다.

### 작성자: YunSukHyun
