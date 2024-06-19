## Padding

- 프로젝트 세팅하기
- EdgeInsets.all 생성자
- EdgeInsets.symmetric 생성자
- sets.only 생성자
- EdgeInsets.fromLTRB 생성자

### 프로젝트 세팅하기

```Dart
return Scaffold(  
  body: Center(  
    child: Container(  
      color: Colors.red,  
      child: Container(  
        color: Colors.blue,  
        width: 50.0,  
        height: 50.0,  
      ),    )  ));
```

- 빨간색 컨테이너는 크기를 설정하지 않아 내부(자식)위젯과 같은 크기를 차지하고 있기 때문에 보이지 않는다. 실제로 존재는 한다.

### EdgeInsets.all 생성자

```Dart
return Scaffold(  
  body: Center(  
    child: Container(  
      color: Colors.red,  
      child: Padding(  
        padding: const EdgeInsets.all(8.0),  
        child: Container(  
          color: Colors.blue,  
          width: 50.0,  
          height: 50.0,  
        ),      ),    )  ));
```
- Container - Show Context Actions - Wrap with Padding
- 파란색 컨테이너 주변에 빨간색 컨테이너가 8픽셀만큼 보이게 된다.
- 즉, Edgekbsets.all을 사용하면 4개의 면에 똑같은 여백을 추가할 수 있다.

### EdgeInsets.symmetric 생성자

- Symmetric은 Named 파라미터 두 개를 입력할 수 있다.
- 좌우, 상하 대칭으로 따로 지정이 가능하다.
- horizontal: 좌우
- vertical: 상하

### sets.only 생성자

- 4개의 면에 모두 직접 여백을 지정할 수 있다.
- 입력은 선택할 수 있다. (안 하면 0을 입력한 것과 동일)
- Named  parameter
- top / left / right / bottom

### EdgeInsets.fromLTRB 생성자

- LTRB: left, top, right, bottom
- only와 마찬가지로 모든 여백을 직접 지정할 수 있다.
- 값 입력은 필수이다.
