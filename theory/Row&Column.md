## Row&Column

- 프로젝트 소개
- 프로젝트 초기화
- Row &amp; Column 공부를 위한 준비
- Column MainAxisAlignment
- Row MainAxisAlignment
- Column MainAxisSize
- Row MainAxisSize
- Column CrossAxisAlignment
- Row CrossAxisAlignment
- Expanded Widget
- Flexible Widget
- Challenge
- Challenge 해답

###  프로젝트 소개

- Row 행
	* 가로로 위젯을 배치할 때 사용
	* 가로: MainAxisAlignment (최대 크기 차지)
	* 세로: CrossAxisAlignment 
		(최소 크기 차지(자식 위젯이 갖고 있는 사이즈))
- Column 열
	- 세로로 위젯을 배치할 때 사용
	- 세로: CrossAxisAlignment 반대축
	- 가로: MainAxisAlignment 주축
- MainAxisAlignment 주축
- CrossAxisAlignment 반대축
- 특별한 제한 사항이 없으면 Row위젯과 Column위젯의 주축은 최대 크기를 차지하고 반대축은 최소 크기를 차지한다.

#### MainAxisAlignment
MainAxisAlignment의 옵션들 (암기)
- MainAxisAlignment.start: 주축의 시작에 정렬한다.
- MainAxisAlignment.end: 주축의 끝에 정렬한다.
- MainAxisAlignment.center: 주축의 중앙에 정렬한다.
- MainAxisAlignment.spaceVBetween:주축에서 위젯들 **사이에** 동일한 간격을 두고 정렬한다.
- MainAxisAlignment.spaceAround: 주축에서 위젯들 **주변에** 동일한 간격을 두고 정렬한다.
	- 서로 양쪽 끝에 1만큼의 공간이 생긴다면, 위젯들 사이에는 2개만큼의 공간이 생긴다.
		- 위젯들 주변에 동일한 간격을 두고 정렬했기 때문에 자식 위젯 서로 사이에 1씩 각각 공간을 뒀기 때문. 따라서 위젯 사이에는 2만큼의 공간이 생기고 위젯과 끝 사아이에는 1만큼의 공간이 생긴다.
- MainAxisAlignment.SpaceEvenly: 주축에서 위젯들 **앞뒤 및 사이에** 동일한 간격을 두고 정렬한다.
	- 1만큼의 공간이 모든 공간사이에 적용을 받는다.


#### CrossAxisAlignment
CrossAxisAlignment의 옵션들 (암기)
- CrossAxisAlignment.start: 반대축의 시작에 정렬한다.
- CrossAxisAlignment.end: 반대축의 끝에 정렬한다.
- CrossAxisAlignment. cemter: 반대축의 주앙에 정렬한다.
- CrossAxisAlignment.stretch: 반대축으로 위젯들을 최대로 확장한다.
- CrossAxisAlignment.baseline: 텍스트 기준선을 기중으로 위젯을 정렬한다.
	- TextBaseline.alphabetic: 
		- 글자 밑 부분으르 포함하지 않은 채 베이스라인이 생긴다.
	- TextBaseline.ideographic: 
		- 글자 밑 부분을 포함한 채 베이스라인이 생긴다.
		- 중국어의 경우 글 자 끝에 베이스라인이 닿는다.
		- 거의 쓰지 않는다.



### 프로젝트 초기화


```Dart
import 'package:flutter/material.dart';  
  
class HomeScreen extends StatelessWidget {  
  const HomeScreen({super.key});  
  
  @override  
  Widget build(BuildContext context) {  
    return const Placeholder();  
  }  
}
```

```Dart
import 'package:flutter/material.dart';  
import 'package:row_and_column/screen/home_screen.dart';  
  
void main() {  
  runApp(  
    MaterialApp(  
      home: HomeScreen(),  
    )  
  );

```
1. 정석인 방법
	- im을 입력하면 import 자동 완성 - tab
	- mat을 입력하면 material.dart 자동 완성 tab
	- stless 입력하면 stateless Widget  자동완성 - 클래스 생성
	- 이름은 HomeScreen이라 작성

2. 더 간단한 방법
	-  HomeScreen 우클릭해서 Show Context Actions - import 자동 완성

 <정리> 코드를 초기화 하라
 1. main 함수를 제외한 main dart에 있는 모든 코드 삭제
 2. runApp 안에 MaterialApp위젯을 넣은 후
 3. home: HomeScreen이라는 위젯을 만들고
 4. screen 폴더 안에  home_screen.dart라는 파일을 만든 다음
 5. HomeScreen 클래스를 생성해두면 된다.


### Row & Column

- MaterialApp - Scaffold
- Container
	- 다른 위젯을 담는 위젯, 다른 위젯을 감싸는 박스 같은 위젯이다.
	- 모양이나 테두리를 만들거나 배경 색상을 넣거나 크기를 조절하는 등 다양한 작업이 가능하다.
	- Column위젯의 크기 얼만큼 차지하고 있는 지 확인을 위해 사용 가능하다.
- Safe Area: 상태바 등을 제외한 공간만 사용할 수 있도록 해주는 위젯 (상하 모두)
- DRY - Do not Repeat Yourself (반복되는 코드를 작성하지 말 것).
```Dart
// DRY - Do not Repeat Yourself

Container(
  height: 50.0,  
  width: 50.0,  
  color: Colors.red,  
),  
Container(  
  height: 50.0,  
  width: 50.0,  
  color: Colors.orange,  
),  
Container(  
  height: 50.0,  
  width: 50.0,  
  color: Colors.yellow,  
),
Container(  
  height: 50.0,  
  width: 50.0,  
  color: Colors.green,  
),
```

```Dart
children: colors.map(  
  (e) => Container(  
    height: 50.0,  
    width: 50.0,  
   color: e,  
  ),).toList(),
```

- Map: 리스트에 있는 값들을 하나씩 순회하면서 각 색깔을 갖고 있는 컨테이너를 추출한다.
- Map - toList 실행

- Column위젯이 차지하고 있는 크기 확인하기
```Dart
child: Container(  
  color: Colors.black,  
  child: Column(  
    children: colors.map(  
      (e) => Container(  
        height: 50.0,  
        width: 50.0,  
       color: e,  
      ),    ).toList(),  
  ),),
```
### Column MainAxisAlignment

`mainAxisAlignment: MainAxisAlignment,`
- 왼: 파라미터 (매개변수)
- 오: 값
- 기본값: MainAxisAlignment.start
### Row MainAxisAlignment

- Row 와 Column은 주축과 반대축이 반대일 뿐 모든 파라미터를 같이 공유한다. 

### Column MainAxisSize

- 기본값: MainAxisSize.max
- MainAxisSize.min: 필요한 공간만 칼럼이 차지한다.
### Row MainAxisSize

- Row 와 Column은 주축과 반대축이 반대일 뿐 모든 파라미터를 같이 공유한다. 

### Column CrossAxisAlignment

```Dart
child: Container(  
  color: Colors.black,  
  width: double.infinity,
  child: Column(
```
- 기본값: CrossAxisAlignment.center (가운데 정렬)
- CrossAxisAlignment.stretch (차지할 수 있는 최대 크기만)
### Row CrossAxisAlignment

```Dart
child: Container(  
  color: Colors.black,  
  height: double.infinity,  
  child: Row(
```

### Expanded Widget

- column안에서 남는 공간을 최대한 차지
- 여러개 사용 시 expanded Widget들이 공간을 똑같은 비율로 나눠갖게 된다.
- flex: 공간을 차지하게 되는 비율 결정 (기본값 1)

### Flexible Widget

`class Expanded extends Flexible`

- Expanded 위젯은 Flexible 위젯을 상속받고 있다.
		정의된 곳으로 이동: Control + B

`fit: FlexFit.tight`
- Flexible Widget이 차지할 수 있는 크기와 똑같이 차지한다.
	- Expeanded와 같은 결과를 도출할 수 있다.
	- 즉, **Expanded Widget은 Flexible Widget에 Fit 파라미터를 flexfit.tight 옵션을 지정해주는 것과 동일**하다.
`fit: FlexFit.loose,`
- Flexible Widget이 배정된 만큼의 공간을 차지하지만 나머지  Expended 자식 위젯들이 남는 공간을 가져가지 못한다.
- Flexible Widget의 자식 위젯은 배정된 사이즈만 차지하게 된다.
- Fit 파라미터를 조절함으로써 Flexible Widget이 차지하는 크기만큼 내부(자식)위젯이 차지가능 여부를 결정할 수 있다.

```Dart

import 'package:flutter/material.dart';  
import 'package:row_and_column/const/colors.dart';  
  
class HomeScreen extends StatelessWidget {  
  const HomeScreen({super.key});  
  
  @override  
  Widget build(BuildContext context) {  
    return Scaffold(  
        body: SafeArea(  
          child: Container(  
            color: Colors.black,  
            height: double.infinity,  
            child: Column(  
              children: [  
                Flexible(  
                  flex: 2,  
                  fit: FlexFit.loose,  
                  child: Container(  
                    height: 50.0,  
                    width: 50.0,  
                    color: Colors.red,  
                  ),  
                ),  
                Expanded(  
                  flex: 3,  
                  child: Container(  
                    height: 50.0,  
                    width: 50.0,  
                    color: Colors.orange,  
                  ),  
                ),  
                Expanded(  
                  child: Container(  
                    height: 50.0,  
                    width: 50.0,  
                    color: Colors.yellow,  
                  ),  
                ),  
              ]  
            ),  
          ),  
        ),  
      );  
  }  
}
```

### Challenge

### Challenge 해답

```Dart
import 'package:flutter/material.dart';  
import 'package:row_and_column/const/colors.dart';  
  
class HomeScreen extends StatelessWidget {  
  const HomeScreen({super.key});  
  
  @override  
  Widget build(BuildContext context) {  
    return Scaffold(  
      body: SafeArea(  
        child: Column(  
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,  
          children: [  
            Row(  
              mainAxisAlignment: MainAxisAlignment.spaceAround,  
              children: colors  
                  .map(  
                    (e) => Container(  
                      height: 50.0,  
                      width: 50.0,  
                      color: e,  
                    ),  
                  )  
                  .toList(),  
            ),  
            Row(  
              mainAxisAlignment: MainAxisAlignment.center,  
              children: [  
                Container(  
                  height: 50.0,  
                  width: 50.0,  
                  color: Colors.orange,  
                )  
              ]  
            ),  
            Row(  
              mainAxisAlignment: MainAxisAlignment.end,  
              children: colors  
                  .map(  
                    (e) => Container(  
                  height: 50.0,  
                  width: 50.0,  
                  color: e,  
                ),  
              )  
                  .toList(),  
            ),  
            Row(  
                mainAxisAlignment: MainAxisAlignment.center,  
                children: [  
                  Container(  
                    height: 50.0,  
                    width: 50.0,  
                    color: Colors.green,  
                  )  
                ]  
            ),  
          ],  
        ),  
      ),  
    );  
  }  
}
```






