## widgetTree

- 플러터에서 위젯 트리는  UI를 렌더링(화면에 그리는)하는 데 사용되는 계층 구조를 의미.
- 트리: 나무처럼 위젯을 배치한다.

- 예시
```Dart
MaterialApp(  
  debugShowCheckedModeBanner: false,  
  home: Scaffold(  
    backgroundColor: Colors.black,  
    body: Center(  
      child: Text(  
        'Hello World',  
        style: TextStyle(  
          color: Colors.white,
```
	  MateriaApp
	  Scaffold
	  Center
	  Text
  
- 위에서부터 아래로 계층 구조
- 위에는 부모 위젯
- 아래는 자식 위젯 (여러 개의 자식 위젯을 가질 수 있음)
