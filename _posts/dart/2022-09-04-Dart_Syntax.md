---
layout: single
title: "Dart 기초 문법 정리"
categories:
  - Dart
tags:
  - [Flutter, syntax]
date: 2022-09-04
---

다른 프로그래밍 언어를 배우다 dart언어를 배우시는 분들을 위해 준비한 dart기초 문법입니다.<br/>내용을 딥하게 다루기 보다는 제가 평소 다루던 언어에는 없는 문법들을 위주로 공부한 것을 정리해보았습니다.<br/>코드에 주석으로 설명을 달아두었으며, 중간중간 삽입된 다트패드로 코드를 실행해보며 재밌게 공부해보시길 바랍니다.

**1. 자료형(type)**

int: 정수형<br/>
double: 실수형<br/>
bool: true, false<br/> 
String: 문자열<br/>
num: int, double을 포함하는 타입<br/>

- 집합 자료형

List: 중복을 허용하며 순서가 있는 집합<br/>
Set: 중복을 허용하지 않고 순서가 없는 집합<br/> 
Map: key-value 쌍으로 구성된 집합<br/>

```dart
**void main() {
  // 변수 type
  String name = "Bob"; 
  int age = 20;

  //List
  List<int> Nums = [1,2,3]; 
  Nums [0] = 9;

  //Map key & value pair 
  Map<String, int> NameAge ={
    "qwer": 20, 
    "asdf": 30
  };
  Name Age["qwer"] = 40; //key변경
}**
```
집합 자료형에서 list는 인덱스로 접근이 가능하지만 set, map 은 불가능하다.<br/>
num 타입을 추가로 알아보자.

```dart
**void main() { 
  // num
  int age = 25; //정수
  double weight = 65.4; //실수

  num age1 = age; //num은 int, double형 모두 대입가능
  num weight1 = weight;
  print(age1); //25 출력
  print (weight1); //65.4 출력
}**
```

num 타입은 int형과 double형을 포함하는 즉, 수를 표현하는 타입의 상위 개념이다<br/> 그러므로 num은 int, double을 모두 받을 수 있지만, 반대는 불가능하다.

**2. 선언자**

-var<br/>
-dynamic<br/>

```dart
**void main() {
  //var 선언자 - 타입추론
  var age = 23; 
  var x = word.isEmpty; 

  print("${age.runtimeType}, ${x.runtimeType}");
  //int, bool 출력

  //var 로 선언하여 문자열 할당
  var word = '랜덤값';
  print(word.runtimeType); //String 출력

  //이번에는 var 로 선언하여 숫자값을 할당
  var number = 1;
  print(number.runtimeType); // int 출력

  //var형은 타입이 정해진 이후, 형을 변환할 수 없다
  //int word = 2; => 컴파일 에러


  //위에 var로 선언 후, 다시 문자열을 재할당 해보자
  word = '랜덤값 변경' :

  // 문제없이 변경된 값으로 출력된다
  print(word); // '랜덤값 변경' 출력
}**
```

var, dynamic 선언자는 정해진 값이 명확하지 않을 때 사용하여 최초 할당된 값에 따라변화한다.<br/> var 선언자는 내가 할당한 값에 의해 타입이 정해지고, 그 이후에는 타입을 바꿀 수 없다.<br/>
cf.runtimeType - 타입 반환 함수

---
var 타입의 특이점 

<iframe src="https://dartpad.dev/embed-dart.html?id=7c24cd351900efaa517583b9f27c80b9" style="width:140%; height:450px"></iframe>

```dart
**void main() { 
  // dynamic 선언자 - 타입변경 
  dynamic Name = '다이나믹값';

  //var 선언자를 사용했을때 처럼 문제없이 출력된다.
  print(Name); //'다이나믹값' 출력

  //var 선언자와 달리 
  //dynamic 선언자를 사용하면 에러없이 값의 종류를 바꿀 수 있다
  //dynamic은 할당된 변수값의 종류에 영향없이 타입이 변경되는 선언자이다

  Name = 1; //1 출력
  print(Name);
}**
```
다이나믹한 변동성이 있는 dynamic 선언자는 타입추론, 변경 둘 다 가능하다.

**3. 연산자**

-논리 연산자<br/>

&&: 그리고<br/>II : 또는<br/>

-증감 연산자<br/>

전위 연산: ++ [식] --[식]<br/>후위 연산: [식] ++, [식]--<br/>

-비교 연산자<br/>

>=: 크거나 같다<br/>==: 같다<br/>

```dart
**void main() {
  // 산술 연산자 (+,-,*,/,~/,%)
  var a = 5; 
  var b = 2;
  print(a ~/ b); // 몫(int) 출력

  // 증감 연산자
  print(a += 4); 
  // 비교 논리 연산자 
  if (a >= 8 && b ==2) { 
    print("true");
  }
}**
```

---
연산자 이해 확인용 문제 

<iframe src="https://dartpad.dev/embed-dart.html?id=b7890a47355d696ff13f0bd397a14414" style="width:140%; height:450px"></iframe>


-삼항 연산자

![flutter syntax](https://user-images.githubusercontent.com/108365477/189390020-ce3a4b9e-da28-4c22-a306-4943c052cc1c.png)

Condition ? A:B

Condition이 참이면 A 실행,거짓이면 B 실행

if-else 가 있는데 삼항 연산자를 쓰는이유는 코드의 길이를 줄일 수 있는경우도 있지만,

if/else - 문(statement) 으로서 if자체로는 아무런 값을 만들어내지않는다.

삼항연산자 - 식(expression)으로서 값을 만들어낸다.

-null check 연산자

```dart
**void main(){
//?? 연산자
  String a;
  String b = 'Hi';
  String c = 'Good";

  a = b ?? c;
  //a = b ?? c;
  //b가 null이 아니면 a에 배정한다.

  print('a = ${a}');

  //??= 연산자  
  int? i; //null
  i ??= 2; //2 할당
  print(i); //2 출력

  //i??= k;
  //i가 null이면 k를 넣는다.

  int? k = 1; //null 아님
  k ??= 2; //2 할당
  print(k); //에러는 안나지만 1 출력
}**
```

**4. 함수**

```dart
**void main() { 
  // 함수 - 리턴 값 타입 함수명 (매개변수 타입 매개변수){}
  void introduce (String name, [String food = 'snack']) { 
  //[파라미터] - optional parameter 
  //[파라미터 = default] - 기본값 설정 
    print('I am $name, I like $food!');
  }
  introduce ('Tom'); //I am Tom, I like snack!
  introduce('Tom', 'pizza'); //I am Tom, I like pizza!

  //named parameter - 순서 상관x 
    add({
      required int x, 
      required int y, 
      required int z,

    }) {
    int sum = x+y+z; 
    print (sum);
  }
  add(x: 10, y: 20, z: 30); //60 출력
  add(y: 20, x: 10, z: 30); //60 
}**
```

---
named parameter , optional parameter 추가설명과 코드 

<iframe src="https://dartpad.dev/embed-dart.html?id=9507d86b7f8abd0d82fe0926d734109f" style="width:140%; height:450px"></iframe>

**5. typedef**

```dart
**void main(){
  Operation operation = add; 
  int result = operation (10, 20, 30);

  print (result); //60 출력

  operation = subtract; 
  int result2 = operation (10, 20, 30);

  print (result2); //-40 출력
  print (calculate (1, 2, 3, add)); //6 출력
  print(calculate (1, 2, 3, subtract)); //-4 출력

  // signature
  typedef Operation = int Function(int x, int y, int z);

  // 더하기
  int add(int x, int y, int z) => x + y + z; 

  //빼기
  int subtract(int x, int y, int z) => x - y - z;

  // 계산
  int calculate(int x, int y, int z, Operation operation) { 
  return operation(x, y, z);
  //calculate함수에 파라미터 x , y, z 와
  //operation 을 넣으면 리턴 값으로 operation 에
  //파리미터가 들어가서 operation의 함수 실행
}**
```

typedef 를 사용하면 함수를 변수처럼 활용 가능

같은 타입의 파라미터, 리턴 값을 가진 함수는 모두 사용 가능하다.

---
위의 코드 실행 해보기 

<iframe src="https://dartpad.dev/embed-dart.html?id=252332620128aeb46fb201a73df3679a" style="width:140%; height:450px"></iframe>

**6. 문자열 변수 사용**

```dart
**void main() { 
  void printName(String name) {
    print("I'm $name."); 
  } //$변수 - 문자열 내에서 어떤 변수의 값을 그대로 사용 
  printName("Bob"); //I'm Bob 출력

  void printAge(int age) { 
    print("I'm an ${age > 18 ? 'adult' : adolescence'}"); 
    //표현식을 써야 할 때는 반드시 ${}
    printAge(7); //adolescence 
  }
  
  **7. 상수**
  
  -final<br/>
  -const<br/>
  
  ```dart
  **void main() {
    const Datetime rightNow = Datetime.now(); => error
    final Datetime rightNow = Datetime.now();
  }**
   ```
 현재 시간을 가져오는 DateTime.now(); 는 런타임 시점에서 결정되기 때문에 
 const에서 에러가 난다.
 
 const는 컴퓨터 언어로 번역되는 컴파일 과정에서 상수가 된다. 
  >> 런타임 시점에 결정되는 값은 const에 담을 수 없다.

  final은 번역 후 실제로 프로그램이 실제 실행되는 과정에서 
  상수가 된다. 

  **8. enum**

```dart
**enum Status {
    approved,
    pending,
    rejected,
  } //enum {상수 값}

  void main() {
  Status status = Status.approved;

  if (status == Status.approved) { 
    print('승인입니다'); 
   } else if (status == Status.pending) 
    print('대기입니다'; 
   } else {
    print('거절입니다');
  }
  print (Status.values); //상수 전체 값 
}**
```

enum 을 사용하면 한정된 상수 값 집합을 나타낼 때 유용하다.
 
정확히 이 값만 존재 - 다른 값이 들어오면 에러<br/>
몇가지 타입만 사용하도록 강제 가능<br/>
오타 방지<br/>

따라서 직관적이고 에러없는 코드 작성에 용이하다.

**9. nullable / non-nullable**

![flutter syntax](https://user-images.githubusercontent.com/108365477/189398690-bdb91616-2182-4c86-82d9-10df4e06f94f.png)

null = 아무런 값도 될 수 없다.

이때까지 배운 모든 타입은 2가지로 나뉜다. 

첫번째는 그 타입만 들어갈 수 있는 경우,

두번째는 그 타입과 null까지 들어갈 수 있는 경우.

그러나 타입 뒤에 물음표를 붙이면 어떤 타입이든 null도 들어갈 수 있게 되는데,<br/>
이것이 nullable이다.

반대로 null을 절대 받을 수 없게 하고 싶다면 느낌표를 붙여주면 non-nullable 을 의미한다.


여기까지 dart기초 문법에 대해 분석해보았습니다. 

혹여나 살펴보면서 잘 모르는 부분이나 궁금하신 점이 있으시다면 편하게 댓글 남겨주시면 감사하겠습니다:)

**작성자: Lee yeseul** <br/>
