---
layout: single
categories:
  - 플러터
title: Code의 질 높이기
date: 2022-11-18
toc: true
comments : true
---

## FEEDBACK : Code의 질 높이기

- 저번 멘토링 때 예슬이와 석현이가 짠 코드들의 로직을 보고 내 코드의 질이 낮다는 걸 느낌.
- 뿐만 아니라 대표님이 올려주신 영상 속 음성을 들었는데, 팀마다 코드를 짜는 스타일이 있다고 하셨다.
- **종합한 바, 다음 멘토링까지 코드의 질을 높이기 위한 스터디를 해보자고 결심했음 !**

- 그래서 내가 선택한 방법은 **토스 앱 기능 구현을 잠시 멈추고 그동안 스터디 했던 개념들 총정리 및 코드의 질을 높이는 방법을 배우는데 시간 투자.**
    
![화면 캡처 2022-11-19 233914](https://user-images.githubusercontent.com/110464205/202862295-c60aab56-1b69-4cb1-a91f-af1d150c0fe2.png)
    
### 모듈화 Modularizing

- 먼저 반복되는 부분 (동일하거나 동일한 기능 등)은 반복되지 않도록 함.
    - 반복되는 위젯이라고 생각되는 부분을 Extract Widget 기능으로 추출해서 따로 사용

### 추상화 Abstraction

- 식당에 웨이터, 셰프, 서빙, 캐셔 등을 고용해서 식당을 운영하듯이, **프로그램을 만들고 있다면 모든 것을 할 수 있는 하나의 큰 구성 요소를 만드는 대신 서로 다른 클래스로 분리하는 것**이 훨씬 나음.
    - main.dart 파일에는 최대한 위젯들의 layout이 가시적으로 보이도록 구성하는 게 좋음.

### 캡슐화 Encapsulation

- 추상화 시킨 클래스들이 서로의 기능을 침범하지 않도록 캡슐화시키고 싶은 곳에
    - _ (private) 표시
        
![KakaoTalk_20221120_004001574](https://user-images.githubusercontent.com/110464205/202862324-729a3e3a-92ae-4b7d-b5fc-2496b51b83e8.jpg)
        

### 상속 Inheritance

- 많은 다른 클래스와 별도의 모듈로 추상화할 때 많은 코드를 다시 작성해야 하는 것을 방지하기 위해 상속이 필요함.
    - 제일 간단한 예시로 statelesswidget class를 만들 때 statelesswidget에 정의되어 있는 모든 property 들을 상속 받아서 사용하고 있었음.

### 다형성 Polymorphism

- 상속받을 때 상속 받은 메서드 등을 우리가 원하는 대로 @override 로 커스텀가능.

### final vs const

- final 변수 **( 아직 덜 이해됨)**
    - 오직 한 번만 설정할 수 있음.
- const 변수
    - 컴파일 타임 상수임
        - 컴파일이란 우리가 작성한 코드를 기계가 이해할 수 있는 형식으로 변환하는 것
        - 런타임동안 액세스 불가능.
        - 코드가 컴파일된(실행) 후에 생성된 것이 있으면 const로 설정 X
        
- 플러터에서 StatelessWidget의 경우 레고 블럭처럼 불변 객체임.
    - 예를 들어 Card라는 statelesswidget의 경우 상태가 변할 수 없기 때문에 바꾸려면 Card라는 객체가 없어지고 새로운 card로 생성되면서 바뀌는 것임.

### Enum

- enum EnumName { } 로 형성
- 우리가 작성한 코드를 나중에 봐도 이해될 수 있게끔 도울 수 있는 역할.
    - 예를 들어 자동차 종류를 나타낼 때 1 = 현대차, 2 = 기아차, 3 = 삼성차 라고 했을 때, 자동차 관련 코드 작성시 1, 2, 3 처럼 숫자로 표시하면 숫자가 의미하는 바를 명확히 알기 어려움. 이 때 다음과 같이 enum 형성
        
        ```dart
        enum CarType { 
        Hyundai,
        Kia,
        Samsung,
         }
        ```
        
    - 그럼 CarType.Hyundai 처럼 코드의 의미를 알 수 있는 코드 작성 가능.
    - 
### 삼항 연산자 

<iframe src="https://dartpad.dev/embed-flutter.html?id=d70d2487c6ab42cba8b3194205801786" style="width:100%; height:500px"></iframe>

_lightIsOn ? Colors.yellow.shade600 : Colors.black, 과 같이 if - else 문을 축약한 형태로 깔끔하게 사용 가능 !

## 향후 과제 

이러한 개념들을 바탕으로 지금까지 만든 스파게티 코드들을 ,,,, 최대한 리팩토링 할 예정이고 

앞으로 작성하는 코드들은 이러한 개념을 전부 녹여서 리팩토링 할 일을 최대한 줄이는 방향으로 갈 예정입니닷 ! 

-작성자: 강창환 
