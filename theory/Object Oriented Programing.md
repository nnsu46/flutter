
# Constructor 생성자

```Dart
void main() {
  Idol blackPink = Idol();

  print(blackPink.name);
  print(blackPink.members);
  blackPink.sayHello();
  blackPink.introduce();
}
class Idol {
  String name = '블랙핑크';
  List<String> members = ['지수', '제니', '리사', '로제'];

  void sayHello() {
    print('안녕하세요 블랙핑크입니다.');
  }

  void introduce() {
    print('저희 멤버는 지수, 제니, 리사, 로제가 있습니다.');
  }
}
```

```text
블랙핑크
[지수, 제니, 리사, 로제]
안녕하세요 블랙핑크입니다.
저희 멤버는 지수, 제니, 리사, 로제가 있습니다.
```

- void
	- 아무것도 return 하지 않는다.
- Class vs Instance
	- Class: 설계서를 정의한다.
	- Instance: 설계서를 바탕으로 무한하게 실체를 만들 수 있다.

```Dart
void main() {

  Idol bts = Idol(
  'BTS',
  ['RM', '진', '슈가', '제이홉', '지민', '뷔', '정국'],
  );

  print(bts.name);
  print(bts.members);
  bts.sayHello();
  bts.introduce();
}
class Idol {
  String name;
  List<String> members;
  
  Idol(String name, List<String> members)
      : this.name = name,
        this.members = members;

  void sayHello() {
    print('안녕하세요 ${this.name}입니다.');
  }

  void introduce() {
    print('저희 멤버는 ${this.members}가 있습니다.');
  }
}
```

```text
BTS
[RM, 진, 슈가, 제이홉, 지민, 뷔, 정국]
안녕하세요 BTS입니다.
저희 멤버는 [RM, 진, 슈가, 제이홉, 지민, 뷔, 정국]가 있습니다.
```

- this: 현재 위치하는 클래스를 의미한다.

```Dart
Idol(String name, List<String> members)
   : this.name = name,
     this.members = members;
```

```Dart
Idol(this.name, this.members);
```

- 이처럼 더 간결하게 만들 수 있다.

```Dart
void main() {

  Idol bts = Idol.fromList(
    [
      ['RM', '진', '슈가', '제이홉', '지민', '뷔', '정국'],
      'BTS',
    ]
  );

  print(bts.name);
  print(bts.members);
  bts.sayHello();
  bts.introduce();
}
class Idol {
  String name;
  List<String> members;

  Idol(this.name, this.members);

  Idol.fromList(List values)
      : this.members = values[0],
        this.name = values[1];

  void sayHello() {
    print('안녕하세요 ${this.name}입니다.');
  }

  void introduce() {
    print('저희 멤버는 ${this.members}가 있습니다.');
  }
}
```

- 실행 결과는 동일하다.
	- 클래스 선언 할 때 Constructor을 갖고서 외부에서 파라미터를 받을 수도 있고,
	- Named Constructor을 통해서 파라미터를 받을 수도 있다.


```Dart
void main() {
  Idol blackPink = const Idol(
    '블랙핑크',
    ['지수', '제니', '리사', '로제'],
  );

  print(blackPink.name);
  print(blackPink.members);
  blackPink.sayHello();
  blackPink.introduce();

  Idol bts = Idol.fromList([
    ['RM', '진', '슈가', '제이홉', '지민', '뷔', '정국'],
    'BTS',
  ]);

  print(bts.name);
  print(bts.members);
  bts.sayHello();
  bts.introduce();
}
class Idol {
  final String name;
  final List<String> members;

  const Idol(this.name, this.members);

  Idol.fromList(List values)
      : this.members = values[0],
        this.name = values[1];

  void sayHello() {
    print('안녕하세요 ${this.name}입니다.');
  }

  void introduce() {
    print('저희 멤버는 ${this.members}가 있습니다.');
  }
}
```

- Immutable 프로그래밍
	- 값을 선언하고 나면 변경할 수 없는 형식으로 코딩을 많이 한다.
- ` blackPink.name = '코드팩토리';`
	- 이걸 넣으면 내용을 바꿀 수 있는데 `final` 을 사용해서 값을 바꿀 수 없도록 한다.
		- `final`로 선언하지 못하는 소수의 상황들을 제외하고는 거의 대부분의 상황에서는 클래스의 변수를 `final`로 선언하는 습관을 만드는 것이 좋다.
			- 그래야 버그를 좀 더 방지할 수 있다.
- constructor 앞에 `const`를 쓰면 const constructor를 간단하게 만들 수 있다.
	- `const` 또한 한 번 선언하고 나면 값을 바꿀 수 없다.

```Dart
void main() {
  Idol blackPink = Idol(
    '블랙핑크',
    ['지수', '제니', '리사', '로제'],
  );

  Idol blackPink2 = Idol(
    '블랙핑크',
    ['지수', '제니', '리사', '로제'],
  );
```

- `print(blackPink == blackPink2)` 
	- `false` 컴퓨터는 BlackPink 와 BlackPink2를 다르다고 인식한다.
- 그러나 둘 다 const로 선언하고, 값 또한 모두 같을 경우에는 `true`가 나온다.

# Getter and Setter

- Getter: 데이터를 가져올 때
- Setter: 데이터를 설정할 때

```Dart
void main() {
  Idol blackPink = Idol(
    '블랙핑크',
    ['지수', '제니', '리사', '로제'],
  );

  Idol bts = Idol.fromList([
    ['RM', '진', '슈가', '제이홉', '지민', '뷔', '정국'],
    'BTS',
  ]);

  print(blackPink.firstMember);
  print(bts.firstMember);
  
  blackPink.firstMember = '코드팩토리';
  bts.firstMember = '아이언맨';
  
  print(blackPink.firstMember);
  print(bts.firstMember);
}

class Idol {
  final String name;
  final List<String> members;

  Idol(this.name, this.members);

  Idol.fromList(List values)
      : this.members = List<String>.from(values[0]),
        this.name = values[1];

  void sayHello() {
    print('안녕하세요 ${this.name}입니다.');
  }

  void introduce() {
    print('저희 멤버는 ${this.members}가 있습니다.');
  }

  String get firstMember {
    return this.members[0];
  }
  
  set firstMember(String name){
    this.members[0] = name;
  }
}
```

```text
지수
RM
코드팩토리
아이언맨
```

- `  String get firstMember { return this.members[0];
	- String을 리턴해주는 `getter`이다. 이름은 firstMember이다.
	- 파라미터를 사용하지 않는다.
		- 중괄호가 필요 없다.
- `  set firstMember(String name){ this.members[0] = name;`
	- `String name` 파라미터에 무조건 하나의 값만 들어간다.
	-  불변하게 짜는 게 주인 요즘 프로그래밍에서는 잘 사용하지 않는다.

# Private 속성

- 현재 무언가 선언이 되어있는 이 파일을 외부에서 사용할 수 없도록 한다.
- 클래스나 변수, 함수 앞에 `'_'`(언더바)를 넣으면 된다.

```Dart
void main() {
  _Idol blackPink속


```Dart
void main() {
  print('------- Idol -------');
  Idol apink = Idol(name: '에이핑크', membersCount: 5);

  apink.sayName();
  apink.sayMembersCount();

  print('------- Boy Group --------');
  BoyGroup bts = BoyGroup('BTS', 7);

  bts.sayName();
  bts.sayMembersCount();
  bts.sayMale();

  print('------- Girl Group --------');
  GirlGroup redVelvet = GirlGroup('Red Velvet', 5);

  redVelvet.sayMembersCount();
  redVelvet.sayName();
  redVelvet.sayFemale();

  print('------- Type Comparison --------');
  print(apink is Idol);
  print(apink is BoyGroup);
  print(apink is GirlGroup);

  print('------- Type Comparison 2 --------');
  print(bts is Idol);
  print(bts is BoyGroup);
  print(bts is GirlGroup);

  print('------- Type Comparison 3 --------');
  print(redVelvet is Idol);
  print(redVelvet is BoyGroup);
  print(redVelvet is GirlGroup);
}

class Idol {
  // 이름
  String name;
  // 멤버 숫자
  int membersCount;

  Idol({
    required this.name,
    required this.membersCount,
  });

  void sayName() {
    print('저는 ${this.name}입니다.');
  }

  void sayMembersCount() {
    print('${this.name}은 ${this.membersCount}명의 멤버가 있습니다.');
  }
}

class BoyGroup extends Idol {
  BoyGroup(
    String name,
    int membersCount,
  ) : super(
          name: name,
          membersCount: membersCount,
        );

  void sayMale() {
    print('저는 남자 아이돌입니다.');
  }
}

class GirlGroup extends Idol {
  GirlGroup(
    String name,
    int membersCount,
  ) : super(
          name: name,
          membersCount: membersCount,
        );

  void sayFemale() {
    print('저는 여자 아이돌입니다.');
  }
}

```

```text
------- Idol -------
저는 에이핑크입니다.
에이핑크은 5명의 멤버가 있습니다.
------- Boy Group --------
저는 BTS입니다.
BTS은 7명의 멤버가 있습니다.
저는 남자 아이돌입니다.
------- Girl Group --------
Red Velvet은 5명의 멤버가 있습니다.
저는 Red Velvet입니다.
저는 여자 아이돌입니다.
------- Type Comparison --------
true
false
false
------- Type Comparison 2 --------
true
true
false
------- Type Comparison 3 --------
true
false
true
```

- 상속을 받으면 부모 클래스의 모든 속성은 자식 클래스가 부여받는다.
- `extends`로 부모 클래스를 상속받을 수 있다.
	- 상속받을 때 부모 클래스가 정해둔 생성자를 준수해야한다.
- `super` 부모클래스를 자식클래스스에서 호출할 때 사용한다.
- 부모클래스(`idol`)는 자식 클래스(`BoyGroup`, `GirlGroup`)에서 추가된 변수나 메서드를 직접 사용할 수 없다.
- 자식 클래스는 부모 클래스의 변수와 를 사용할 수 있다.
- 자식 클래스의 인스턴스는 부모 클래스 타입으로 사용할 수 있다.
	- 부모 클래스의 인스턴스는 자식 클래스 타입으로 사용할 수 없다.

# Override

- override: 덮어쓰다, 우선시하겠다.
- 부모 클래스의 메소드를 재정의 할 수 있다.

```Dart
void main() {
  TimesTwo tt = TimesTwo(2);

  print(tt.calculate()); // TimesTwo의 calculate 메서드 호출

  TimesFour tf = TimesFour(2);

  print(tf.calculate()); // TimesFour의 calculate 메서드 호출
}

class TimesTwo {
  final int number;

  TimesTwo(
    this.number,
  );

  int calculate() {
    return number * 2;
  }
}

class TimesFour extends TimesTwo {
  TimesFour(
    int number,
  ) : super(number);

  @override
  int calculate() {
    return number * 4;
  }
}
```

- 사용하고자 하는 메소드 위에 `@override`를 붙인다.
- `super.number`를 쓸 때 `this.number` 또는 `number`도 가능하다.

```Dart
@override
  int calculate(){
    return super.calculate * 2;
  }
```

- 이렇게 메소드를 불러오는 것도 가능하다.
	- 이 때 `this.calculate`를 쓰면 자식 클래스의 `claculate`를 불러오게 되어 무한 반복되기 때문에 `super`를 써주어야 한다.

# Static

- static은 instance에 귀속되지 않고 class에 귀속된다.
	- 해당 클래스의 변수를 바꿔주면 다른 인스턴스에 공유된다.
	
```Dart
void main() {
  Employee seulgi = Employee("슬기");
  Employee chorong = Employee("초롱");
  seulgi.NameAndBuilding();
  chorong.NameAndBuilding();

  Employee.building = "오투타워";

  seulgi.NameAndBuilding();
  chorong.NameAndBuilding();
}

class Employee {
  static String? building;
  final String name;

  Employee(this.name);

  void NameAndBuilding() {
    print("제 이름은 $name입니다. $building 건물에서 근무하고 있습니다.");
  }

  static void Building() {
    print("$building에서 근무중입니다.");
  }
}
```

- `static` 멤버에 접근하려면 클래스 이름을 사용해야 한다.
	- `seulgi.building` (X)
	-
# Interface

```Dart
class IdolInterface {
  String name;
  
  IdolInterface(this.name);
  
  void sayName() {}
}

class BoyGroup implements IdolInterface{
  String name;
  
  BoyGroup(this.name);
  
  void sayName() {}
}
```

- Dart에서는 클래스를 인터페이스처럼 사용할 수 있다.
- `implements` 키워드를 사용한다.
	- 해당 클래스는 인터페이스에 정의된 모든 메서드를 구현해야 한다.
- 인터페이스는 형태를 강제하고, 상속은 기능과 속성을 물려주는 데 중점을 둔다.

```Dart
abstract class IdolInterface {
  String name;
  
  IdolInterface(this.name);
  
  void sayName(); 
}
```

- abstract: 인터페이스가 실수로 사용되는 것을 방지한다.
	- 이때는 인터페이스 안의 `body{}`를 지워도 된
# Generic

- 타입을 외부에서 받을 때 사용한다.

```Dart
void main() {
  Lecture<String> lecture1 = Lecture("123","lecture");
  lecture1.printIdType();
  
  Lecture<int> lecture2 = Lecture(123,"lecture");
  lecture2.printIdType();
}

class Lecture<T> {
  final T id;
  final String name;
  
  Lecture(this.id, this.name);
  
  void printIdType(){
    print(id.runtimeType);
  }
}
```

- `T` 는 아무거나 넣으면 된다.
- 여러 개 넣을 수 있다. `T, X, ···`
