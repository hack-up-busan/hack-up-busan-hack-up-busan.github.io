---
layout: single
title: Flutter 간단한 드롭다운 만들기 Expansiontile
categories:
  - Flutter
tags:
  - [Dropdown, widget]
toc: true
date: 2023-01-05
---
## Flutter 드롭다운 만들기

[지난글](https://hack-up-busan.github.io/flutter/%EC%83%81%ED%83%9C%EA%B4%80%EB%A6%AC/)

지난 시간에 이어 드롭다운(dropdown)을 만드는 방법을 알아보도록 하자. 지난 포스팅에서는 드롭다운에 대해 너무 어렵게 생각 했었기 때문에 
상태관리에 관한 부분까지 다루는 지경까지 갔었지만 드롭다운 자체를 만드는데에는 이미 만들어진 훌륭한 widget이 존재하였다. 

## Expansiontile
Expensiontile이 그 주인공이다. 
<iframe src="https://dartpad.dev/embed-flutter.html?id=d4f94e6e79049227a09e7b3a2d0fe0f5" style="width:120%; height:700px"></iframe>

보기와 같이 children에 리스트로 위젯들을 등록하면 
바로 드롭 다운으로 동작을 한다. 
또한 trailing과 onExpansionChanged로  Icon을 커스텀하거나 controlAffinity로 드롭다운 버튼을 앞으로 위치시키는것도 가능하다. 

## 토스에 적용

<iframe src="https://dartpad.dev/embed-flutter.html?id=125c9e61db5971e77c2cfc7145d3e8d3" style="width:120%; height:700px"></iframe>

###: YunSukHyun
