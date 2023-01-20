---
layout: single
title: ChatGPT 빠르게 체험해보기
categories:
  - Flutter
tags:
  - [ChatGPT]
toc: true
date: 2023-01-20
---

ChatGPT의 기능은 우리가 궁금한 내용을 입력하면 이 프로그램이 관련 내용을 알려주는 것이다.

알려줄 수 있는 내용으로는 다음과 같다.

- 컨텐츠 생성
- 요약
- 분류, 감정 분석
- 데이터 추출
- 번역
- 다른 것도 많이

공식문서 예제에서는 고양이 이름을 3가지 지어줘 ! 라고 하면 인공지능이 멋진 이름 3가지를 지어준다 ! ㅋㅋㅋ

![1](https://user-images.githubusercontent.com/110464205/213746301-a428c61b-850c-49bf-8d2a-13d78d53c652.png)<br>
그냥 말에서 검은 말로 간단한 형용사를 덧붙였는데 이름이 달라졌다. 

![2](https://user-images.githubusercontent.com/110464205/213746322-17c96295-5180-4aac-8887-5d6392703f93.png)

이와 같이 예시 등 상세한 설명을 덧붙일 수록 우리가 원하는 결과에 더 가깝게 나온다. 

![3](https://user-images.githubusercontent.com/110464205/213746362-49c40d19-014b-4821-adf5-3851f007888e.png)

위처럼, 우리가 원하는 걸 이 모델한테 여러가지 예시를 들어주고 질문을 하면 우리가 원하는 답과 더더욱 비슷하게 나옴을 알 수 있다.

![4](https://user-images.githubusercontent.com/110464205/213746379-853d2148-b749-42c3-8beb-c6662b945768.png)

Temperature 를 0으로 두면 똑같은 대답만 나오게 됨. 0에 가까울 수록 정답에 가까운 것 같고 1에 가까울 수록 창의적인 ? 답변이 나오는 것 같음.


### 어플리케이션 빌드 간단하게 따라해보기 

NODE.JS 로 진행

디렉토리를 하나 파서 다음을 클론해옴.
```dart
git clone https://github.com/openai/openai-quickstart-node.git
```

그러고 클론해온 디렉토리에서 openai-quickstart-node 디렉터리로 이동하고 .env.example .env라는 파일을 복사했음.
```dart
cd openai-quickstart-node
cp .env.example .env
```


새 api key를 생성하고 복사해서 **`.env`** file의 **OPENAI_API_KEY 프로퍼티에 할당함.**

![5](https://user-images.githubusercontent.com/110464205/213746425-19b298ca-4d07-4943-9a06-c52ad38b3b6f.png)
![6](https://user-images.githubusercontent.com/110464205/213746463-ea705d53-c1cf-410d-9cac-df985f77536a.png)

그리고 터미널에 다음 커맨드를 실행하면
```dart
npm install
npm run dev
```

![OpenAI_Quickstart_-_Chrome_2023-01-20_16-54-45_AdobeExpress](https://user-images.githubusercontent.com/110464205/213742872-0f5c16c1-c113-4750-83d0-5ba5cd07cf40.gif)

내가 원하는 동물의 이름 3가지를 지어줘 ~ ~ 라고 GPT한테 부탁하는 건데, 나는 사자 이름을 부탁했더니 초록색 버튼 밑의 3가지가 나왔다.

이를 동작시키는 중점적인 코드는 다음과 같다. 
```jsx
function generatePrompt(animal) {
  const capitalizedAnimal =
    animal[0].toUpperCase() + animal.slice(1).toLowerCase();
  return `Suggest three names for an animal that is a superhero.

Animal: Cat
Names: Captain Sharpclaw, Agent Fluffball, The Incredible Feline
Animal: Dog
Names: Ruff the Protector, Wonder Canine, Sir Barks-a-Lot
Animal: ${capitalizedAnimal}
Names:`;
}
```
즉, 슈퍼히어로와 연관시킨 동물 이름 3가지 제안해줘 ! 라고 하고 예시로
- 고양이는 Captain Sharpclaw, Agent Fluffball, The Incredible Feline
- 강아지는 Ruff the Protector, Wonder Canine, Sir Barks-a-Lot
이렇게야 라고 알려준뒤 내가 원하는 동물 종류를 기입한다. 

그럼 ! 위와 같이 사자 + 슈퍼히어로를 합친 멋진 이름 세 가지를 추천해준다.


### 사용후기

어떤 문제를 해결했을까 라는 생각을 해봤는데, 어떤 정보를 구글링하게 되면 정보가 너무 많아서 이 블로그 저 블로그 찾아야 된다는 단점이 있다.
또한 그 블로그의 글이 정말 질적으로 보장이 된건지도 모른다. 워낙 코드를 복붙해놓는 경우가 많기 때문 ! 
따라서 ChatGPT에게 물어본다면 정확성 + 원하는 정답에 가까운 정보를 알려주기 때문에 아주 매력적이라고 생각한다. 

앞으로도 모르는 거 있으면 물어볼게 PT야 ... 
