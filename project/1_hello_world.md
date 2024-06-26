## hello World

- 프로젝트 목표
- 프로젝트 생성하기
- 기본 프로젝트 안드로이드와 아이폰에서 모두 실행하고 콘솔창 확인 해보기
- 화면 중앙에 글자 렌더링 하기
- 위젯이란?
- 배경 색상과 글자 색상 변경해보기
- Dart Format으로 코드 정리해서 가독성 높이기

#### Point
- 플러터 코드의 시작점인 main()함수에 대해 배운다.
- 최상위에 항상 입력되는  MateriaApp 위젯에 대해 배운다.
- 기본적인 레이아웃을 세팅할 수 있는 Scaffold 위젯을 사용해본다.
- 가운데 정렬을 해주는 Center 위젯을 사용해본다.
- 글자를 화면에 출력하는 Text 위젯을 사용해본다.


```Dart
import 'package:flutter/material.dart';  
  
void main() {  
  /// 플러터 앱을 실행한다.  
  runApp(  
    /// MaterialApp은 항상 최상위에 위치한다.
    /// Scaffold는 바로 아래에 위치한다.
    /// 위젯 - Widget    MaterialApp(  
      debugShowCheckedModeBanner: false,  
      home: Scaffold(  
        backgroundColor: Colors.black,  
        body: Center(  
          child: Text(  
            'Hello World',  
            style: TextStyle(  
              color: Colors.white,  
            ),  
          )  
        ),  
      ),  
    ),  
  );  
}
```

이 Dart 코드는 Flutter 애플리케이션을 만드는 기본적인 프로그램이다.

```dart
import 'package:flutter/material.dart';
``` 

먼저, `flutter/material.dart` 패키지를 가져온다. 
이 패키지는 Flutter 애플리케이션에서 자주 사용하는 Material Design 위젯들을 포함한다.

```dart
void main() {  
  runApp(
    MaterialApp(
      debugShowCheckedModeBanner: false,  
      home: Scaffold(  
        backgroundColor: Colors.black,  
        body: Center(  
          child: Text(  
            'Hello World',  
            style: TextStyle(  
              color: Colors.white,  
            ),  
          )  
        ),  
      ),  
    ),  
  );  
}
```
### 코드 분석

1. main 함수
```dart
void main() {
  runApp(
```

  애플리케이션의 시작점. `main` 함수에서 `runApp` 함수를 호출한다.
  
2. MaterialApp 위젯
```dart
MaterialApp(
  debugShowCheckedModeBanner: false,
```

`MaterialApp`은 Flutter 애플리케이션의 최상위 위젯이다.
일반적으로 애플리케이션의 전반적인 테마와 라우팅을 설정한다.
  
`debugShowCheckedModeBanner: false`는 디버그 모드에서 나타나는 디버그 배너를 숨긴다.


3. Scaffold 위젯
```dart
home: Scaffold(
  backgroundColor: Colors.black,
```

`Scaffold`는 화면의 기본적인 구조와 레이아웃을 정의한다.
일반적으로 앱 바, 드로어, 플로팅 액션 버튼 등을 포함할 수 있다.
    
`backgroundColor: Colors.black`는 화면의 배경색을 검정색으로 설정한다.

4. Center 위젯
```dart
body: Center(
```

`Center` 위젯은 자식 위젯을 중앙에 배치한다.

5. Text 위젯
```dart
child: Text(  
  'Hello World',  
  style: TextStyle(  
    color: Colors.white,  
  ),  
```
`Text` 위젯은 화면에 텍스트를 표시한다.

`style: TextStyle( color: Colors.white, )`는 텍스트 스타일을 흰색으로 설정한다.

### 전체 코드 동작

- 애플리케이션이 시작되면 `runApp` 함수가 `MaterialApp` 위젯을 실행한다.
- `MaterialApp` 위젯은 최상위 위젯으로, `Scaffold` 위젯을 `home` 속성으로 가진다.
- `Scaffold` 위젯은 검정색 배경을 가지며, 그 중앙에 `Center` 위젯을 배치한다.
- `Center` 위젯은 화면 중앙에 `Text` 위젯을 배치하여 "Hello World" 텍스트를 흰색으로 표시한다.

검정색 배경의 화면 중앙에 "Hello World"라는 흰색 텍스트가 표시되는
간단한 애플리케이션이 완성된다.