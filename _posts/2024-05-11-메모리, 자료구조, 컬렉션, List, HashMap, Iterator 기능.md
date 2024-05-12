---
title: 메모리, 자료구조, 컬렉션, List, HashMap, Iterator 기능
date: 2024-05-11 18:00:00 +09:00
categories: [1. Fundamental, Java]
tags: [Java, Fundamental, Memory, Data Structure, Collections, Collections Framework, List, ArrayList, LinkedList, HashMap, Set, Contains, Iterator, Hash, Stack, Queue, Heap, Brute Force, Sorting]
---

<!-- 2024-05-11 글 작성 시작; 2024-05-12 페이지 호출 완료 -->
<h2>강의 내용 복습 : 코리아IT 신촌점 자바 강의 (2024-05-08 강의)</h2>
> - Tool :  
<img alt="Java" src="https://img.shields.io/badge/-Java-007396?style=flat-square&logo=java&logoColor=white" />
<img alt="Eclipse" src="https://img.shields.io/badge/-Eclipse-2C2255?style=flat-square&logo=eclipse&logoColor=white" />

<br>

### 🔔 메모리(Memory)
### 📌 메모리 뜻
> - 메모리는 컴퓨터에서 데이터를 저장 또는 처리하는 가장 기본적인 단위입니다.
> - 메모리는 컴퓨터에 내장된 물리적인 부분이며 주로 주기억장치 및 보조기억장치로 구분됩니다.

### 📌 주기억장치(Primary Memory)
> - 컴퓨터의 CPU가 접근할 수 있는 공간이며 각종 데이터 및 명령어가 저장되는 곳입니다.
> - 프로세스 처리 속도가 빠른 편이지만 전원이 꺼지면 데이터가 사라지는 휘발성이 있습니다.
> - 아래는 주기억장치의 종류입니다.
>    - 램(RAM) : 데이터 또는 프로그램을 일시적으로 저장하는 기능이 있습니다.
>    - 캐시(Cache) 메모리 : CPU 내부에 위치하며 자주 사용되는 데이터를 복사해두고 사용됩니다.

### 📌 보조기억장치(Secondary Storage)
> - 보조기억장치는 주기억장치보다 처리 속도가 느리지만 전원이 꺼져도 데이터가 유지됩니다.
> - 그래서 대용량 데이터를 반영구적으로 저장하는 데 사용됩니다.
> - 아래는 보조기억장치의 종류입니다.
>    - HDD(Hard Disk Drive) : 자기 디스크라는 것을 사용하여 데이터를 저장합니다.
>    - SSD(Solid State Drive) : 반도체 칩을 사용하여 데이터를 저장합니다.
>    - 외장 하드 드라이브 : 컴퓨터에 연결하여 사용하는 저장소입니다.

<br>

### 🔔 자료구조(Data Structure)
### 📌 자료구조 뜻
> - 자료구조는 추상적인 개념이며 데이터에 효율적으로 접근하기 위한 개념입니다.
> - 즉, 데이터를 효율적으로 저장, 관리, 처리하기 위해 필요한 것입니다.
> - 각 자료구조의 특징이 있기 때문에 필요한 기능에 따라 자료구조를 달리 선택해야 됩니다.
> - 참고로 컬렉션(Collections)이란 자료구조가 메모리에 실제 구현된 것입니다.

### 📌 자료구조 : 기본 or 추상
> - 기본 및 추상 잣대의 자료구조는 아래와 같이 구분됩니다.
>    - 기본 자료구조 : int, double, char, boolean
>    - 추상 자료구조 : Array, List, Stack, Queue, HashTable, Set, Graph, Tree

### 📌 자료구조 : 선형 or 비선형
> - 선형 및 비선형 잣대의 자료구조는 아래와 같이 구분됩니다.
>    - 선형 자료구조 : ArrayList, LinkedList, Stack, Queue
>    - 비선형 자료구조 : HashTable, Graph, Binary Search Tree

### 📌 자료구조 : 정적 or 동적
> - 정적 및 동적 잣대의 자료구조는 아래와 같이 구분됩니다.
>    - 정적 자료구조 : 컴파일 과정 중에 메모리 크기(공간)가 결정되는 것
>    - 동적 자료구조 : 프로그램 실행 중에 메모리 크기가 변경되는 것

### 📌 컬렉션(Collections Framework)
> - 컬렉션이란 추상적인 개념의 자료구조가 라이브러리 형태로 메모리에 실제 구현된 것입니다.
> - 즉, 컬렉션은 단어 그대로 자료구조의 집합을 뜻합니다.
> - 참고로 모든 자료구조가 컬렉션에 포함되는 것은 아닙니다.
> - 예를들어 HashMap의 경우 자료구조는 맞지만 Collections Framework에 포함되지는 않습니다.
> - 실무에서 자주 사용되는 자료구조는 리스트(List), 맵(HashMap), 셋(Set) 등이 있습니다.

<br>

### 🔔 리스트(List)
### 📌 List 특징
> - 리스트는 ArrayList 및 LinkedList로 구분되며 이는 Array와 상이합니다.
> - 배열은 한 번 생성하면 데이터 크기 변경, 데이터 수정 및 삭제 등에 제약이 있는 편입니다.
> - 이와는 달리 리스트는 데이터 크기 변경, 데이터 수정 및 삭제 등에 제약이 없는 편입니다.
> - 한 예시로 ArrayList는 데이터를 삽입하는 대로 데이터 크기가 증대합니다.

### 📌 ArrayList 소개
> - ArrayList는 데이터를 순차적으로 삽입 또는 삭제할 때 처리 속도가 빠른 편입니다.
> - ArrayList는 데이터를 임의적으로 삽입 또는 삭제할 때 처리 속도가 느린 편입니다.
> - 데이터의 임의적인 중간 삽입 또는 삭제 속도를 개선하기 위한 것은 LinkedList입니다.

### 📌 ArrayList 특징
> - 보통 데이터를 순차적으로 삽입하려는 목적의 저장용으로 사용됩니다.
> - add 메서드로 새로운 배열 요소를 생성 및 치환합니다.
> - 내부 구조가 배열로 되어있습니다.
> - ArrayList 생성 시 배열의 길이를 설정할 필요가 없습니다.

### 📌 LinkedList 소개
> - LinkedList는 데이터를 임의적으로 삽입 또는 삭제할 때 처리 속도가 빠른 편입니다.
> - LinkedList는 데이터를 순차적으로 삽입 또는 삭제할 때 처리 속도가 느린 편입니다.
> - 단, 데이터 처리량이 10만 건 이상일 경우에 처리 속도가 ArrayList와 차이납니다.
> - 게다가 데이터 처리량이 10만 건 이하일 경우 LinkedList의 데이터 처리 속도가 더 빠릅니다.
> - 따라서 10만 건 이하 정도의 데이터 작업일 경우 LinkedList 사용이 더 효율적일 수 있습니다.

### 📌 LinkedList 특징
> - 보통 데이터를 임의적으로 삽입 또는 삭제하려는 목적의 연산용으로 사용됩니다.
> - LinkedList의 데이터는 node 형태로 구분되며 List 내에 Head Node와 Tail Node가 있습니다.
> - 각각의 node에는 이전 node 및 이후 node의 주소와 value 데이터가 포함됩니다.
> - node의 주소를 공유하기 때문에 탐색, 정렬 등의 연산 속도가 빠른 편입니다.

### 📌 List 활용
> - 개발 프로젝트에서 불특정 다수의 데이터 작업이 요구된다면 ArrayList 사용이 더 효율적입니다.
> - 이때 데이터 임의 처리가 빈번하다면 일부를 LinkedList로 이동시켜서 작업하는 것이 좋겠습니다.
> - 리스트는 선형 자료 구조이며 인덱스가 있기에 순차적인 데이터 처리가 가능합니다.
> - 리스트를 사용하려면 제네릭(Generic)을 이용하여 데이터 유형을 설정합니다.

<br>

### 🔔 맵(HashMap)
### 📌 HashMap 소개
> - HashMap은 데이터가 key 및 value 쌍으로 구성되는 HashTable 자료구조 형태로 구성됩니다.
> - 그래서 데이터 저장 또는 삭제 속도가 다른 자료구조에 비해 느린 편입니다.
> - 그런데 key라는 고유값으로 데이터를 탐색하기 때문에 탐색 속도는 매우 빠른 편입니다.
> - 따라서 프로젝트에서 데이터 탐색 기능이 빈번하게 요구되는 경우 HashMap을 이용합니다.

### 📌 HashMap 특징
> - HashMap을 사용하려면 제네릭에 해당 key 및 value의 데이터 유형을 함께 설정합니다.
> - 각각의 HashMap 객체는 주소 또는 값으로 구분되며 이때의 주소는 16진수의 HashCode입니다.
> - HashMap은 데이터의 순서가 없기 때문에 임의의 중간 삽입 또는 삭제가 불가능합니다.
> - 참고로 LinkedHashMap의 경우 데이터 순서는 있지만 인덱스가 없습니다.

### 📌 HashMap 활용
> - HashMap의 key 데이터는 중복을 허용하지 않습니다.
> - 그런데 key 데이터 자체가 중복되면 value 데이터가 업데이트 됩니다.
> - value 데이터 치환을 방지하기 위해서는 putIfAbsent 메서드를 이용하면 됩니다.

<br>

### 🔔 셋(Set)
### 📌 Set 특징
> - 셋은 리스트와 비슷한 기능을 제공하지만 인덱스가 없기에 데이터의 순서가 없습니다.
> - 따라서 순차적인 데이터 처리는 가능하지만 임의의 데이터 처리는 불가능합니다.
> - 한편 셋은 리스트와 달리 중복을 허용하지 않습니다.
> - 만일 중복된 데이터가 삽입될 경우 초기 데이터를 제외한 나머지 데이터는 무시됩니다.
> - 그러므로 셋은 중복 데이터 처리 시 활용될 수 있지만 자주 사용되는 것은 아니라고 합니다.

<br>

### 🔔 Collections Framework 주요 기능
### 📌 contains 메서드
> - contains 메서드는 자료구조의 중복 데이터를 탐색하는 기능을 제공합니다.
> - 예를들면 HashMap에는 containsKey 및 containsValue, List에는 contains가 있습니다.

### 📌 Iterator 인터페이스
> - Iterator는 Java의 Collections Framework에서 제공하는 데이터 접근 방법 중 하나입니다.
> - Iterator는 대부분의 컬렉션 타입(List, Set, Map)에서 사용 가능합니다.
> - List 및 Set의 경우 .iterator 메서드로 Iterator를 직접적으로 사용할 수 있습니다.
> - HashMap의 경우 .keySet, .values 등을 통해 key 또는 value의 집합을 순회할 수 있습니다.

### 📌 Iterator 활용
> - Iterator는 요소의 순서를 유지하면서 데이터를 처리할 때 안전하고 유용합니다.
> - 특히 List의 구현체가 LinkedList인 경우 Iterator를 사용하면 성능상 이점이 있습니다.
> - 왜냐하면 Iterator를 이용하면 인덱스 기반의 접근이 필요하지 않기 때문입니다.
> - 반면 인덱스를 통한 접근이나 특정 요소에 빠르게 접근해야 되는 경우에는 적합하지 않습니다.

### 📌 Iterator 주요 메서드
> - Iterator 인터페이스는 자료구조를 순회하기 위해 아래 메서드를 기본적으로 정의합니다.
> - hasNext(), next(), remove() 메서드는 Iterator의 핵심 메서드입니다.

### 📌 hasNext 메서드
> - Iterator가 다음 요소를 포함하는지 확인합니다.
> - 순회할 요소가 있으면 true, 없으면 false를 반환합니다.
> - 그래서 while 반복문 등 반복문의 조건에 잘 사용됩니다.

### 📌 next 메서드
> - Iterator 순회 중 다음 요소를 반환합니다.
> - 만일 반환될 요소가 없을 경우 NoSuchElementException이 발생됩니다.

### 📌 remove 메서드
> - 자료구조에서 조건에 해당되는 요소를 제거합니다.
> - 참고로 remove 메서드는 next 메서드 실행 이후에 적용 가능합니다.
> - 아래는 Iterator 인터페이스 및 주요 메서드 사용 예시입니다.
> - 출력 내용에서 remove 메서드가 잘 작동된 것이 확인됩니다.

``` java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class TestIterator {
	
	public static void main(String[] args) {
		
		List<Integer> number = new ArrayList<>();
		
		number.add(1);
		number.add(2);
		number.add(3);
		number.add(4);
		number.add(5);
		number.add(6);
		number.add(7);
		number.add(8);
		number.add(9);
		number.add(10);
		
		Iterator<Integer> iterateNumber = number.iterator();
		
		while(iterateNumber.hasNext()) {
			int someValue = iterateNumber.next();
			System.out.println(someValue);
			System.out.println(number);
			
			if(someValue > 5) {
				iterateNumber.remove();
			}
		}
		
		System.out.println();
		
		System.out.println("Result of Iterator Test = " + number);
		
	}

}
```

```
1
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
2
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
3
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
4
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
5
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
6
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
7
[1, 2, 3, 4, 5, 7, 8, 9, 10]
8
[1, 2, 3, 4, 5, 8, 9, 10]
9
[1, 2, 3, 4, 5, 9, 10]
10
[1, 2, 3, 4, 5, 10]

Result of Iterator Test = [1, 2, 3, 4, 5]
```

<br>

### 🔔 응용 학습
### 📌 해시(Hash)
> - 해시는 key 및 value를 매핑하여 데이터를 저장하는 비선형 자료구조입니다.
> - Hash는 하나의 개념이며 HashMap, HashTable 등의 자료구조에 적용됩니다.
> - 해시 함수를 이용하여 데이터가 저장되는 위치를 결정하며 데이터 탐색 속도가 매우 빠릅니다.
> - 메모리 관점에서 해시는 특정 메모리 영역을 지칭하지는 않습니다.
> - 참고로 HashCode (객체의 주소)는 16진수로 구성되어 있습니다.

### 📌 스택(Stack)
> - 스택은 LIFO (Last In, First Out) 원칙을 따르는 선형 자료구조입니다.
> - LIFO는 데이터의 입력/출력이 한쪽 끝에서만 이루어지는 것을 의미합니다.
> - 메모리 관점에서 스택은 함수의 매개변수, 반환 주소, 지역 변수 등이 저장됩니다.
> - 스택은 함수의 호출, 반환, 괄호 검사 등에 이용됩니다.

### 📌 큐(Queue)
> - 큐는 FIFO (First In, First Out) 원칙을 따르는 선형 자료구조입니다.
> - FIFO는 한쪽 끝에서는 데이터의 입력, 다른 한쪽 끝에서는 출력되는 것을 의미합니다.
> - 메모리 관점에서 큐는 메모리 영역이 아닌 데이터 관리 목적의 추상적인 개념입니다.
> - 큐는 프린터의 인쇄 대기열, 작업 스케줄링 등에 사용됩니다.

### 📌 힙(Heap)
> - 힙은 이진 트리(Binary Tree) 기반의 비선형 자료구조입니다.
> - 힙에는 max-heap 및 min-heap이 있으며 우선 순위 큐(Queue) 구현에 사용됩니다.
> - 메모리 관점에서 힙은 동적 메모리 할당을 위한 메모리 영역이기도 합니다.
> - 따라서 프로그램 실행 중에 필요한 메모리 공간을 동적으로 할당하고 해제하는 데 사용됩니다.

### 📌 완전탐색(Brute Force)
> - 완전탐색은 가능한 모든 경우의 수를 찾아내는 가장 단순한 형태의 알고리즘입니다.
> - 모든 가능성을 탐색하기 때문에 반드시 정답을 찾을 수 있게 됩니다.
> - 하지만 데이터의 양이 많아질수록 시간 복잡도가 증가하기에 비효율적입니다.
> - 그럼에도 알고리즘 구현이 상대적으로 쉽기 때문에 최적화가 거의 없이도 쉽게 접근 가능합니다.
> - 완전탐색의 예시로는 순열 생성, 재귀 호출, 백 트래킹과 같은 것이 있습니다.

### 📌 정렬(Sorting)
> - 정렬이란 데이터를 특정 기준에 따라 순서대로 나열하는 데이터 처리 과정입니다.
> - 정렬 방법은 버블 정렬, 선택 정렬, 삽입 정렬, 퀵 정렬, 병합 정렬 등이 있으며 다양합니다.
> - 정렬은 효율적인 데이터 관리, 검색, 중복 확인, 전처리 단계 등에 이용됩니다.
> - 따라서 정렬을 잘 사용하기 위해서는 시간 및 공간 복잡도 등을 깊이있게 이해해야 됩니다.

<br>
<br>
<br>
