## Functional Programming

# 형변환

```Dart
void main() {
  List<String> blackPink = ["로제","지수","리사","제니","제니"];
  
  print(blackPink);
  print(blackPink.asMap());
  print(blackPink.toSet());
}
```

```text
[로제, 지수, 리사, 제니, 제니]
{0: 로제, 1: 지수, 2: 리사, 3: 제니, 4: 제니}
{로제, 지수, 리사, 제니}
```
- `asMap`
	- Map으로 형변환한다.
	- key에는 인덱스, value에는 리스트의 값이 들어간다.
- `toSet`
	- Set으로 형변환한다.
	- 리스트에 중복된 값이 있으면 삭제된다.

```Dart
Map blackPinkMap = blackPink.asMap();
  
 print(blackPinkMap.keys.toList());
 print(blackPinkMap.values.toList());
```

```text
[0, 1, 2, 3, 4]
[로제, 지수, 리사, 제니, 제니]
```

`.toList` 를 붙이면 리스트의 형태로 받을 수 있다.

```Dart
  Set blackPinkSet = Set.from(blackPink);
  
  print(blackPinkSet.toList());
}
```

```text
[로제, 지수, 리사, 제니]
```

- `Set.from(blackPink)` 
	- list를 set을 만드는 방법 중 하나이다. (`toset`)
- `toList()`
	- set를 list로 만든다.

# List

```Dart
void main() {
  List<String> blackPink = ["로제","지수","리사","제니","제니"];
  

  final newBlackPink = blackPink.map((x) {
    return '블랙핑크 $x';
  });
  
  print(blackPink);
  print(newBlackPink.toList());
}
```

```text
[로제, 지수, 리사, 제니, 제니]
[블랙핑크 로제, 블랙핑크 지수, 블랙핑크 리사, 블랙핑크 제니, 블랙핑크 제니]
```

- `x`에 리스트의 각 멤버를 돌아가면서 받고, `return`하면 `블랙핑크 $x`에 값이 돌아가며 들어간다.
- blackPink의 값을 변경하는 것이 아니라 새로운 리스트를 만들어 리턴 값을 받는다.

```Dart
  final newBlackPink = blackPink.map((x){
    return "블랭핑크 $x";
  }).toList();
```

```Dart
  final newBlackPink2 = blackPink.map((x) => "블랙핑크 $x");
```

- arrow 함수를 이용해서 더 간결하게 쓸 수 있다.

```Dart
void main() {
  String number = "13579";
  final parsed = number.split("").map((x) => "$x.jpg").toList();
  print(parsed);
```

```text
[1.jpg, 3.jpg, 5.jpg, 7.jpg, 9.jpg]
```

- `number.split` 스트링 값들을 각 각 나눠 하나의 리스트로 만들어 준다.

# Map

```Dart
void main() {
  Map<String, String> harryPotter = {
    "Harry Potter": "해리 포터",
    "Ron Weasley": "론 위즐리",
    "Hermione Granger": "헤르미온느 그레인저"
  };

  final result = harryPotter.map((key, value) =>
      MapEntry(
        "Harry Potter Character $key", 
        "해리포터 캐릭터 $value"
      )
  );
  
  print(harryPotter);
  print(result);
}
```

```text
{Harry Potter: 해리 포터, Ron Weasley: 론 위즐리, Hermione Granger: 헤르미온느 그레인저}
{Harry Potter Character Harry Potter: 해리포터 캐릭터 해리 포터, Harry Potter Character Ron Weasley: 해리포터 캐릭터 론 위즐리, Harry Potter Character Hermione Granger: 해리포터 캐릭터 헤르미온느 그레인저}
```

- map을 통해 각 key와 value를 변경할 수 있다.
	- 새로운 맵으로 만든다.
	- 이 방법은 잘 사용하지 않는다.

```Dart
void main() {
  Map<String, String> harryPotter = {
    "Harry Potter": "해리 포터",
    "Ron Weasley": "론 위즐리",
    "Hermione Granger": "헤르미온느 그레인저"
  };
  
  final keys = harryPotter.keys.map((x) => "HPC $x").toList();
  final values = harryPotter.values.map((x) => "해리포터 $x").toList();
  
  print(keys);
  print(values);
}
```

```text
[HPC Harry Potter, HPC Ron Weasley, HPC Hermione Granger]
[해리포터 해리 포터, 해리포터 론 위즐리, 해리포터 헤르미온느 그레인저]
```

- key값, value값을 각각 리스트로 변경할 수 있다.

# Set

```Dart
void main() {
  Set blackPink = {
    "로제",
    "지수",
    "제니",
    "리사"
  };
  
  final newSet = blackPink.map((x) => "블랙핑크 $x").toSet();
  
  print(newSet);
}
```

```text
{블랙핑크 로제, 블랙핑크 지수, 블랙핑크 제니, 블랙핑크 리사}
```

- set도 map을 통해 데이터 값들을 변경할 수 있다.

# Where

```Dart
void main() {
  List<Map<String, String>> people = [
    {"name": "로제", "group": "블랙핑크"},
    {"name": "지수", "group": "블랙핑크"},
    {"name": "RM", "group": "BTS"},
    {"name": "뷔", "group": "BTS"}
  ];
  
  print(people);
  
  final blackPink = people.where((x) => x["group"] == "블랙핑크").toList();
  
  print(blackPink);
}
```

```text
[{name: 로제, group: 블랙핑크}, {name: 지수, group: 블랙핑크}, {name: RM, group: BTS}, {name: 뷔, group: BTS}]
[{name: 로제, group: 블랙핑크}, {name: 지수, group: 블랙핑크}]
```

- `people.where((x) => )`
	- map과 작동 방식이 유사하다.
	- 각 멤버들을 돌면서 true 또는 false를 반환한다.
		- true: 유지
		- false: 제거
			- 원래 리스트의 값을 변경하는 건 아니고, 새로운 리스트로 받아온다.
# Reduce

- 리스트의 모든 요소를 하나의 값으로 줄인다.

```Dart
void main() {
  List<int> numbers = [1, 3, 5, 7, 9];
  
  final result = numbers.reduce((prev, next){
    print("----------------");
    print("previous : $prev");
    print("next     : $next");
    print("total    : ${prev+next}");
    
    return prev+next;
  });
  
  print(result);
}
```

```text
----------------
previous : 1
next     : 3
total    : 4
----------------
previous : 4
next     : 5
total    : 9
----------------
previous : 9
next     : 7
total    : 16
----------------
previous : 16
next     : 9
total    : 25
25
```

- previous
	- 맨 처음에만 첫 번째 값이 들어간다.
	- 다음부터는 total, return해준 값이 들어간다.
- next  
	- 다음 값이 들어간다.

```Dart
final result = numbers.reduce((prev,next) => prev + next);
```

```text
25
```

- 코드를 이렇게 한 줄로 줄여 최종 결값을 받을 수 있다.


```Dart
void main() {
  List<String> words = ["안녕하세요", "저는", "코드팩토리입니다."];

  final sentence = words.reduce((prev, next) => prev + next);

  print(sentence);
}
```

```text
안녕하세요저는코드팩토리입니다.
```

-  return되는 값의 형태와 처음에 입력되는 데이터 타입이 같아야 한다.
	- numbers 는 int
	- words는 String

# Fold

- 같은 타입으로 return해주어야 하는 reduce와 달리 fold는 아무 형태나 return할 수 있다.
- fold`< >` 안에 반환할 형태를 적어준다.

```Dart
void main() {
  List<int> numbers = [1,3,5,7,9];
  
  final sum = numbers.fold<int>(0,(prev,next)=>prev+next);
  
  print(sum);
}
```

```text
25
```

- previous
	- 맨 처음에 선언해준 값이 들어간다.
	- 다음부터는 return해준 값이 들어간다.
- next  
	- 맨 처음에 리스트의 첫 번째 값이 들어가고, 이후 다음 값이 들어간다.

```Dart
void main() {
  List<String> words = ["안녕하세요 ","저는 ","코드팩토리","입니다."];
  
  final lengts = words.fold<int>(0,(prev,next) => prev + next.length);
  
  print(lengts);
}
```

```text
18
```

- 이렇게 문자열로 된 리스트의 길이 값도 구할 수 있다.

# Cascading Operator

- 여러 개의 리스트를 하나로 합칠 수 있다.

```Dart
void main() {
  List<int> even = [2,4,6,8];
  List<int> odd = [1,3,5,7];
  
  print([even,odd]);
  print([...even,...odd]);
}
```

```text
[[2, 4, 6, 8], [1, 3, 5, 7]]
[2, 4, 6, 8, 1, 3, 5, 7]
```

- even과 ...even은 다르다.
	- 새로운 리스트에 값을 풀어 넣는 것이다.

# 실전

```Dart
void main() {
  final List<Map<String, String>> people = [
    {"name": "지수", "group": "블랙핑크"},
    {"name": "로제", "group": "블랙핑크"},
    {"name": "RM", "group": "BTS"},
    {"name": "", "group": "BTS"},
  ];
  
  print(parsePeople);

  final parsePeople =
      people.map((x) => Person(name: x["name"]!, group: x["group"]!)).toList();
}

class Person {
  final String name;
  final String group;

  Person({
    required this.name,
    required this.group,
  });
}
```

```text
[Instance of 'Person', Instance of 'Person', Instance of 'Person', Instance of 'Person']
```

- map은 자유도가 높다.
	- map안에 name이 들어있는지, group이 들어있는지 알 수 없다.
- 매번 ! 으로 이 값들이 존재한다고 선언해야 한다.

```Dart
void main() {
  final List<Map<String, String>> people = [
    {"name": "지수", "group": "블랙핑크"},
    {"name": "로제", "group": "블랙핑크"},
    {"name": "뷔", "group": "BTS"},
    {"name": "RM", "group": "BTS"},
  ];

  final parsePeople =
      people.map((x) => Person(name: x["name"]!, group: x["group"]!)).toList();

  print(parsePeople);
}

class Person {
  final String name;
  final String group;

  Person({
    required this.name,
    required this.group,
  });

  @override
  String toString() {
    return "Person(name:$name), (group:$group)";
  }
}
```

```text
[Person(name:지수), (group:블랙핑크), Person(name:로제), (group:블랙핑크), Person(name:뷔), (group:BTS), Person(name:RM), (group:BTS)]
```


