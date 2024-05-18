# 자바 컬렉션 프레임 워크 (JCF)
- 데이터를 저장하는 자료구조와 데이터를 처리하는 알고리즘을 구조화하여 클래스로 구현한 것이다.
- java.util 패키지에 구현되어 있다.
- 크게 List, Set, Map으로 구분할 수 있다.

![jcf](./img/jcf.jpg)

## 특징

인터페이스 | 특징 | 구현 클래스
-|-|-
List| 순서가 있는 데이터의 집합. 데이터의 중복을 허용 | [LinkedList](/Data-Structure/Linked-List.md), [Stack](/Data-Structure/Stack.md), [Vector](/Data-Structure/Vector.md), [ArrayList](/Data-Structure/ArrayList.md)
Set | 순서가 없는 데이터의 집합. 데이터의 중복 비허용  | [HashSet](/Data-Structure/HashSet.md), [TreeSet](/Data-Structure/TreeSet.md)
Map | 키와 값의 한 쌍으로 이루어지는 데이터의 집합으로 순서가 없다.<br>키는 중복 비허용, 값은 허용 | [HashMap](/Data-Structure/Hash-Map.md), [TreeMap](/Data-Structure/TreeMap.md), [HashTable](/Data-Structure/Hash-Table.md), Properties

## Collection

- 하나의 객체를 관리하기 위한 메서드가 선언된 인터페이스
- 여러 클래스들이 Collection 인터페이스를 구현한다.
- Collection에 선언되는 주요 메서드

메서드|설명
-|-
boolean add(E e)|Collection에 객체를 추가
void clear()|Collection의 모든 객체를 제거
Iterator<E> iterator|Collection을 순환할 반복자(Iterator)를 반환
boolean remove(Object o)|Collection에 매개변수에 해당하는 인스턴스가 존재할시 제거
int size|Collection에 있는 요소의 개수 반환

## Map

- key-value pair의 객체를 관리하는데 필요한 메서드가 정의된다.
- key는 중복x
- 검색을 위한 자료구조
- key를 이용하여 값을 저장하거나 검색, 삭제할 때 사용하면 편리
- 내부적으로 hash 방식으로 구현된다.

```java
index = hash(key) // index는 저장 위치
```
- key가 되는 객체는 객체의 유일성함의 여부를 알기 위해 equals()와 hashCode() 메서드를 재정의한다.
- 여러 클래스들이 Map 인터페이스를 구현한다.
- Map 인터페이스에 선언되는 주요 메서드

메서드|설명
-|-
V put(K key, V value|	key에 해당하는 value 값을 map에 넣는다.
V get(K key)|	key에 해당하는 value 값을 반환한다.
boolean isEmpty()|	Map이 비었는지 여부를 반환한다.
boolean containsKey(Object key)|	Map에 해당 key가 있는지 여부를 반환한다.
boolean containsValue(Object value)|	Map에 해당 value가 있는지 여부를 반환한다.
Set keyset()|	key 집합을 Set로 반환한다. (중복 안 되므로 Set)
Collection values()|	value를 Collection으로 반환한다. (중복 무관)
V remove(key)|	key가 있는 경우 삭제한다.
boolean remove(Object key, Object value)|	key가 있는 경우 key에 해당하는 value가 매개변수와 일치할 때 삭제한다.
