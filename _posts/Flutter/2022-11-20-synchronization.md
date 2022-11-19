1. 혼자 코드 구현시 어려웠던 점
2. 동기화 시 어려웠던 점
3. 높이 설정의 에러들 //추후

![image](https://user-images.githubusercontent.com/108365477/202861005-766a0154-5cea-425f-b890-0b510b9ad738.png)

전체적인 틀은 stless 위젯인 appbar, bottomnavbar, 내 주식 tabbar 를 그대로 사용했고
위 사진의 오늘의 발견 탭 안을 새로 구현하였다.

먼저, 혼자 구현하며 어려웠던 점은 ListView로 주식리스트를 구현하는 것이었다.
class에 대한 개념이 부족했고 ListView 와 ListView.builder 에 대한 사용경험 전무, listtile까지
비슷해 보이는 위젯들이 많았다.
/*ListView로는 세로로 나열된 다른 형태의 데이터를 스크롤할때, 모든 데이터 호출 //내주식 탭바뷰
ListView.builder로는 같은형식(주식리스트)의 데이터를 생성할때, 화면에 보이는 부분만 빌더가 호출// 거래량 탭바뷰
사용법을 먼저 정리해보면

1. Listdata class 정의 (ListView에 사용될 data class)
2.  List<Widget> 에 들어갈 데이터 입력(현재는 명시적으로 데이터를 넣어주었지만 
  추후에 json형식으로 받아와 동적으로 구현할 예정 , stful위젯사용)
3. ListView.builder 를 통해 데이터 생성
  itemBuilder를 사용하여 item을 itemcount에 맞춰서 ListView를 구성
  
  
 동기화 시 어려웠던 점 - 간단히 해결되었던건 플러터 sdk버전이 안맞았던것(upgrade 로 해결)
  난관이었던 부분은 코드 리팩토링이 되어있지않아 동기화 시 코드 수정이 많았음
  -앞으로 프로젝트를 진행하기 위해 의존성이 없는 위젯끼리는 파일 분리하는것이 중요함을 느낌
  어려웠던 점은 아니었지만 개인적으로 필요하다고 생각되는것은 변수, 파일, 위젯이름을 지을때
  딱 봐도 알수있게, 그리고 공통으로 사용되는 부분은 함수로 따로 생성
  
