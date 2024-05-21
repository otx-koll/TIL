# ArrayList

배열을 기반으로 한 컬렉션의 하나이며, 데이터를 추가, 삭제시 내부에서 동적으로 배열의 길이를 조절해준다.

## 특징

- 연속적인 데이터의 리스트(중간에 빈공간 x)
- 내부적으로 `Object[]` 배열을 이용하여 요소를 저장한다.
- 내부적으로 배열을 이용하기 때문에 인덱스를 이용해 요소에 빠르게 접근할 수 있다.
- 데이터의 크기에 따라 가변적으로 공간을 늘리거나 줄인다.
- 그러나 배열 공간이 꽉찰 때마다 배열을 복사하는 방식으로 늘리는데, 이때마다 지연이 된다.
- 데이터를 리스트 중간에 삽입/삭제 할 경우, 중간에 빈 공간이 생기지 않도록 요소들의 위치를 앞뒤로 이동시키기 때문에 삽입/삭제 동작이 느리다.
- 따라서 조회를 많이 하는 경우에 사용하는 것이 좋다.

**1. ArrayList vs 배열**

배열은 길이가 고정된 반면 ArrayList는 배열의 길이를 자동으로 조절해주는 기능을 가지고 있어 가변적이다.

**2. ArrayList vs Vector**

ArrayList와 Vector는 멀티 스레드 환경을 위한 동기화를 제외하고는 거의 유사하다. 다만, ArrayList는 동기화 처리가 되어 있지 않은 대신 처리 속도가 빠르다.

**3. ArrayList vs LinkedList**

ArrayList는 내부적으로 배열을 기반으로 하기 때문에 데이터의 위치 정보를 바로 알 수 있어 데이터를 읽는 속도가 LinkedList에 비해 빠르다. 대신 데이터를 중간에 삽입하거나 삭제가 빈번할 경우엔 데이터의 이동 없이 연결 정보만을 가지고 있는 LinkedList가 더 효율적이다.

## ArrayList 사용법

### 객체 생성

ArrayList를 사용하기 위해선 패키지를 `import`해줘야한다.

```java
import java.util.ArrayList;
```

메소드|설명
-|-
ArrayList()|크기가 10인
ArrayList(Collection c)|주어진 컬렉션이 저장된 ArrayList를 생성
ArrayList(int initialCapacity)|지정된 초기용량을 갖는 ArrayList를 생성

```java
// 타입설정 Integer 객체만 적재가능
ArrayList<Integer> members = new ArrayList<>();

// 초기 용량(capacity) 지정
ArrayList<Integer> num1 = new ArrayList<>(10);

// 배열을 넣어 생성
ArrayList<Integer> list1 = new ArrayList<>(Arrays.asList(1, 2, 3));

// 다른 컬렉션으로부터 그대로 요소를 받아와 생성
// ArrayList를 인자로 받는 API를 사용하기 위해서 Collection 타입 변환이 필요할 때 많이 사용
ArrayList<Integer> list2 = new ArratList<>(list1);
```

생성 문법을 보면 `<>`기호를 이용해 타입을 지정하는 걸 알 수 있으며, 저 기호가 바로 제네릭이다.

- `제네릭(Generics)` : 클래스 내부에서 사용할 데이터 타입을 외부에서 지정하는 기법

만약 `<>` 안에 String 타입명을 작성하면 ArrayList 클랙스 자료형의 타입은 String 타입으로 지정되어 문자열 데이터만 리스트에 적재할 수 있게 된다.

### 요소 추가

객체를 생성할 때 지정한 타입의 데이터만 추가가 가능하다.

- `용량(capacity)` : 리스트의 공간 용량
- `크기(size)` : 리스트에 들어있는 요소들의 총 개수

메소드|설명
-|-
boolean add(Object obj)	|ArrayList의 마지막에 객체를 추가하며, 성공하면 true를 리턴한다.
void addAll(Collection c)|주어진 컬렉션의 모든 객체를 저장하며, 마지막 index 뒤에 붙인다.

```java
ArrayList<String> list1 = new ArrayList<>(5); // 용량 5으로 지정
list1.add("A");

ArrayList<String list2 = new ArrayList<>(5);
list2.add("C");
list2.add("D");

list1.addAll(list2);		// list1에 list2의 내용 추가
System.out.println(list1);	// [A, C, D] 출력
```

### 요소 삽입

원하는 인덱스에 요소를 넣을 수 있게 기존의 요소들이 한 칸씩 뒤로 이동되면서 빈 공간을 만들어낸다. 

메소드|설명
-|-
boolean add(int index, Object obj)|지정된 index에 객체를 저장하며, 자리에 있던 기존의 데이터는 삭제되지 않고 뒤로 밀려난다.
void addAll(Collection c)|지정된 index부터 주어진 컬렉션의 데이터를 저장하며, 자리에 있던 기존의 데이터는 삭제되지 않고 뒤로 밀려난다.

위치를 지정하여 삽입할 시 인덱스가 리스트의 용량을 넘지 않도록 조절해야 한다.

```java
ArrayList<String> list = new ArrayList<>(5); 

list.add("1");
list.add("2");
list.add("3");
list.add(1, "A");

System.out.println(list); // [1, A, 3]
```

### 요소 삭제

요소의 삭제도 중간에 위치한 요소를 제거할 경우, 나머지 요소들이 빈 공간을 채우려 앞쪽으로 이동하게 된다.

메소드|설명
-|-
Object remove(int index)|지정된 위치(index)에 있는 객체를 제거한다.
boolean remove(Object obj)|지정된 객체를 제거하고, 성공하면 true를 리턴한다.
boolean removeAll(Collection c)|지정한 컬렉션에 저장된 것과 동일한 객체들을 ArrayList에서 제거한다.
void clear()|ArrayList를 완전히 비운다.
boolean retainAll(Collection c)|ArrayList에 저장된 객체 중에서 주어진 컬렉션과 공통된 것들만 남기고 제거한다.(removeAll의 반대 버전)

```java
ArrayList<String> list = new ArrayList<>(5);

list.add("1");
list.add("2");
list.add("3");
list.remove(1);
System.out.println(list); // [1, 3]

// 모든 값 제거
list.clear();
System.out.println(list); // []
```

### 요소 검색

메소드|설명
-|-
boolean isEmpty()|ArrayList가 비어있는지 확인한다.
boolean contains(Object obj)|지정된 객체(obj)가 ArrayList에 포함되어 있는지 확인한다.
int indexOf(Object obj)|지정된 객체(obj)가 저장된 위치를 찾아 반환한다.
int lastIndexOf(Object obj)|지정된 객체(obj)가 저장된 위치를 뒤에서부터 역방향으로 찾아 반환한다.

```java
ArrayList<String> list1 = new ArrayList<>();
list1.add("A");
list1.add("B");
list1.add("A");

// list에 A가 있는지 검색 : true
list1.contains("A"); 

// list에 A가 있는지 순차적으로 검색하고 index를 반환 (만일 없으면 -1)
list1.indexOf("A"); // 0

// list에 A가 있는지 역순으로 검색하고 index를 반환 (만일 없으면 -1)
list1.lastIndexOf("A"); // 2
```

### 요소 얻기

메소드|	설명
-|-
Object get(int index)|지정된 위치(index)에 저장된 객체를 반환한다.
List subList(int from_index, int to_index)|from_index부터 to_index-1 사이에 저장된 객체를 반환한다.

```java
ArrayList<String> list = new ArrayList<>(5); 

list.add("J");
list.add("A");
list.add("v");
list.add("A");

// 개별 단일 요소 반환
list.get(0); 		// "J"

// list[0] ~ list[3] 범위 반환
list.subList(0, 4); // [J, A, V, A]
```

### 요소 변경

메소드|	설명
-|-
Object set(int index, Object obj)|	주어진 객체(obj)를 지정한 위치(index)에 저장한다.
자리에 있던 기존의 데이터는 삭제되고, 새로운 데이터가 대체되어 들어간다.

```java
ArrayList<String> list = new ArrayList<>(5); 

list.add("data1");
list.add("data2");
list.add("data3");

// index 1번의 데이터를 문자열 "setData"로 변경한다.
list.set(1, "setData");

System.out.println(list);	// [data1, setData, data3]
```

### 용량 확장

데이터를 추가하면서 용량(capacity)보다 크기(size)가 커진다면, 자동으로 용량을 늘려준다. 

만약 자동으로 용량을 늘려야한다면, 자체적으로 배열을 큰사이즈로 새로 만들고, 기존의 배열에서 요소들을 복사해 간접적으로 리스트의 용량을 늘린다.

하지만 이런 동작은 리스트를 다루기엔 편하지만, 배열 복사 동작 자체가 비용이 꽤 크기 때문에 오버헤드를 발생시키게 된다.

메소드|설명
-|-
int size()|	ArrayList에 저장된 객체의 개수를 반환한다.
void ensureCapacity(int minCapacity)|ArrayList의 용량이 최소한 minCapacity가 되도록 한다.
void trimToSize()|용량의 크기에 맞게 줄인다(빈 공간을 없앤다)

```java
ArrayList<String> list1 = new ArrayList<>(5); // 용량(capacity)를 5으로 설정

// 용량 5을 넘은 요소 7개 추가
list1.add("A");
list1.add("B");
list1.add("C");
list1.add("D");
list1.add("E");
list1.add("F");
list1.add("G");

// 크기(size)는 7 : 자동으로 용량이 증가되어 데이터를 적재함(오버헤드 발생)
list1.size();

// --------------------------------------------------

ArrayList<String> list2 = new ArrayList<>(5); // 용량(capacity)를 5으로 설정

// 용량 5에 맞게 요소 5개 추가
list2.add("A");
list2.add("B");
list2.add("C");
list2.add("D");
list2.add("E");

// ensureCapacity() 메소드를 이용해 용량 확장
list2.ensureCapacity(10);

// 용량 확장 후 요소 추가
list2.add("F");
list2.add("G");

// 미리 확장해 오버헤드 발생하지 않았다.
// 따라서, 사용될 데이트의 개수를 미리 알고있는 경우엔 처음에 그 값으로 선언해주면 된다.
System.out.println(list); // [1, 2, 3, 4, 5, 6, 7]
```

### 복사

메서드|설명
-|-
Object clone()|ArrayList를 복제한다.

```java
ArrayList<Integer> number = new ArrayList<>();
number.add(1);
number.add(3);
number.add(5);

// ArrayList는 내부적으로 Object[] 배열로 저장하기 때문에 형변환이 필요함
ArrayList<Integer> cloneNumber = (ArrayList<Integer>) number.clone();

System.out.println("ArrayList: " + number); // [1, 3, 5]
System.out.println("Cloned ArrayList: " + cloneNumber); // [1, 3, 5]
```

### 배열 변환

메서드|설명
-|-
Object[] toArray()|ArrayList에 저장된 모든 객체들을 배열로 반환한다.
Object[] toArray(Obejct[] objArr)|ArrayList에 저장된 모든 객체들을 배열 objArr에 담아 반환한다.

```java
ArrayList<String> languages= new ArrayList<>();
languages.add("Java");
languages.add("Python");
languages.add("C");

/* ArrayList<String> 을 String[] 배열로 변환 */

// 방법 1 : 배열로 변환하고 반환
String[] arr1 = languages.toArray();

// 방법 1 : 매개변수로 지정된 배열에 담아 바환
String[] arr2 = new String[languages.size()]; // 먼저 리스트 사이즈에 맞게 배열 생성
languages.toArray(arr2);
```

### 정렬

주의할 점은 `sort()`메소드는 정렬된 값을 반환하는 것이 아니라 원본 리스트 자체를 변경시키는 점이다.

메소드|	설명
-|-
void sort(Comparator c)|지정된 정렬기준(c)으로 ArrayList를 정렬한다.

Comparator를 이용해 정렬하기 위해선 패키지를 import 해줘야한다.

```java
import java.util.Comparator;

ArrayList<String> list1 = new ArrayList<>();
list1.add("3");
list1.add("2");
list1.add("1");

// 오름차순 정렬
list1.sort(Comparator.naturalOrder());
System.out.println(list1);	// [1, 2, 3]

// 내림차순 정렬
list1.sort(Comparator.reverseOrder());
System.out.println(list1);	// [3, 2, 1]
```

### 순회

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(1);
list.add(2);
list.add(3);
list.add(4);

for (Integer i : list){
	System.out.println(i);
}
```

### 이터레이터

몇몇 컬렉션에서는 저장된 요소를 Iterator 인터페이스로 읽어오도록 하는 순회 패턴을 지향하기도 한다.

메소드|설명
-|-
Iterator iterator()|ArrayList의 Iterator 객체를 반환한다.
ListIterator listIterator()|ArrayList의 ListIterator를 반환한다.
ListIterator listIterator(int index)|ArrayList의 지정된 위치부터 시작하는 ListIterator를 반환한다.

Collection 인터페이스에서는 Iterator 인터페이스를 구현한 클래스의 인스턴스를 반환하는 `irerator()` 메소드를 정의해 각 요소에 접근하도록 정의하고 있다. 따라서 Collection 인터페이스를 상속받는 List나 Set 인터페이스에서도 `iterator()` 메소드를 사용할 수 있다.

```java
// 이터레이터 객체 반환
Iterator<Integer> iter = list.iterator();

// 만일 다음 요소가 있을 경우 반복
while(iter.hasNext()){
	System.out.println(iter.next());	// 1, 2, 3를 출력하고 종료
}
```

또한, ArrayList에는 Iterator뿐만 아니라 리스트 전용 이터레이터 객체인 ListIterator도 지원한다.

ListIterator 인터페이스는 Iterator 인터페이스를 상속받아 여러 기능을 추가한 인터페이스이며, Iterator는 컬렉션의 요소를 접근할 때 단방향으로만 이동할 수 있는 반면, ListIterator 인터페이스는 컬렉션 요소의 대체, 추가, 검색 등을 위한 작업에서 양방향으로 이동하는 것을 지원해 쓰임새가 더 넓다.

그리고 Iterator는 Collection 인터페이스를 구현한 컬렉션에서 모두 사용할 수 있는 반면, ListIterator는 오로지 List 컬렉션에서만 사용이 가능하다.

```java
// ListIterator 객체 반환
ListIterator<Integer> iter = lnkList.listIterator();

// 만일 다음 요소가 있다면 반복
while (iter.hasNext()) {
    System.out.println(iter.next()); // 요소를 출력하고 반복 위치를 뒤로 이동
} 

// -- 리스트를 끝까지 순회한 상태

// 만일 이전 요소가 있다면 반복
while (iter.hasPrevious()) {
    System.out.println(iter.previous()); // 요소를 출력하고 반복 위치를 앞으로 이동
}
```
