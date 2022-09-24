---
layout: single
title: "Flutter/Dart 핵심만 쏙 - Declarative programming"
categories:
  - Dart
tags:
  - [Flutter]
toc: true
date: 2022-09-11
---

## 선언형 프로그래밍 정의와 예시

♦ 명령형 프로그래밍(imperative programming)은 언어 해석이 순차적이며 어떠한 방법으로 문제를 해결할지에 초점<br/>
  
♦ 선언형 프로그래밍(declarative programming)은 순서나 문제 해결 과정을 다루기보다
  
  **무엇을** 나타내야 할지에 초점<br/>

이렇게 말하면 이해가 잘 안가니 예를 들어 설명해보면, 

샌드위치를 만들 때(재료는 있다고 가정)<br/>

♦ 명령형: 빵을 맨 밑에 두고 그 위에 머스타드를 발라. 그 위에 양상추를 올리고 그 위에 토마토를 올려. 그 다음 패티를 올리고 빵을 맨 위에 덮어.<br/>

♦ 선언형: 샌드위치 만들어.

물론 선언적 방식의 접근을 위해서는 명령형 방식으로 '어떻게 접근하는가'가 먼저 추상화가 되어있어야 한다.<br/>

샌드위치를 만들라고 시키는 것은 어떤 것을 둔다는 개념, 소스를 바른다는 개념 등을 알고 있다고 전제하는 것이다.<br/>

즉, 선언적 접근 방식의 기저에는 명령형이 깔려있고 **추상화** 된 것이다.

## 선언형 vs 명령형 프로그래밍 dart코드 비교
```dart
**----------------------------(명령형)
String scream(int length) => "A${'a' * length}h!";

main() {

  final values = [1, 2, 3, 5, 10];
  
  for (var length in values) 
  { 
    print (scream(length));
  }
}**
```


```dart
**----------------------------(함수형)

String scream(int length) => "A${'a' * length}h!";

main() {

  final values = [1, 2, 3, 5, 10];
  
  values.map(scream).forEach(print);  
}**
```
