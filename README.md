# 선형구조 (Linear)
### 1. 연결 리스트 (Linked list)
### 2. 스택 (Stack)
### 3. 큐 (Queue) <br><br>

## 연결 리스트 (LInked list) <br>

연결 리스트는 데이터 요소들이 노드(node)들로 연결된 자료 구조입니다. <br><br>
연결 리스트는 자료들을 반드시 연속적으로 배열시키지는 않습니다.<br><br>
각 노드는 데이터 요소를 가지고 있고, 다음 노드를 가리키는 포인터(pointer)를 포함합니다. <br><br>
이러한 구조는 순서가 있는 데이터 요소를 효율적으로 저장하고 조작할 수 있습니다. <br><br>

### 특징
링크 값을 변화시키는 것 만으로 노드의 삽입 삭제가 용이하고, <br><br>
연결 리스트는 늘어선 노드의 중간지점에서도 자료의 추가와 삭제가 O(1)의 시간에 가능하다는 장점을 갖습니다. <br><br>
그러나 배열이나 트리 구조와는 달리 특정 위치의 데이터를 검색해 내는데에는 O(n)의 시간이 걸리는 단점도 갖고 있습니다. <br><br>
또, 연결을 위한 링크(포인터) 부분이 필요하기 때문에 순차 리스트에 비해 기억공간 이용 효율이 좋지 않습니다. 

### 자바코드
``` java
public class linkedlist {
	// 첫번째 노드를 가리키는 필드
	private Node head;
	private Node tail;
	private int size = 0;
		// 데이터가 저장될 필드
		private class Node {
		// 다음 노드를 가리키는 필드
		private Object data;
		private Node next;
		public Node (Object input) {
			this.data = input;
			this.next = null;
		}
		// 노드의 내용을 쉽게 출력해서 확인해볼 수 있는 기능
		public String toString() {
			return String.valueOf(this.data);
		}
	}
	
	public void addFirst (Object input) {
		// 노드를 생성합니다.
		Node temp = new Node(input);
		// 새로운 노드의 다음 노드로 헤드를 지정합니다.
		temp.next = head;
		// 헤드로 새로운 노드를 지정합니다.
		head = temp;
		size++;
		if(head.next == null) {
			tail = head;
		}
	}
	
	public void addLast(Object input) {
		// 노드 생성
		Node temp = new Node(input);
		//리스트의 노드가 없다면 첫번째 노드를 추가하는 메소드를 사용합니다.
		if(size == 0) {
			addFirst(input);
		}	else  {
			// 마지막 노드의 다음 노드로 생성한 노드를 지정합니다.
			tail.next = temp;
			// 마지막 노드를 갱신합니다.
			tail = temp;
			// 엘리먼트의 개수를 1 증가시킵니다.
			size++;
		}
		
	}
	
}
```
### Linked list main
``` java
public class linkedlistmain {
	
	public static void main (String [] args) {
		linkedlist numbers = new linkedlist();
		numbers.addFirst(12);
		numbers.addFirst(10);
		numbers.addFirst(1);
		numbers.addLast(4);
		
		
	}
}
```
<br><br><br><br><br>
## 스택 (Stack)
스택은 제한적으로 접근할 수 있는 나열 구조입니다. <br><br>
접근 방법은 언제나 목록의 끝에서만 일어납니다. <br><br>

### 특징
스택의 가장 큰 특징은 후입선출(LIFO) 입니다. <br><br> 
가장 최근에 들어온 데이터가 가장 먼저 나간다는 의미입니다. <br><br>
![image](https://user-images.githubusercontent.com/114748816/226506815-1c939186-8428-4cde-95c2-619c74489e11.png) <br><br>

### 자바코드

```java
public class Stack {
	private int[] stk;		// 스택용 배열
	private int capacity;	// 스택의 크기
	private int ptr;		// 스택 포인터
	
	// 실행시 예외: 스택이 비어있음
	public class EmptyIntStackException extends RuntimeException {
		public EmptyIntStackException() { }
	}
	
	// 실행시 예외: 스택이 가득 참
	public class OverflowIntStackException extends RuntimeException {
		public OverflowIntStackException() { }
	}
	
	// 생성자
	public Stack(int maxlen) {
		ptr = 0;
		capacity = maxlen;
		try {
			stk = new int[capacity];
		}	catch (OutOfMemoryError e) {
			capacity = 0;
		}
	}
	
	// 스택에 x를 푸시
	public int push (int x) throws OverflowIntStackException {
		if (ptr >= capacity)
			throw new OverflowIntStackException();
		return stk[ptr++] = x;
	}
	
	// 스택에서 데이터를 팝(정상에 있는 데이터를 꺼냄)
	public int pop() throws EmptyIntStackException {
		if (ptr == 0) 
			throw new EmptyIntStackException();
		return stk[--ptr];
	}
}
```

## 큐 (Queue)
큐는 먼저 집어 넣은 데이터가 먼저 나오는 FIFO(First In First Out)구조로 저장하는 형식을 말합니다.

### 특징
들어간 순서 그대로 나오는 것이 특징이고, <br>
큐에 가장 먼저 들어온 자료가 가장 먼저 삭제됩니다. <br><br>

 컴퓨터 시스템의 작업 스케줄에서 특별한 우선 순위가 없는 경우<br>
 먼저 들어온 프로세스가 먼저 처리됩니다.  
 
 ### 자바코드
 ```java
 public class Queue {
	
	private int [] que;		// 큐용 배열
	private int capacity;	// 큐의 크기
	private int front;		// 
	private int rear;
	private int num;
	
	// 실행시 예외: 큐가 비어있음
	public class EmptyIntQueueException extends RuntimeException {
		public EmptyIntQueueException() {}
	}
	
	// 실행시 예외: 큐가 가득참
	public class OverflowIntQueueException extends RuntimeException {
		public OverflowIntQueueException() {}
	}
	
	// 생성자 (constructor)
	public Queue(int maxlen) {
		num = front = rear = 0;
		capacity = maxlen;
		try {
			que = new int[capacity];				// 큐 본체용 배열을 생성
			}	catch (OutOfMemoryError e) {		// 생성할 수 없음
				capacity = 0;
			}
	}
	
	// 큐에 데이터를 인큐
	public int enque(int x) throws OverflowIntQueueException {
		if (num >= capacity) 
			throw new OverflowIntQueueException();		// 큐가 가득참
		que[rear++] = x;
		num++;
		if(rear == capacity)
			rear = 0;
	}
	
	// 큐에서 데이터를 디큐
	public int deque() throws EmptyIntQueueException {
		if (num <= 0)
			throw new EmptyIntQueueException();			// 큐가 비어있음
		int x = que[front++];
		num--;
		if (front == capacity)
			front = 0;
		return x;
	}
	
	// 큐에서 데이터를 피크(프런트 데이터 들여다봄)
}
```
