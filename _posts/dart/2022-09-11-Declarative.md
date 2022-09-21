---
layout: single
title: Declarative programming 
categories:
  - Dart
tags:
  - [Flutter]
toc: true
date: 2022-09-11
---

## 선언형 프로그래밍 정의와 예시

♦ 명령형 프로그래밍(imperative programming)은 언어 해석이 순차적이며 어떠한 방법으로 문제를 해결할지 가 주요 관심<br/>
♦ 선언형 프로그래밍(declarative)은 순서나 문제 해결 과정을 다루기보다 **무엇을** 나타내야 할지에 초점<br/>

이렇게 말하면 이해가 잘 안가니 예를 들어 설명해보면, 샌드위치를 만들 때(재료는 있다고 가정)<br/>

명령형(HOW): 빵을 맨 밑에 두고 그 위에 머스타드를 발라. 그 위에 양상추를 올리고 그 위에 토마토를 올려. 그 다음 패티를 올리고 빵을 맨 위에 덮어.<br/>

선언형(HOW): 샌드위치 만들어.

물론 선언적 방식의 접근을 위해서는 명령형 방식으로 '어떻게 접근하는가'가 먼저 추상화가 되어있어야 한다.<br/>

샌드위치를 만들어라고 시키는 것은 어떤 것을 둔다는 개념, 소스를 바른다는 개념 등을 알고 있다고 전제하는 것이다.<br/>

즉, 선언적 접근 방식의 기저에는 명령형이 깔려있고 **추상화** 된 것이다.

## 선언형 프로그래밍 dart코드 예시(UI)

![Declarative programming](https://user-images.githubusercontent.com/108365477/189506289-5d3d8a46-8fcc-4a38-aec6-8733c2fc3457.png)<br/>
출처: 인문주

위의 UI에서 절반 기준 위쪽은 View A, 아래쪽은 View B<br/>

다음은 View A를 구현한 dart 소스코드 입니다.

```dart
class _ViewA extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final value = Provider.of<AppState>(context).sum;
    return Container(
      color: Colors.black,
      child: Center(
        child: Text(
          '$value',
          style: TextStyle(color: Colors.white, fontSize: 40),
        ),
      ),
    );
  }
}
```


**build 함수는 UI 객체에 해당하는 위젯(Widget)을 반환합니다.<br/>
반환된 위젯은 Flutter 플랫폼에 의해 UI에 표시됩니다. 위젯의 구체적인 내용은 Container입니다. 위에서Container는 검은색의 사각형을 표시합니다.<br/> 
Container는 Center를 포함하고 있습니다. Center는 자식 위젯인 Text를 화면의 가운데에 위치시킵니다. Text는 앱 상태(AppState)로 정의된 sum의 값을 표시하고 있습니다. 모든 UI 객체가 '선언'되기 때문에 '명령'이 없습니다.<br/> 
특히 _ViewA가 StatelessWidget을 상속한다는 것은 View A에 상태 변수가 없다는 것을 의미합니다. View A는 sum을 화면에 표시하는 일만 수행합니다.**

다음은 View B를 구현한 dart 소스코드 입니다.

```dart
class _ViewB extends StatefulWidget {
  _ViewB({required this.onUpdate});

  final Function(int value) onUpdate;

  @override
  State<StatefulWidget> createState() {
    return _ViewBState();
  }
}

class _ViewBState extends State<_ViewB> {
  var localCount = 0;

  @override
  Widget build(BuildContext context) {
    return Center(
      child: ElevatedButton(
        child: Text('$localCount'),
        onPressed: () {
          setState(() {
            widget.onUpdate(++localCount);
          });
        },
      ),
    );
  }
}
```

**_ViewBState에 상태 변수로 선언된 localCount의 값은 onPressed로 버튼 이벤트가 전달될 때 ++localCount에 의해 증가합니다.<br/> 그리고 setState를 호출하면 build 함수가 다시 실행되면서 UI에 localCount의 변경된 값이 반영됩니다.**
