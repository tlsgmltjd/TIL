## 컬렉션 프레임워크

- 자료구조 종류의 형태들을 자바 클래스로 구현한 모음집이다.
- 배열로 데이터를 관리하면 데이터를 저장할때 한전 정해진 배열의 크기를 변경할 수 없다는 단점이 있다.
  - 이런 단점을 컬렉션즈 프레임워크가 커버해준다.

컬렉션즈 프레임워크의 주요 인터페이스로는 `List`, `Set`, `Map`이 있다.

- `List`, `Set`은 공통된 부분이 많아 `Collection`이라는 상위 인터페이스가 정의되어있다.
- `Map`은 둘과 달리 키와 값을 쌍으로 관리하는 구조라서 독립된 인터페이스이다.

| interface | 설명                                                     | 구현클래스                     |
| --------- | -------------------------------------------------------- | ------------------------------ |
| List      | 순서 O, 데이터 중복 O                                    | ArrayList, LinkedList ...      |
| Set       | 순서 X, 데이터 중복 X                                    | HashSet, TreeSet...            |
| Map       | <Ket, Value>가 쌍으로 저장, 순서 X, (키가 다르면) 중복 O | HashMap, TreeMap, Hashtable... |

### List

- List 인터페이스는 순서를 유지하며 중복 저장을 허용한다.
- 구현체로는 ArrayList, LinkedList가 있다.
- 배열과 비슷한 자료구조이다.
  - 배열과 차이점으론 배열은 한번 생성하면 크기를 변경할 수 없지만 리스트 자료구조는 저장공간이 필요에 따라 자유롭다.

```java
List<String> list = new AarrayList<>();
// 데이터 저장
list.add("hello");
list.add("hello world");
list.add("hello");

System.out.println(list.size()); // 3

for (int i = 0; i < list.size(); i++) {
    String str = list.get(i);
    System.out.println(str);
}
```

### Set

- Set 인터페이스는 중복이 없고 순서도 없는 자료구조이다.
- 구현체로는 HashSet, TreeSet 등이 있다.

```java
Set<String> set1 = new HashSet<>();
// 데이터 저장
boolean res1 = set1.add("hello"); // true
boolean res2 = set1.add("hello world"); // true
boolean res3 = set1.add("hello"); // false (중복값이기 때문에 저장되지 않음)

System.out.println(set1.size()); // 2

Iterator<String> iter = set1.iterator();
while(iter.hasNext()) {
    String str = iter.next();
    System.out.println(str);
}
```

### Map

- key, value를 쌍으로 저장하는 자료구조이며 키는 중복될 수 없고, 값은 중복이 가능하다.
- 구현체로는 HashMap, TreeMap이 있다.

```java
Map<String, String> map = new HashMap<>();
map.put("001", "hello1");
map.put("002", "hello2");
map.put("003", "hello3");

map.put("001", "hello4");

System.out.println(map.size()); // 3 -> 중복된 키로 등록한 데이터가 있기 때문에 해당 데이터가 기존의 데이터를 덮어씌움

System.out.println(map.get("001")); // -> "hello4"

// map 자료구조의 모든 키들을 Set 자료구조로 담아줌
Set<String> keys = map.keySet();

Iterator<String> iter = keys.iterator();
while(iter.hasNext()) {
    String key = iter.next();
    System.out.println(map.get(key));
}
```
