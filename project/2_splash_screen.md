## Splash Screen

- 프로젝트 소개
- YAML 구조
- Asset 파일 pubspec.yaml에 등록하기
- Image 위젯 사용해보기
- Hex Code를 사용해서 색상 지정하기
- Column 위젯 사용해보기
- CircularProgressIndicator 위젯 사용해보기
- StatelessWidget 선언해보기
- stless 단축어 사용해서 StatelessWidget 생성하기
- Padding 위젯 사용해보기 &amp; Hot Reload 사용해보기
- SizedBox 위젯 사용해보기
- Show Context Action 사용해보기

#### Point
- StatelessWidget 사용법
- Asset 이미지 등록법
- Image 위젯 사용법
- Column 위젯 사용법
- HexCode 색상 사용법
- CircularProgressIndicator 위젯 사용법
- Padding 위젯 사용법
- SizeBox 위젯 사용

- 스프래시 스크린 = 시작 로딩화면
	사용자 검증, 어떤 화면을 보여줄 지 정하는 로직을 실행한다거나, 코드들을 실행하는 동안 사용자한테 앱이 멈춘 게 아닌 무언가 작업을 하고 있다는 걸 보여주기 위해 보여주는 화면
### YAML Structure

- 사람이 쉽게 알고 쓸 수 있는 데이터 직렬화(컴퓨터가 읽을 수 있는 쉬운 구조로 변경) 언어이다.
- 주로 설정 파일이나 데이터 전송 형식으로 사용되며 들여쓰기를 통해 계층 구조를 표현한다.

#### Key / Value Pair

```
{
	'name' : 'Code Factory',
	'age' : 32,
	'gender' : 'Male'
}
```

```Dart
name: Code Factory
age: 32
gender: Male
```
- :(콜론)뒤에 한 칸 꼭 띄어야 한다.

#### List
```
{
	'ive_members' : [
	  'YuJin',
	  'WondYoung',
	  'Rei',
	  'GaEul',
	  'Eseo'
	]
}	
```

```Dart
ive_members:
	- YouJin
	- WonYoung
	- Rei
	- Gaeul
	- Eseo
```

#### Nested Key / Value Pair

```
{
	'person':{
	  'namme': 'Code Factory',
	  'age': 32,
	  'address':{
	    'city': 'Seoul',
	    'country': 'South Korea'
	    }
	}
}
```

```Dart
person:
  name: Code Factory
  age: 32
  address:
    city: Seoul
    country: South Korea
```
- 두 칸씩 띄운다.

#### Complex Structure

```
{
	'members': [
	{
	  'name': 'Rei',
	  'age': 20
	},
	{
	  'name': 'WonYoung',
	  'age': 21
	}
  ]
}
```

```Dart
memebrs:
  - name: Rei
    age: 20
  - name: WonYoung
    age: 21
```

#### Comment

```Dart
# 이건 주석입니다.
app_name: hello_world # 이것도 주석입니다.
```


### Asset 파일 pubspec.yaml에 등록하기

- 앱에서 사용할 무언가를 집어 넣는 공간을 Asset  폴더라고 이름을 일반적으로 짓는다.

asset/ img/logo.png
경로에 이미지 넣고 나서
pubspec.yami
flutter 안에
uses-material-design: true
밑에 두 칸 띄우고 asstes: 작성
다음 줄에 - asset/img/ 작성 -> 이미지 폴더 안에 있는 모든 이미지를 사용할 수 있도록 한다.
오른쪽 상단에 Pub get버튼을 눌러 변경된 사항을 적용한다.
0이 나오면 성공(1은 실패)

### Image 위젯 사용해보기

`Image.asset('asset/img/logo.png')`

### Hex Code를 사용해서 색상 지정하기

- color picker
- flutter는 16진수
- 16진수를 flutter에서 표현하는 방법 : 0x
- ff : 알파, 투명도. RGB값에 해당되는 정확한 값을 입력 가능하다.

`Color(0xFF335CB0)`

### Column 위젯 사용해보기

- Center 위젯은 child위젯이라고 해서 자식, 단 하나의 위젯만 입력 가능하다.
- 여러개의 위젯을 가운데 정렬할 수 있는 위젯 : Column
- mainAxisAlignment: 주축에서 정렬
	(<-> crossAxisAlignment)

```Dart
body: Column(  
  mainAxisAlignment: MainAxisAlignment.center,  
  children: [  
    Image.asset(  
      'asset/img/logo.png',
```
### CircularProgressIndicator 위젯 사용해보기

```Dart
// Image.asset 밑에
CircularProgressIndicator(  
  color: Colors.white,
```

### StatelessWidget 선언해보기

```Dart
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(  
    MaterialApp(  
      home: HomeScreen(),  
    ),  
  );  
}  
  
/// StatelessWidget  
class HomeScreen extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return Scaffold(  
        /// 335CB0  
        backgroundColor: Color(0xFF335CB0),  
        body: Column(  
          mainAxisAlignment: MainAxisAlignment.center,  
          children: [  
            Image.asset(  
              'asset/img/logo.png',  
            ),  
            CircularProgressIndicator(  
              color: Colors.white,  
            ),  
          ],  
        ));  
  }  
}
```
- build 누르고 엔터->오버라이딩 자동완성
### stless 단축어 사용해서 StatelessWidget 생성하기

- stless 작성하면 자동 완성된다.

### Padding 위젯 사용해보기 & Hot Reload 사용해보기

```Dart
body: Padding(  
    padding: EdgeInsets.symmetric(  
      horizontal: 32.0,  
    ),
```
- Padding 위젯은 padding 파라미터를 꼭 입력해야 한다.
- EdgeInsets: 테두리 간격
- symmetric: 대칭
- horizontal: 수평 (생략 가능)
- vertical: 수직 (생략 가능)
### SizedBox 위젯 사용해보기

```Dart
children: [  
  Image.asset(  
    'asset/img/logo.png',  
  ),  
  SizedBox(height: 28.0),  
  CircularProgressIndicator(  
      color: Colors.white,  
    ),  
],
```
- SizedBox: 높이가 있는 박스
	- 기본적으로 투명 색이기 때문에 패딩과 똑같은 효과를 준다.
	- 패딩보다 조금 더 효율이 좋다.
### Show Context Action 사용해보기
- 삭제하고 싶은 위젯 위에 커서를 올린 후 오른쪽 클릭
	Remove this widget 클릭
	- 물론 Remove가 실행 안 되는 경우도 존재한다.
	- 모든 옵션이 모든 위젯을 대상으로 하는 건 아니다.
-  Wrap With Widget


## 최종 코드

```Dart
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(  
    MaterialApp(  
      home: HomeScreen(),  // HomeScreen 위젯을 홈으로 설정
    ),  
  );  
}  
  
/// StatelessWidget  
class HomeScreen extends StatelessWidget {  
  const HomeScreen({super.key}); // 생성자 부분은 생략 가능  
  
  @override  
  Widget build(BuildContext context) {  
    return Scaffold(  
        /// 배경 색상 설정 (색상 코드: 335CB0)
        backgroundColor: Color(0xFF335CB0),  
        body: Padding(  
            padding: EdgeInsets.symmetric(  
              horizontal: 32.0,  // 좌우 여백 설정
            ),  
            child: Column(  
              mainAxisAlignment: MainAxisAlignment.center,  // 세로축 가운데 정렬
              children: [  
                Image.asset(  
                  'asset/img/logo.png',  // 이미지 경로 설정
                ),  
                SizedBox(height: 28.0),  // 이미지와 로딩 인디케이터 사이 간격 설정
                CircularProgressIndicator(  
                  color: Colors.white,  // 로딩 인디케이터 색상 설정
                ),  
              ],  
            )  
        )  
    );  
  }  
}
```
