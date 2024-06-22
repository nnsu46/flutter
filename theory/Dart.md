
# 변수 선언하기

```Dart
void main() {
  var name = "코드 팩토리";
  print(name);
}
```

```text
코드 팩토리
```

- Var 
	- 오른쪽 값으로 유형을 유추한다.
		- Ex) 문자: String / 정수: int
	- 변수가 실행되는 순간 어떤 타입인지 정해진다.
	- 정해진 타입은 고정되고 다른 형태로 바꿀 수 없다.
	- var이라는 타입 자체가 존재하는 건 아니다.
	- 되도록 정확한 타입(String, int ···)을 명시해주는 게 좋다.

# 변수 타입

- Integer (int) 정수
- Double (double)  실수
- Boolean (bool) 참거짓
- String (str) 문자열
	- S 대문자로 써야한다.
	- 덧셈 가능하다. 
		- 뺄셈, 나눗셈은 안 된다.
	- ${ }에 변수를 넣을 수 있다.
	- 괄호가 없어도 되지만, 괄호 안에 넣어야 실제 변수로 인식한다.
- Dynamic
	- var과 동일하게 변수의 형태가 미리 정해지지 않는다. 
	- var과는 달리 변수 형태 변경이 자유롭다.

# Nullable vs Non-nullable

- nullabel: null이 될 수 있다.
- non-nullable: null이 될 수 없다.
- null: 값이 존재하지 않는다.

```dart
void main() {
  String name = "코드팩토리";
  print(name);
  
  String? name2 = "블랙핑크";
  name2 = null;
  print(name2);
}
```

```text
코드팩토리
null
```

- 변수 뒤에 '?'을 넣으면 해당 변수는 null을 넣을 수 있다.
	- 기본적으로 변수에 null을 사용할 수 없지만 '?'을 붙이면 사용할 수 있다.

```Dart
void main() {
  String? name2 = "블랙핑크";
  print(name2!);
}
```

-  null이 들어갈 수 있는 변수에 '!'을 넣으면 'null로 사용되고 있지 않다'를 의미한다.

# Final vs Const

- final과 const로 선언하면 이후 변수의 값을 변경할 수 없다.
- final과 const는 변수 타입 선언을 생략 수 있다.
	- final과 const가 var기능을 한다.
### 'DateTime', final와 const 차이

```Dart
DateTime now = DateTime.now(); 
print(now);
```

- 현재 시간을 변수에 저장 할 수 있다. 
- 나오는 시간은 실행 버튼을 누르는 순간이 아닌 코드가 실행되는 순간이다.
	- 그렇기 때문에 코드를 다른데 붙여 쓰면 차이가 존재한다.

```Dart
void main() {
  final DateTime now = DateTime.now();
  const DateTime now = DateTime.now(); // 오류 발생
}
```

- const는 빌드타입의 값을 알고 있어야 하고, final은 알고 있지 않아도 된다.
# Operators 연산자

```Dart
void main() {
  int number = 2;
  
  print(number);
  print(number +2);
  print(number -2);
  print(number *2);
  print(number /2);
  
  print('--------------------');
  print(number %2);
  print(number %3);
}
```

```text
2
4
0
4
1
--------------------
0
2
```

-  `'+', '-', '*', */*, '%'`
	- 변수값을 재저장 하지 않는다.


```Dart
void main() {
  int number = 2;
  
  number ++;
  print(number); 
  
  number --;
  print(number); 
}
```

```text
3
2
```

```Dart
dobule numver = 4.0;

number += 1;
print(number) 

number -= 1;
print(number) 

number *= 2;
print(number) 

number /= 2;
print(number);
```

```text
5
4
8
4
```

- `'++', '--', '+=', '-='. '*=', '/='`
	- 변수값을 재저장한다.

```Dart
void main() {
  //null
  double? number = 4.0;
  
  print(number);
  
  number = 2.0;
  
  print(number);
  
  number = null;
  print(number);
  
  number ??= 3.0;
  print(number);

```

```text
4
2
null
3
```

- `number ?? = n`
	- number가 null이면 오른쪽 값으로 변경한다.

```Dart
void main() {
  int number1 = 1;
  int number2 = 2;
  
  print(number1 > number2);
  print(number1 < number2);
  print(number1 >= number2);
  print(number1 <= number2);
  print(number1 == number2); 
  print(number1 != number2); 
}
```

```text
false
true
false
true
false
true
```

- `'>', '<', '>=', '<=', '==', '!='`
	- 변수 크기를 비교한다.

```Dart
void main() {
  int number1 = 1;
  print(number1 is int);
  print(number1 is! double);
}
```

```text
true
false
```

- `'is' 'is!'`
	- 변수 타입을 비교한다.

```Dart
void main() {
  bool result1 = 12 > 10 && 1 > 0;
  print(result1);

  bool result2 = 12 > 10 && 0 > 1;
  print(result2);

  bool result3 = 12 > 10 || 1 > 0;
  print(result3);

  bool result4 = 12 > 10 || 0 > 1;
  print(result4);

  bool result5 = 12 < 10 || 0 > 1;
  print(result5);
}
```

```text
true
false
true
true
false
```

- And 조건: `%%`
- Or 조건: `||`
# List

```Dart
void main() {
List<stromg> blackPink = ['제니', '지수', '로제',' 리사'];
print(blackPink.length);

blackPink.add('코드팩토리');

print(balckPink);
print.remove('코드팩토리');
prinkt(blackPink);
print(blackPink.indexOf(('로제'));
}
```

```text
4
[제니, 지수, 로제,  리사, 코드팩토리]
[제니, 지수, 로제,  리사]
2
```

- 중복값을 가질 수 있다.
- '< >' 를 통해 타입을 설정 가능하다.
- 인덱스는 0부터 시작한다.
- `변수명.length` 길이를 알 수 있다.
- `변수명.add(값)` 값을 추가한다.
- `변수명.remove(값);` 값을 제거한다.
- `변수명.indexOf(값)` 값의 위치를 알려준다.
# Map

```Dart
void main() {
  Map<String, String> dictionary = {
    'Harry Potter': '해리포터',
    'Ron Weasley': '론 위즐리',
    'Hermione Granger': '헤르미온느 그레인저',
  };
  print(dictionary);

  Map<String, bool> isHarryPotter = {
    'Harry Potter': true,
    'Ron Weasley': true,
    'Ironman': false,
  };
  print(isHarryPotter);
}
```

```text
{Harry Potter: 해리포터, Ron Weasley: 론 위즐리, Hermione Granger: 헤르미온느 그레인저}
{Harry Potter: true, Ron Weasley: true, Ironman: false}
```

- key, value  형식을 지정해주어야 한다.
- addAll로 괄호 안의 값을 한 번에 추가할 수 있다.
- `[새로운 key 값] = 새로운 value`
	- 하나만 넣을 시 이렇게 넣어도 된다.
 - key를 통해서 value 찾을 수 있다.
	 - value를 통해서는 찾을 수 없다.

```dart
  Map<String, String> dictonary = {
    "해리포터" : "해리해리",
    "론 위즐리" : "론론",
    "헤르미온느" : "헤르헤르",
  };
  print(dictonary);
  
  dictonary["론 위즐리"] = "위즐위즐";
  print(dictonary);
}
```

```text
<결과>
{해리포터: 해리해리, 론 위즐리: 론론, 헤르미온느: 헤르헤르}
{해리포터: 해리해리, 론 위즐리: 위즐위즐, 헤르미온느: 헤르헤르}
```

- key를 통해서 값을 바꿀 수 있다.

```Dart
void main() {
  Map<String, String> dictonary = {
    "해리포터" : "해리해리",
    "론 위즐리" : "론론",
    "헤르미온느" : "헤르헤르",
  };
  print(dictonary);
  
  dictonary.remove("론 위즐리");
  print(dictonary);
}
```

```text
<결과>
{해리포터: 해리해리, 론 위즐리: 론론, 헤르미온느: 헤르헤르}
{해리포터: 해리해리, 헤르미온느: 헤르헤르}
```

- `remove`를 통해 해당 key와 value를 지울 수 있다.

```Dart
void main() {
  Map<String, String> dictonary = {
    "해리포터" : "해리해리",
    "론 위즐리" : "론론",
    "헤르미온느" : "헤르헤르",
  };
  
  print(dictonary.keys);
  print(dictonary.values);
}
```

```text
(해리포터, 론 위즐리, 헤르미온느)
(해리해리, 론론, 헤르헤르)
```
- key와 value값만 가져올 수 있다.

# Set

- 중복값이 들어갈 수 없다.
- 기본적인 함수는 List와 거의 동일하다.
	- index를 통해 값을 찾는 것은 불가능하다.

# If 문

- 다른 프로그래밍 언어의 if문과 동일하다.
### Switch 

- break를 넣어야 다음 명령이 실행되지 않는다.
- default 필수이다.
	- if문에서의 else같은 역할.

# Loops

### for 문

- for (초기식 ; 조건식 ; 증감식) {출력} 

```Dart
void main() {
  List<int> numbers = [1,2,3,4,5];
  
  for(int number in numbers){
    print(number);
  }
}
```

```text
1
2
3
4
5
```

- for (변수타입 변수 in 리스트)  리스트 안의 값들을 반복 시킬 수 있다.

- While 
	- 무한 반복하지 않도록 조건 설정에 주의해야 한다.
- do while 문
	- while문과 동작 순서가 다르다.
	- 거의 사용하지 않는다.
- Break
	- loop 종료
 - Continue
	 - 해당 loop만 넘기고 계속 진행된다.

# Enum

- 정확히 해당 값만 사용하겠다는 걸 알려줄 수 있다.
- 오타나 실수할 경우 빠르게 한정된 값을 이용하도록 강제할 수 있다.
\
```Dart
enum Status {
  approved,
  pending,
  rejected,
}

void main() {
  Status status = Status.approved;

  if (status == Status.approved) {
    print("승인입니다.");
  } else if (status == Status.pending) {
    print("대기입니다.");
  } else {
    print("거절입니다.");
  }
}
```

```text
승인입니다.
```

# 함수

- 함수가 어떤 역할을 할 건지 주석을 달아놓고 작성하는 게 좋다.
- 함수를 정의할 때는 가장 먼저 이름을 정한다.
	- `함수명()`
- main 함수는 자동으로 실행이 되는 함수이다.
	- 다른 함수들은 메인 함수 안에 실행을 해줘야 한다
- parameter : 매개변수
- positional parameter: 순서가 중요한 파라미터
- optional parameter: 있어도 되고 없어도 되는 파라미터
	- 사용하지 않는 파라미터는 `[]` 대괄호 안에 넣으면 된다.
```Dart
void main() {
  addNumber(30);
}

addNumber(int x, [int y, int z]) { // 오류 발생생
  int sum = x + y + z;
}
```

- int y와 z가 optional parameter로 지정되고 값이 없는, 즉 null이 된다.
	- int?을 사용하면 null을 사용할 수 있지만 null끼리 더할 수 없기 때문에 오류가 또 발생한다.

```Dart
void main() {
  addNumber(30);
}

addNumber(int x, [int y = 30, int z = 40]) {
  int sum = x + y + z;
}
```

- 해결 방법
	- y, z에 기본값을 넣어준다. (기본값 선언)
		- x는 무조건 값을 넣어줘야 실행되기 때문에 기본값을 넣을 필요 없다.

```DArt
void main() {
  addNumber(30,40,50);
}

addNumber(int x, [int y = 30, int z = 40]) {
  int sum = x + y + z;
}
```

```text
x : 10
y : 50
z : 60
짝수입니다.
x : 20
y : 90
z : 100
짝수입니다.
```

- 값이 입력되면 기본값은 무시된다.

```dart
void main() {
  addNumber(x:10, y:20, z:30);
  addNumber(y:20, x:10, z:30);
}

addNumber({
  required int x,
  required int y,
  required int z,
}) {
  int sum = x + y + z;
}
```

- named parameter : 이름이 있는 파라미터
	- required를 사용하여 이름을 직접 선언하기 때문에 순서가 중요하지 않다.

```Dart
void main() {
  addNumber(x:10, y:20,);
  addNumber(y:20, x:10, z:30);
}

addNumber({
  required int x,
  required int y,
  int z = 30,
}) {
  int sum = x + y + z;
}
```

- required를 없애고 기본값을 설정하면 optional parameter로 사용할 수 있다.

```Dart
void main() {
  addNumber(10, y:20,);
  addNumber(10, y:20, z:30);
}

addNumber(int x,{
  required int y,
  int z = 30,
}) {
  int sum = x + y + z;
}
```

- positional parameter
- optional parameter
- named parameter

```Dart
void main() {
  addNumber(10, y:20,);
  addNumber(10, y:20, z:30);
}

int addNumber(int x,{
  required int y,
  int z = 30,
}) => x + y + z;
```

- arrow function 화살표 함수
# Typedef

- 함수를 편리하게 사용할 수 있는 기능 중 하나이다.

```Dart
void main() {
  Operation operation = add;
  int result = operation(10, 20, 30);
  print(result);

  operation = subtract;
  int result2 = operation(10, 20, 30);
  print(result2);
}

typedef Operation = int Function(int x, int y, int z);

int add(int x, int y, int z) => x + y + z;
int subtract(int x, int y, int z) => x - y - z;
```

```text
60
-40
```

- typedef와 사용되는 파라미터 변수가 동일해야 한다.

```Dart
void main() {
  int result = calculate(30,40,50, add);
  print(result);

  int result2 = calculate(40,50,60, subtract);
  print(result2);
}

typedef Operation = int Function(int x, int y, int z);
int add(int x, int y, int z) => x + y + z;
int subtract(int x, int y, int z) => x - y - z;

int calculate(int x, int y, int z,Operation operation) {
  return operation(x,y,z);
}
```

```text
120
-70
```

- `int calculate(int x, int y, int z,Operation operation) { return operation(x,y,z); }`
	주로 이 형태로 사용을 많이 한다.
