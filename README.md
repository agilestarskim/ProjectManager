# Project Manager

## 📖 목차
🍀 [소개](#소개) </br>
💻 [실행 화면](#실행_화면) </br>
🛠️ [사용 기술](#사용_기술) </br>
👀 [다이어그램](#Diagram) </br>
🧨 [트러블 슈팅](#트러블_슈팅) </br>
📚 [참고 링크](#참고_링크) </br>

</br>

## 🍀 소개<a id="소개"></a>

하나의 프로젝트를 TODO, DOING, DONE 섹션으로 세분화하여 관리할 수 있는 어플리케이션입니다.  
각 셀을 길게 클릭하여 할 일의 상태를 변경할 수 있고 스와이프를 통해 삭제할 수 있습니다.  
상단 바에 위치한 + 버튼을 눌러 새로운 셀을 추가하거나 기존의 셀을 클릭하여 수정할 수 있습니다.  
모든 활동들은 로컬 데이터베이스 저장되고 활동 내역을 리스트 형태로 확인할 수 있습니다.  
기기를 바꿔도 데이터를 영구보관 할 수 있도록 서버에 저장합니다.  
서버에 유저를 식별할 수 있도록 로그인 로그아웃을 제공합니다.  


</br>

## 💻 실행 화면<a id="실행_화면"></a>


</br>

## 🛠️ 사용 기술<a id="사용_기술"></a>
| 구현 내용	| 도구 |
|:---:|:---:|
|UI|SwiftUI|
|아키텍쳐|클린 아키텍쳐 + MVVM|
|로컬 데이터|Realm|
|리모트 데이터|Firebase|
|비동기처리|Async/Await|

</br>

## 👀 Diagram<a id="Diagram"></a>


</br>

## 🧨 트러블 슈팅<a id="트러블_슈팅"></a>


### TaskFormView 재활용

TaskFormView에서 Create와 Edit을 구현하기 위해 중복된 부분들을 어떻게 처리할까 고민했습니다.

1️⃣ View의 init에서 분기처리

view를 init할 때 optional Task를 사용해, create일 경우 nil, edit일 경우 수정할 task를 주입하여 분기처리를 하였습니다. 단점은 init에 로직이 들어가 복잡해지고 기능이 추가될 때마다 수정할 부분도 많아지고 사용하지 않은 메소드들을 viewModel에 모두 집어넣어야한다는 문제가 있었습니다.

[Optional Task를 이용](https://github.com/WhalesJin/ios-project-manager/blob/f2d72324a03fabdb7f51d02ce3442bcc2aaa28e3/ProjectManager/ProjectManager/Presentation/Kanban/TaskForm/TaskFormView.swift)

2️⃣ Protocol을 이용해 구현하기

Create와 Edit을 관찰해보니 중복되는 부분이 많아서 프로토콜로 기능 정의 후 Create와 Edit의 ViewModel을 각각 따로 만들어서 뷰모델을 주입하는 형식으로 구현해봤습니다. 단점은 기능이 추가될 때마다 각 뷰모델에 똑같은 메소드와 프로퍼티를 억지로 만들어야한다는 단점이 있습니다.

[Protocol 사용](https://github.com/WhalesJin/ios-project-manager/blob/ddea938b958136009b59b3b63a54f7b339904648/ProjectManager/ProjectManager/Presentation/Kanban/TaskForm/TaskFormView.swift)


<br>

## 📚 참고 링크<a id="참고_링크"></a>

- <Img src = "https://hackmd.io/_uploads/Hyyrii91T.png" width="20"/> [Firebase](https://firebase.google.com/?hl=ko)
- <Img src = "https://hackmd.io/_uploads/B1pu3oq1a.png" width="20"/> [Realm 설치](https://www.mongodb.com/docs/realm/sdk/swift/install/#std-label-ios-install)
- [🍎 Apple Docs: CloudKit](https://developer.apple.com/kr/icloud/cloudkit/)
- [🍎 Apple Docs: List](https://developer.apple.com/documentation/swiftui/list)
- [🍎 Apple Docs: ViewModifier](https://developer.apple.com/documentation/swiftui/viewmodifier)
- [🍎 Apple Docs: GeometryReader](https://developer.apple.com/documentation/swiftui/geometryreader)
- [🍎 Apple Docs: ScrollViewReader](https://developer.apple.com/documentation/swiftui/scrollviewreader)
- [🍎 Apple Docs: UnitPoint](https://developer.apple.com/documentation/swiftui/unitpoint)
- [📚 StackOverflow: ViewModel Protocol](https://stackoverflow.com/questions/59503399/how-to-define-a-protocol-as-a-type-for-a-observedobject-property)

