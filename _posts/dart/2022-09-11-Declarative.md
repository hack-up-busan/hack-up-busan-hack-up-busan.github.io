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

dart 언어의 큰 강점인 선언형 프로그래밍 방식을 배우고 싶으신 분들을 위해 쉽게 설명해 보았습니다.<br/>
주로 명령형으로 코드를 쓰셔서 처음 이 개념을 접하시는 분들도 차이를 이해하면 좋겠습니다.<br/>
그럼 내용으로 들어가봅시다!<br/>

## 선언형 프로그래밍 정의와 예시

♦ 명령형 프로그래밍(imperative programming)은 언어 해석이 순차적이며 <br/>어떠한 방법으로 문제를 해결할지에 초점
  
♦ 선언형 프로그래밍(declarative programming)은 순서나 문제 해결 과정을 다루기보다 <br/>**무엇을** 나타내야 할지에 초점

이렇게 말하면 이해가 잘 안가니 예를 들어 설명해보면, 샌드위치를 만들 때(재료는 있다고 가정)<br/>

♦ 명령형: 빵을 맨 밑에 두고 그 위에 머스타드를 발라. 그 위에 양상추를 올리고 그 위에 토마토를 올려. 그 다음 패티를 올리고 빵을 맨 위에 덮어.<br/>

♦ 선언형: 샌드위치 만들어.

물론 선언적 방식의 접근을 위해서는 명령형 방식으로 '어떻게 접근하는가'가 먼저 추상화가 되어있어야 한다.<br/>

샌드위치를 만들라고 시키는 것은 어떤 것을 둔다는 개념, 소스를 바른다는 개념 등을 알고 있다고 전제하는 것이다.<br/>

즉, 선언적 접근 방식의 기저에는 명령형이 깔려있고 **추상화** 된 것이다.<br/>

## 선언형 vs 명령형 프로그래밍 dart코드 비교
```dart
----------------------------(명령형)
//${'a' * length} 는 문자 'a'를 length 횟수만큼 반복하라는 뜻

String scream(int length) => "A${'a' * length}h!";

main() {

  final values = [1, 2, 3];
  
  for (var length in values) 
  { 
    print (scream(length));
  }
}
```

아래는 for문을 values.map(scream).forEach(print); 로 수정한 함수형 코드이다. (결과값 동일)

```dart
----------------------------(함수형)

String scream(int length) => "A${'a' * length}h!";

main() {

  final values = [1, 2, 3];
  
  values.map(scream).forEach(print); 
  // scream 함수를 인수로 넘김
}
```

함수형 프로그래밍에서 할 수 있는 것:

●  다른 함수에 함수를 인수로 넘기기

●  함수에 변수로 할당하기

●  여러 인수를 취하는 함수를 각각 단일 인수를 취하는 일련의 함수로 분해(커링이라고도 함).

Dart는 위의 기능을 모두 제공한다. Dart에서는 함수들은 곧 객체이며 Function타입을 가지고 있다. 

즉, 함수들은 변수로 할당되거나 다른 함수에 인수로 넘겨질 수있다. 


