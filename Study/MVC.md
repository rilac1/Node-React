# MVC란?
### Model-View-Controller

MVC는 Mode-View-Controller의 약자로서 개발할 때 3가지 형태로 구분하여 개발하는 **소프트웨어 개발 방법론** 이다.
- Model
  - 어플리케이션이 "무엇"을 할지 정의함.
  - ex) 처리되는 알고리즘, DB와 상호작용(CRUD)
- Controller
  - 모델이 "어떻게" 처리할지를 결정함.
  - 요청내용을 분석해서 Model과 View에 업데이트 요청을 하게됨.
- View
  - 화면에 무엇인가를 "보여주기"위한 역할을 함.
  - ex) 최종 사용자에게 UI를 보여줌.

> Model과 View는 직접 통신이 불가능함. 오로지 Controller를 통해서만 가능.