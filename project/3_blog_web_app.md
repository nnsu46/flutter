## Blog Web App

- 프로젝트 목표
- Semantic Versioning
- Pub.dev 구경 및 외부 패키지 추가해보기
- 안드로이드 네이티브 세팅 변경하기
- AppBar 디자인하기
- WebView 초기화하기
- 웹사이트 웹뷰에 띄우기 & 다큐멘테이션 읽어보기
- 콜백 함수 이용해서 홈으로 버튼 만들어보기
- JavascriptMode 변경하기

### 프로젝트 목표

#### Point

- Controller 개념
- 외부 패키지 사용법
- Pun.dev 사용법
- Semantic Versioning
- Callback 함수

### Semantic Versioning

- Semantic Versioning: 소프트웨어 버전 관리의 표준화된 규칙이다.
- [MAJOR].[MINOR].[PATCH] 점으로 구분한다.
- MAJOR 버전: 하위 호황성을 깨뜨리는 중요한 변경이 있을 때 올린다. 주로 기존 APi의 변경이나 기능의 큰 변화를 의미한다.
	- 5.0.0 버전을 만들었다고 한다면 앞자리가 4(4.0.0)인 어떤 버전과도 호환이 안 될 가능성이 높다.
- MINOR 버전: 하위 호환성을 유지하면서 기능이 추가될 때 올린다. 주로 새로운 기능이 소개되지만, 기존 코드에 영향을 주지 않는 변경 사항이다. (4.1.0)
- PATCH 버전: 하위 호환성을 유지하면서 기존 기능의 버그를 수정할 때 올린다. 새로운 기능이나 API 변경 없이 오로지 버그 수정 관련 업데이트이다.
- 앞의 숫자부터 뒤로 갈수록 덜 중요한 업데이트라 할 수 있다.
- 4.0.0 버전은 5.0.0버전이 나올 때까지 모든 버전과 호환이 된다. (4.999.999라도)
- 즉, Major 버전 업데이트가 아니라면 패키지 사용 방법이 변하지 않는다고 봐도 무방하다. 그래서 "^"(캐럿)을 사용해서 **Major 버전 업데이트 외의 모든 버전**을 최신 버전으로 유지 할 수 있다.
- ^4.3.2
	- 4.3.3 버전이 출시될 경우 자동으로 최신버전을 다운받아 사용한다.
	- 4.4.0 버전이 출시될 경우 자동으로 최신버전을 다운받아 사용한다.
	- 5.0.0 버전이 출시될 경우 최신 버전을 다운받지 않는다.
	- Major 버전이 4인 버전만 최신으로 업데이트한다.
- "^"을 사용해서 개발을 했던 순간에 사용했던 플러그인과 호환이 되는 플로그인 중 가장 최신의 버전 사용이 가능하다.

### Pub.dev 구경 및 외부 패키지 추가해보기

- Google - pub.dev 검색
- 플러터에서 사용할 수 있는 패키지들을 쉽게 검색 가능하다.
- pub.dev - web view 검색
	- SORT BY: 정렬 변경
		- likes, pub points 위주로 고르는 게 좋다.
	- 인증마크가 달린 ((Ex) flutter.dev(실제 플러터 팀)) 자료는 신뢰도가 높다.
	- Dart 3 compatible 은 Dart 3.0 이상을 사용할 수 있다는 의미이다.
		- 이 마크가 없으면 최신 버전의 플러터에서는 작동 하지 않을 수 있다.
	- PLATFORM: 내가 개발하려는 플랫폼을 지원하는 지 확인한다.
	- Readme: 설명서
		- 플랫폼 별로 따로 설정을 해줘야 하는 부분이 적혀 있는 경우가 있다.
	- Changelog: 어떤 버전에서 어떤 기능이 추가됐는지 알려준다.
	- Example: 예제를 코드로 보여준다.
	- Installing: 설치 방법
	- Versions: 어떤 버전들을 사용할 수 있고 언제 출시되었는 지 보여준다.
		- 출시가 활발한 패키지일수록 지원을 많이 받을 수 있다.
- 사용할 패키지(webview_flutter)에 들어간 후 제목 옆의 복사 버튼을 누른다.
- 프로젝트 파일로 돌아와 pubspec.yami - dependecies(의존성) 밑에 붙어넣는다.
- cupertino_icons: ^1.0.6: iOS 스타일의 아이콘들을 사용할 수 있게 해주는 기본 제공 패키지.
- ^ 이 있어야 새로운 magor버전이 업데이트 되기 전까지의 최신 버전을 자동 업데이트 받을 수 있다.
- <주의> 붙어넣은 패키지 옆의 공백(스페이스바 갯수)을 정확히 따라해야 함.
	- yami 파일 타입은 띄어쓰기 갯수로 어디에 종속되는 값인지를 정한다.
	- 의존성들을 추가할 때는 Dependecies의 자식으로 추가해줘야 하기 때문에 띄어쓰기 2개만 넣어주어야 한다.
- pubspec.yami 파일의 오른쪽 상단의 Pub get 버튼을 누르면 Dependencies 안에 넣어놓은 플러그인, 패키지들을 다운로드 받게 되고 어떤 버전의 패키지를 다ㅜㅇㄴ롣즈 받을지 결정하게 된다.

### 안드로이드 네이티브 세팅 변경하기

- 경로를 정확히 파악하고 찾아 들어가야 한다.

### AppBar 디자인하기

```Dart
import 'package:flutter/material.dart';  
  
class HomeScreen extends StatelessWidget {  
  const HomeScreen({super.key});  
  
  @override  
  Widget build(BuildContext context) {  
    return Scaffold(  
      appBar: AppBar(  
        backgroundColor: Colors.orange,  
        title: Text('Code Factory'),  
        centerTitle: true,  
      ),    );  }}
```
- centerTitle: true 
	- 제목을 중앙에 넣는다.

### WebView 초기화하기

- AppBar 끝나고 Scaffold 안에 입력한다.
`body: WebViewWidget(),`
- Controller 파라미터 필수인데 컨트롤러가 제공되지 않았다는 오류가 뜬다.
`WebViewController controller = WebViewController();`
- 클래스 선언 밑에 Controller 변수 선언
	- WebViewController 타입으로 controller이라는 변수를 만들 건데 WebViewController를 인스턴스해와서 만들것이다.
	- 에러 발생
		- const 생성자를 만들려면 이 안의 모든 값들도 const로 선언할 수 있어야 한다.
		- WebViewController는 const 생성자가 존재하지 않는다.
		- 이전 HomScreen const를 삭제하면 에러가 사라진다.
```Dart
body: WebViewWidget(  
  controller: controller,  
),
```

- 이제 WevViewWidget의 Controller parameter에 Controller을 입력한다.
- 에러 발생
	- Controller 선언 시 Widget에 Widget선언을 해줘야 한다.
`WidgetsFlutterBinding.ensureInitialized();`
-  main.dart에 가서 ensureInitialized 함수를 실행한다.
	- Flutter 프레임워크가 실행할 준비가 될 때까지 기다린다.
- 이 코드는 원래 Run 앱 실행 시 자동으로 실행이 되지만, 현재 HomeScreen안의 StatelessWidget에서 이 Controller를 쓰기 때문에 직접 실행해 준다.

### 웹사이트 웹뷰에 띄우기 & 다큐멘테이션 읽어보기

```Dart
final homeUrl = Uri.parse('https://blog.codefactory.ai')  
  
class HomeScreen extends StatelessWidget {  
  
  WebViewController controller = WebViewController()  
      ..loadRequest(homeUrl);
```

- `'..'` : 함수를 실행한 결과 값을 반환하는 게 아닌, 함수를 실행한 대상을 반환한다.
	- `loadRequest`도 실행이 된 것이다.


### 콜백 함수 이용해서 홈으로 버튼 만들어보기

```Dart
actions: [  
  IconButton(  
    onPressed: (){  
      controller.loadRequest(homeUrl);  
    },    icon: Icon(  
      Icons.home,  
    )  
   )
```

- `onPressed: (){}` 콜백 함수
	- 버튼을 클릭했을 때 실행될 동작을 정의한다.
- `controller.loadRequest(homeUrl)`
	- `controller`객체의 `loadRequest` 메서드를 호출해서 `homeUrl`을 로드한다.

### JavascriptMode 변경하기

```Dart
..setJavaScriptMode(JavaScriptMode.unrestricted)
```

- Android는 기본적으로 자바스크립트 모드가 비활성화되어 있다.
- iOS는  기본적으로 자바스크립트 모드가 활성화되어 있다.

## 최종 코드

```Dart
import 'package:flutter/material.dart';  
import 'package:webview_flutter/webview_flutter.dart';  

// 홈 URL 정의
final homeUrl = Uri.parse('https://blog.codefactory.ai');  

class HomeScreen extends StatelessWidget {  
  // WebViewController 초기화 및 설정
  WebViewController controller = WebViewController()  
    ..setJavaScriptMode(JavaScriptMode.unrestricted)  // JavaScript 모드 설정
    ..loadRequest(homeUrl);  // 홈 URL 로드
  
  HomeScreen({super.key});  
  
  @override  
  Widget build(BuildContext context) {  
    return Scaffold(  
      appBar: AppBar(  
        backgroundColor: Colors.orange,  // AppBar 배경 색상 설정
        title: Text('Code Factory'),  // AppBar 제목 설정
        centerTitle: true,  // 제목 가운데 정렬
        actions: [  
          IconButton(  
              onPressed: () {  
                controller.loadRequest(homeUrl);  // 홈 버튼 클릭 시 홈 URL 다시 로드
              },              
              icon: Icon(  
                Icons.home,  // 홈 아이콘
              )
             )        
           ],      
          ),      
          body: WebViewWidget(  
	        controller: controller,  // WebView 위젯에 WebViewController 설정
      ),   
    ); 
 }
}
```