---
layout: single
categories:
  - Flutter
title: Flutter 화면 간 이동시키기
date: 2022-11-03
toc: true
comments : true
---
## Displaying a full-screen route
- MaterialApp의 home이 Navigator 스택의 가장 밑이 되고 앱이 시작될 때 보이는 것임
        
```dart
void main() {
runApp(MaterialApp(home: MyAppHome()));
        }
```
        
- 여기서 push 메소드는 내가 이동하고 싶은 Route(페이지)를 Navitor 현재 스택에 추가하는 것을 얘기함. 
    
 ```dart
Navigotor.push(context, MaterialPageRoute(
  builder: (context) {
  return Scaffold();}
```
    
## named navigator routes 사용하기( 많은 페이지를 관리할 때 용이 )
- 보통 모바일 앱은 많은 페이지를 가지고 있음. 따라서 페이지 이름을 정해서 사용 것이 더 관리하기 쉬움.
- 페이지 이름은 문자열(’/a’ ‘/b’ ‘/c’)처럼 설정.
- 앱의 메인 페이지는 ‘/’ 기본 설정되어 있음.
- routes (페이지) 설정은 MaterialApp의 property 이고 이는 Map<String, WidgetBuilder> 구조로 설정됨.
- 밑 코드에서 보듯 routes 는 Map 구조로 <Key : Value>
- ⇒ <String( 페이지 이름) : WidgetBuilder( (context) ⇒ 이동시킬 페이지 생성자) ) 로 정함.
    
```dart
void main() {
  runApp(MaterialApp(
    home: MyAppHome(), // becomes the route named '/'
    routes: <String, WidgetBuilder> {
        '/a': (BuildContext context) => MyPage(title: 'page A'),
        '/b': (BuildContext context) => MyPage(title: 'page B'),
        '/c': (BuildContext context) => MyPage(title: 'page C'),
      },
    ));
  }
```
    
- 버튼을 누르는 등 그 페이지로 이동시키도록 기능을 추가하려면 버튼의 onTap / onPressed 의 함수 바디 {   } 안에  다음과 같은 네비게이터 인스턴스를 생성.
    
```dart
  Navigator.pushNamed(context, '/b') 
```
    
- Routes can return a value
- Popup routes
- Custom routes
- ModalRoute
- onGenerateRoute
- onUnknownRoute
    - 초기 route(홈페이지)를 설정하지 않았을 때 or 에러가 났을 때 최후의 수단으로 onUnownRoute에 설정한 route로 user에게 보여줄 수 있음.
    - 일종의 Flutter의 error 처리 방법(페이지 경로 문제)
        
```dart
      onUnknownRoute: (settings) {
        return MaterialPageRoute(builder: (ctx) => MyPageScreen();
        }
```
        

[Navigator class - widgets library - Dart API](https://api.flutter.dev/flutter/widgets/Navigator-class.html)

- 작성자: 강창환
