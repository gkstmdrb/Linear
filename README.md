# 선형구조 (Linear)
### 1. 연결 리스트 (Linked list)
### 2. 스택 (Stack)
### 3. 큐 (Queue) <br><br>

## 연결 리스트 (LInked list) <br>

연결 리스트는 데이터 요소들이 노드(node)들로 연결된 자료 구조입니다. <br><br>
각 노드는 데이터 요소를 가지고 있고, 다음 노드를 가리키는 포인터(pointer)를 포함합니다. <br><br>
이러한 구조는 순서가 있는 데이터 요소를 효율적으로 저장하고 조작할 수 있습니다. <br><br>

### 특징
연결 리스트는 늘어선 노드의 중간지점에서도 자료의 추가와 삭제가 O(1)의 시간에 가능하다는 장점을 갖습니다. <br><br>
그러나 배열이나 트리 구조와는 달리 특정 위치의 데이터를 검색해 내는데에는 O(n)의 시간이 걸리는 단점도 갖고 있습니다.

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
