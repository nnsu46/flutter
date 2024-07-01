## Async Programming

# Future

- 미래에 받아올 값으로, 지금까지 배운 모든 타입에 적용 가능하다.

```Dart
void main() {
  Future<String> name = Future.value("코드팩토리");
  Future<int> number = Future.value(1);
  Future<bool> isTrue = Future.value(true);

  print("함수 시작");

  Future.delayed(Duration(seconds: 2), () {
    print("딜레이 끝");
  });
}
```

 - `delayed()` 함수는 두 개의 파라미터를 받는다.
	 - 지연할 시간
	 - 지연 시간이 지난 후 실행 할 함수

# Await

- 파라미터() 와 바디 {} 사이에 `async`를 넣어준다.
	- `await` 키워드는 반드시 `astnc` 함수 내에서 사용한다.
- 비동기 함수 내에서 특정 작업이 선행되어 완료될 때까지 기다린다.
- CPU는 `await`로 인해 대기하는 동안 다른 작업을 수행할 수 있다.

```Dart
void main() async {
  Future<String> name = Future.value("코드팩토리");
  Future<int> number = Future.value(1);
  Future<bool> isTrue = Future.value(true);

  await addNumbers(1, 1);
  await addNumbers(2, 2);
}

Future<void> addNumbers(int number1, int number2) async {
  print("계산시작: $number1 + $number2");

  await Future.delayed(Duration(seconds: 2), () {
    print("계산 완료: $number1 + $number2 = ${number1 + number2}");
  });

  print("함수완료");
}
```

```text
계산시작: 1 + 1
계산 완료: 1 + 1 = 2
함수완료
계산시작: 2 + 2
계산 완료: 2 + 2 = 4
함수완료
```

- `main` 함수 내에서 `addNumbers` 함수를 순차적으로 실행하려면, `main`도 `async`로 선언하고 `addNumbers` 호출 시 `await`를 사용한다.
- `await`는 `Future`를 반환해야 하므로, `void` 반환 함수는 `Future<void>`로 변경해야 한다.

# Returning Future

```Dart
void main() async {
  Future<String> name = Future.value("코드팩토리");
  Future<int> number = Future.value(1);
  Future<bool> isTrue = Future.value(true);

  final result1 = await addNumbers(1, 1);
  final result2 = await addNumbers(2, 2);
  
  print("result1 : $result1");
  print("result2 : $result2");
  print("result1 + result2 = ${result1+result2}");
}

Future<int> addNumbers(int number1, int number2) async {
  print("계산시작: $number1 + $number2");

  await Future.delayed(Duration(seconds: 2), () {
    print("계산 완료: $number1 + $number2 = ${number1 + number2}");
  });

  print("함수완료");
  
  return number1 + number2;
}
```

```text
계산시작: 1 + 1
계산 완료: 1 + 1 = 2
함수완료
계산시작: 2 + 2
계산 완료: 2 + 2 = 4
함수완료
result1 : 2
result2 : 4
result1 + result2 = 6
```

- int형으로 사용할 경우
	- int로 만들어주고 return해주면 된다.
	- future가 알아서 future로 감싸서 return해준다.

# Stream 기본기

- Dart에서 `StreamController`는 기본적으로 제공하는 기능이 아니다.
	- `dart:async` 라이브러리를 임포트해야 한다.
- `StreamController()`를 생성하면 연결된 스트림에 접근할 수 있다.
- 생성된 스트림에 리스너를 추가하고, `add` 메소드를 통해 리스너에게 값을 전달할 수 있다.
	- 여러 개의 값을 전달할 수도 있다.

```Dart
import "dart:async";

void main() {
  final controller = StreamController();
  final stream = controller.stream.asBroadcastStream();

  final streamListener1 = stream.listen((val) {
    print("Listener 1 : $val");
  });
  
  final streamListener2 = stream.listen((val) {
    print("Listener 2 : $val");
  });

  controller.sink.add(1);
  controller.sink.add(2);
  controller.sink.add(3);
  controller.sink.add(4);
  controller.sink.add(5);
}
```

```text
Listener 1 : 1
Listener 2 : 1
Listener 1 : 2
Listener 2 : 2
Listener 1 : 3
Listener 2 : 3
Listener 1 : 4
Listener 2 : 4
Listener 1 : 5
Listener 2 : 5
```

- Dart에서 스트림은 기본적으로 한 번 리스닝 할 리소스가 생긴다.
- 여러 리스너에서 동시에 리스닝하려면 스트림을 브로드캐스트 스트림으로 변환해야 한다.
- `.asBroadcastStream()` 메서드를 사용하여 스트림을 여러 번 리스닝할 수 있다.

```Dart
import "dart:async";

void main() {
  final controller = StreamController();
  final stream = controller.stream.asBroadcastStream();

  final streamListener1 = stream.where((val) => val % 2 == 0).listen((val) {
    print("Listener 1 : $val");
  });

  final streamListener2 = stream.where((val) => val % 2 == 1).listen((val) {
    print("Listener 2 : $val");
  });

  controller.sink.add(1);
  controller.sink.add(2);
  controller.sink.add(3);
  controller.sink.add(4);
  controller.sink.add(5);
}
```

```text
Listener 2 : 1
Listener 1 : 2
Listener 2 : 3
Listener 1 : 4
Listener 2 : 5
```

- 스트림의 `.where()` 메소드를 사용하면 주어진 조건에 따라 스트림의 요소를 변경할 수 있다.
	- 조건을 만족하는 요소만을 포함하는 새로운 스트림을 생성한다.


# Stream 함수

```Dart
import "dart:async";

void main() {
  calculate(2).listen((val){
    print("calculate(2) : $val");
  });
}

Stream<int> calculate(int number) async* {
  for(int i = 0; i < 5; i++) {
    yield i * number;
  }
}
```

```text
<결과>
calculate(2) : 0
calculate(2) : 2
calculate(2) : 4
calculate(2) : 6
calculate(2) : 8
```

- 일반 함수는 `return`을 만나면 해당 값을 반환하고 실행이 종료된다.
- `Stream` 함수는 이러한 한계를 해결할 수 있다.
- 함수의 반환 타입을 `Stream<>`으로 지정하고, 파라미터와 바디 사이에 `async*`을 넣는다.
- 함수에서는 `return` 대신 `yield`를 사용하여 값을 하나씩 반환할 수 있다.

# Stream에서의 async 프로그래밍

```Dart
import "dart:async";

void main() {
  calculate(2).listen((val){
    print("calculate(2) : $val");
  });
  
  calculate(4).listen((val){
    print("calculate(4) : $val");
  });
}

Stream<int> calculate(int number) async* {
  for(int i = 0; i < 5; i++) {
    yield i * number;
  }
  
  await Future.delayed(Duration(seconds : 1));
}
```

```text
<결과>
calculate(2) : 0
calculate(4) : 0
calculate(2) : 2
calculate(4) : 4
calculate(2) : 4
calculate(4) : 8
calculate(2) : 6
calculate(4) : 12
calculate(2) : 8
calculate(4) : 16
```

- `async*`: 선언된 함수 내에서도 `await`와 같은 비동기 연산자를 사용할 수 있다.
- `await`를 사용하는 동안 CPU는 대기 상태가 아니라 다른 작업을 계속 처리한다.
	- 비동기 프로그래밍에서 CPU 리소스를 효율적으로 활용하는 방법이다.

# Yield*

```Dart
mport "dart:async";

void main() {
  playAllStream().listen((val){
    print(val);
  });
}

Stream<int> playAllStream() async* {
  yield* calculate(1);
  yield* calculate(1000);
}

Stream<int> calculate(int number) async* {
  for(int i = 0; i < 5; i++) {
    yield i * number;
  }
  
  await Future.delayed(Duration(seconds : 1));
}
```

```text
0
1
2
3
4
0
1000
2000
3000
4000
```

- 스트림 내에서 특정 작업(`calculate2`)이 완료된 후 다른 작업(`calculate4`)을 시작하려면  스트림을 'await'할 방법이 필요하다.
- `yield`: 값을 하나씩 차례대로 스트림으로 전달한다.
- `yield*`: 연결된 스트림의 모든 값을 가져올 때까지 기다린다.
	- 해당 스트림이 완전히 끝나야 다음 스트림이 실행된다.
