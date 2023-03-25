# 数据结构与算法

## 数据结构

### 栈

栈是一种后进先出（LIFO）的数据结构，可以用数组或链表实现。

#### 栈的图例

栈的插入和删除操作都是在栈顶进行的。下面是一个栈的图例：

![stack example](https://cdn.programiz.com/sites/tutorial2program/files/stack.png)

#### 栈实现

```javascript
class Stack {
  constructor() {
    this.items = [];
  }

  push(element) {
    this.items.push(element);
  }

  pop() {
    return this.items.pop();
  }

  peek() {
    return this.items[this.items.length - 1];
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }

  clear() {
    this.items = [];
  }
}
```

### 队列

队列是一种先进先出（FIFO）的数据结构，可以用数组或链表实现。


![queue example](https://cdn.programiz.com/sites/tutorial2program/files/queue.png)


```javascript
class Queue {
  constructor() {
    this.items = [];
  }

  enqueue(element) {
    this.items.push(element);
  }

  dequeue() {
    return this.items.shift();
  }

  front() {
    return this.items[0];
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }

  clear() {
    this.items = [];
  }
}
```

### 数组

 - 数组是一种线性的数据结构，它由一组连续的内存空间组成，每个内存空间存储一个元素。
 - 数组的长度是固定的，一旦创建就无法改变。
 - 数组可以用于实现栈、队列、堆等数据结构。

![array example](https://cdn.programiz.com/sites/tutorial2program/files/array.png)

 

#### 数组实现

```javascript
class Queue {
  constructor() {
    this.items = [];
  }

  enqueue(element) {
    this.items.push(element);
  }

  dequeue() {
    return this.items.shift();
  }

  front() {
    return this.items[0];
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }

  clear() {
    this.items = [];
  }
}
```

### 链表

链表是一种常见的数据结构，它由一系列节点组成，每个节点包含两个部分：数据和指向下一个节点的指针。链表可以用于实现栈和队列等数据结构。


![linked list example](https://images.xiaozhuanlan.com/photo/2019/3b2c3db521b89f968ec0395d8a77132c.)



#### 链表实现

```javascript
class Node  constructor(element) {
    this.element = element;
    this.next = null;
  }
}

class Queue {
  constructor() {
    this.front = null;
    this.rear = null;
    this.size = 0;
  }

  enqueue(element) {
    const node = new Node(element);
    if (this.isEmpty()) {
      this.front = node;
      this.rear = node;
    } else {
      this.rear.next = node;
      this.rear = node;
    }
    this.size++;
  }

  dequeue() {
    if (this.isEmpty()) {
      return null;
    }
    const node = this.front;
    this.front = node.next;
    if (this.size === 1) {
      this.rear = null;
    }
    this.size--;
    return node.element;
  }

  getFront() {
    if (this.isEmpty()) {
      return null;
    }
    return this.front.element;
  }

  isEmpty() {
    return this.size === 0;
  }

  getSize() {
    return this.size;
  }

  clear() {
    this.front = null;
    this.rear = null;
    this.size = 0;
  }
}
```


#### 单向链表

单向链表是一种链表，每个节点包含一个值和指向下一个节点的指针。链表的第一个节点称为头节点，最后一个节点称为尾节点。链表可以用于实现栈和队列等数据结构。


![linked list example](https://cdn.programiz.com/sites/tutorial2program/files/linked-list.png)


```javascript
class Node {
  constructor(element) {
    this.element = element;
    this.next = null;
  }
}

class LinkedList {
  constructor() {
    this.head = null;
    this.size = 0;
  }

  add(element) {
    const node = new Node(element);
    if (this.head === null) {
      this.head = node;
    } else {
      let current = this.head;
      while (current.next !== null) {
        current = current.next;
      }
      current.next = node;
    }
    this.size++;
  }

  insert(element, index) {
    if (index < 0 || index > this.size) {
      return false;
    }
    const node = new Node(element);
    if (index === 0) {
      node.next = this.head;
      this.head = node;
    } else {
      let current = this.head;
      let previous = null;
      let i = 0;
      while (i < index) {
        previous = current;
        current = current.next;
        i++;
      }
      node.next = current;
      previous.next = node;
    }
    this.size++;
    return true;
  }

  remove(element) {
    let current = this.head;
    let previous = null;
    while (current !== null) {
      if (current.element === element) {
        if (previous === null) {
          this.head = current.next;
        } else {
          previous.next = current.next;
        }
        this.size--;
        return true;
      }
      previous = current;
      current = current.next;
    }
    return false;
  }

  removeAt(index) {
    if (index < 0 || index >= this.size) {
      return null;
    }
    let current = this.head;
    let previous = null;
    let i = 0;
    if (index === 0) {
      this.head = current.next;
    } else {
      while (i < index) {
        previous = current;
        current = current.next;
        i      }
      previous.next = current.next;
    }
    this.size--;
    return current.element;
  }

  indexOf(element) {
    let current = this.head;
    let index = 0;
    while (current !== null) {
      if (current.element === element) {
        return index;
      }
      current = current.next;
      index++;
    }
    return -1;
  }

  isEmpty() {
    return this.size === 0;
  }

  getSize() {
    return this.size;
  }

  getHead() {
    return this.head;
  }

  clear() {
    this.head = null;
    this.size = 0;
  }

  toString() {
    let current = this.head;
    let string = '';
    while (current !== null) {
      string += current.element + (current.next ? ' -> ' : '');
      current = current.next;
    }
    return string;
  }
}

```


#### 双向链表

双向链表是一种链表，每个节点有两个指针，一个指向前一个节点，一个指向后一个节点。双向链表可以从前往后遍历，也可以从后往前遍历。

![doubly linked list example](https://cdn.programiz.com/sites/tutorial2program/files/doubly-linked-list.png)

   

```javascript
class Node {
  constructor(element) {
    this.element = element;
    this.prev = null;
    this.next = null;
  }
}

class DoublyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
    this.size = 0;
  }

  add(element) {
    const node = new Node(element);
    if (this.head === null) {
      this.head = node;
      this.tail = node;
    } else {
      node.prev = this.tail;
      this.tail.next = node;
      this.tail = node;
    }
    this.size++;
  }

  insert(element, index) {
    if (index < 0 || index > this.size) {
      return false;
    }
    const node = new Node(element);
    if (index === 0) {
      if (this.head === null) {
        this.head = node;
        this.tail = node;
      } else {
        node.next = this.head;
        this.head.prev = node;
        this.head = node;
      }
    } else if (index === this.size) {
      node.prev = this.tail;
      this.tail.next = node;
      this.tail = node;
    } else {
      let current = this.head;
      let previous = null;
      let i = 0;
      while (i < index) {
        previous = current;
        current = current.next;
        i++;
      }
      node.prev = previous;
      node.next = current;
      previous.next = node;
      current.prev = node;
    }
    this.size++;
    return true;
  }

  remove(element) {
    let current = this.head;
    while (current !== null) {
      if (current.element === element) {
        if (current === this.head && current === this.tail) {
          this.head = null;
          this.tail = null;
        } else if (current === this.head) {
          this.head = current.next;
          this.head.prev = null;
        } else if (current === this.tail) {
          this.tail = current.prev;
          this.tail.next = null;
        } else {
          current.prev.next = current.next;
          current.next.prev = current.prev;
        }
        this.size--;
        return true;
      }
      current = current.next;
    }
    return false;
  }

  removeAt(index) {
    if (index < 0 || index >= this.size  }
}
```



### 树

树是一种非线性的数据结构，它由一组节点组成，每个节点包含一个值和指向其子节点的指针。树的节点可以有任意数量的子节点，但每个节点只有一个父节点。树的顶部节点称为根节点，没有父节点的节点称为叶子节点。

#### 树的演示

![tree example](https://cdn.programiz.com/sites/tutorial2program/files/tree.png)


#### 二叉树


二叉树是一种特殊的树，每个节点最多只有两个子节点，分别称为左子节点和右子节点。

![binary tree example](https://cdn.programiz.com/sites/tutorial2program/files/binary-tree.png)


```javascript
class Node {
  constructor(element) {
    this.element = element;
    this.left = null;
    this.right = null;
  }
}

class BinaryTree {
  constructor() {
    this.root = null;
  }

  insert(element) {
    const node = new Node(element);
    if (this.root === null) {
      this.root = node;
    } else {
      this.insertNode(this.root, node);
    }
  }

  insertNode(node, newNode) {
    if (newNode.element < node.element) {
      if (node.left === null) {
        node.left = newNode;
      } else {
        this.insertNode(node.left, newNode);
      }
    } else {
      if (node.right === null) {
        node.right = newNode;
      } else {
        this.insertNode(node.right, newNode);
      }
    }
  }

  search(element) {
    return this.searchNode(this.root, element);
  }

  searchNode(node, element) {
    if (node === null) {
      return false;
    }
    if (element < node.element) {
      return this.searchNode(node.left, element);
    } else if (element > node.element) {
      return this.searchNode(node.right, element);
    } else {
      return true;
    }
  }

  remove(element) {
    this.root = this.removeNode(this.root, element);
  }

  removeNode(node, element) {
    if (node === null) {
      return null;
    }
    if (element < node.element) {
      node.left = this.removeNode(node.left, element);
      return node;
    } else if (element > node.element) {
      node.right = this.removeNode(node.right, element);
      return node;
    } else {
      if (node.left === null && node.right === null) {
        node = null;
        return node;
      }
      if (node.left === null) {
        node = node.right;
        return node;
      } else if (node.right === null) {
        node = node.left;
        return node;
      }
      const aux = this.findMinNode(node.right);
      node.element = aux.element;
      node.right = this.removeNode(node.right, aux.element);
      return node;
    }
  }

  findMinNode(node) {
    while (node.left !== null) {
      node = node.left;
    }
    return node;
  }
}
```


### 堆

堆是一种特殊的树形数据结构，它满足以下性质：

- 堆是一棵完全二叉树。
- 堆中每个节点的值都必须大于等于（或小于等于）其子树中每个节点的值。

堆可以用数组实现，数组中的第一个元素为根节点，第二个元素为左子节点，第三个元素为右子节点，以此类推。


![max heap example](https://cdn.programiz.com/sites/tutorial2program/files/MaxHeap.png)



#### 最大堆

最大堆是一种堆，其中每个节点的值都大于等于其子树中每个节点的值。


### 图

图是一种非线性的数据结构，它由一组节点和一组边组成。节点通常表示对象，边表示节点之间的关系。图可以用于表示网络、地图、社交网络等。

![graph example](https://cdn.programiz.com/sites/tutorial2program/files/graph.png)


##### 有向图

有向图是一种图，其中每条边都有一个方向。如果从节点A到节点B有一条有向边，则称节点A指向节点B。

![directed graph example](https://cdn.programiz.com/sites/tutorial2program/files/directed-graph.png)



```javascript
class Graph {
  constructor() {
    this.vertices = [];
    this.adjList = new Map();
  }

  addVertex(v) {
    this.vertices.push(v);
    this.adjList.set(v, []);
  }

  addEdge(v, w) {
    this.adjList.get(v).push(w);
  }

  getVertices() {
    return this.vertices;
  }

  getAdjList() {
    return this.adjList;
  }

  toString() {
    let s = '';
    for (let i = 0; i < this.vertices.length; i++) {
      s += this.vertices[i] + ' -> ';
      const neighbors = this.adjList.get(this.vertices[i]);
      for (let j = 0; j < neighbors.length; j++) {
        s += neighbors[j] + ' ';
      }
      s += '\n';
    }
    return s;
  }
}
```

##### 无向图

无向图是一种图，其中每条边没有方向。如果节点A和节点B之间有一条边，则称节点A和节点B相邻。


![undirected graph example](https://cdn.programiz.com/sites/tutorial2program/files/undirected-graph.png)


```javascript
class Graph {
  constructor() {
    this.vertices = [];
    this.adjList = new Map();
  }

  addVertex(v) {
    this.vertices.push(v);
    this.adjList.set(v, []);
  }

  addEdge(v, w) {
    this.adjList.get(v).push(w);
    this.adjList.get(w).push(v);
  }

  getVertices() {
    return this.vertices;
  }

  getAdjList() {
    return this.adjList;
  }

  toString() {
    let s = '';
    for (let i = 0; i < this.vertices.length; i++) {
      s += this.vertices[i] + ' -> ';
      const neighbors = this.adjList.get(this.vertices[i]);
      for (let j = 0; j < neighbors.length; j++) {
        s += neighbors[j] + ' ';
      }
      s += '\n';
    }
    return s;
  }
}
```


## 算法

算法复杂度是指算法执行所需的时间或空间资源。通常用时间复杂度和空间复杂度来衡量算法的效率。时间复杂度是指算法执行所需的时间资源，通常用大O表示法来表示。空间复杂度是指算法执行所需的空间资源，通常用字节数或位数来表示。计算算法复杂度需要考虑算法的输入规模、算法的执行次数以及算法的执行时间或空间。常见的时间复杂度有常数时间O(1)、对数时间O(log n)、线性时间O(n)、线性对数时间O(n log n)、平方时间O(n^2)、立方时间O(n^3)等。


### 排序算法

排序算法是一种将一组数据按照特定顺序排列的算法。常见的排序算法有冒泡排序、选择排序、插入排序、归并排序、快速排序等。

#### 冒泡排序

冒泡排序是一种简单的排序算法，它重复地遍历要排序的列表，比较相邻的两个元素，如果顺序不对就交换它们的位置。遍历列表的工作是重复地进行直到没有再需要交换的元素。

```javascript
function bubbleSort(arr) {
  const len = arr.length;
  for (let i = 0; i < len - 1; i++) {
    for (let j = 0; j < len - 1 - i; j++) {
      if (arr[j] > arr[j + 1]) {
        const temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
      }
    }
  }
  return arr;
}
```

#### 选择排序

选择排序是一种简单的排序算法，它重复地从未排序的列表中找到最小元素，然后将其放到已排序的列表的末尾。遍历列表的工作是重复地进行直到所有元素都已排序。

```javascript
function selectionSort(arr) {
  const len = arr.length;
  let minIndex, temp;
  for (let i = 0; i < len - 1; i++) {
    minIndex = i;
    for (let j = i + 1; j < len; j++) {
      if (arr[j] < arr[minIndex]) {
        minIndex = j;
      }
    }
    temp = arr[i];
    arr[i] = arr[minIndex];
    arr[minIndex] = temp;
  }
  return arr;
}
```

#### 插入排序

插入排序是一种简单的排序算法，它将一个元素插入到已排序的列表中的正确位置。遍历列表

```javascript
function insertionSort(arr) {
  const len = arr.length;
  let current, j;
  for (let i = 1; i < len; i++) {
    current = arr[i];
    j = i - 1;
    while (j >= 0 && arr[j] > current) {
      arr[j + 1] = arr[j];
      j--;
    }
    arr[j + 1] = current;
  }
  return arr;
}
```

#### 归并排序

归并排序是一种分治算法，它将一个大问题分成多个小问题，然后将小问题的解决方案合并成一个大问题的解决方案。归并排序的基本思想是将待排序的数组分成两个长度相等的子数组，然后对这两个子数组分别进行排序，最后将它们合并成一个有序的数组。

```javascript
function mergeSort(arr) {
  if (arr.length <= 1) {
    return arr;
  }
  const mid = Math.floor(arr.length / 2);
  const leftArr = arr.slice(0, mid);
  const rightArr = arr.slice(mid);
  return merge(mergeSort(leftArr), mergeSort(rightArr));
}

function merge(leftArr, rightArr) {
  const result = [];
  let leftIndex = 0;
  let rightIndex = 0;
  while (leftIndex < leftArr.length && rightIndex < rightArr.length) {
    if (leftArr[leftIndex] < rightArr[rightIndex]) {
      result.push(leftArr[leftIndex]);
      leftIndex++;
    } else {
      result.push(rightArr[rightIndex]);
      rightIndex++;
    }
  }
  return result.concat(leftArr.slice(leftIndex)).concat(rightArr.slice(rightIndex));
}
```

#### 快速排序

快速排序是一种分治算法，它将一个大问题分成多个小问题，然后将小问题的解决方案合并成一个大问题的解决方案。快速排序的基本思想是选择一个基准元素，将数组分成两个子数组，小于基准元素的放在左边，大于基准元素的放在右边，然后对这两个子数组分别进行排序。

```javascript
function quickSort(arr) {
  if (arr.length <= 1) {
    return arr;
  }
  const pivotIndex = Math.floor(arr.length / 2);
  const pivot = arr.splice(pivotIndex, 1)[0];
  const leftArr = [];
  const rightArr = [];
  for (let i = 0; i < arr.length  if (arr[i] < pivot) {
    leftArr.push(arr[i]);
  } else {
    rightArr.push(arr[i]);
  }
}
return quickSort(leftArr).concat([pivot], quickSort(rightArr));
```


```javascript
function quickSort(arr) {
  if (arr.length <= 1) {
    return arr;
  }
  const pivotIndex = Math.floor(arr.length / 2);
  const pivot = arr.splice(pivotIndex, 1)[0];
  const leftArr = [];
  const rightArr = [];
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] < pivot) {
      leftArr.push(arr[i]);
    } else {
      rightArr.push(arr[i]);
    }
  }
  return quickSort(leftArr).concat([pivot], quickSort(rightArr));
}
```


### 搜索算法

搜索算法是一种用于在数据集中查找特定项的算法。常见的搜索算法有线性搜索、二分搜索、深度优先搜索、广度优先搜索等。

#### 线性搜索

线性搜索是一种简单的搜索算法，它遍历整个数据集，查找特定项。如果找到了特定项，则返回其索引；否则返回-1。

```javascript
function linearSearch(arr, item) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === item) {
      return i;
    }
  }
  return -1;
}
```

#### 二分搜索

二分搜索是一种高效的搜索算法，它要求数据集已排序。它重复地将数据集分成两半，直到找到特定项为止。

```javascript
function binarySearch(arr, item) {
  let low = 0;
  let high = arr.length - 1;
  while (low <= high) {
    const mid = Math.floor((low + high) / 2);
    if (arr[mid] === item) {
      return mid;
    } else if (arr[mid] < item) {
      low = mid + 1;
    } else {
      high = mid - 1;
    }
  }
  return -1;
```

#### 深度优先搜索

深度优先搜索是一种用于遍历或搜索树或图的算法。它从根节点或起始节点开始，沿着一条路径遍历到底，直到到达叶子节点或无法继续为止，然后回溯到前一个节点，继续沿着另一条路径遍历，直到遍历完整个树或图。

```javascript
class Graph {
  constructor() {
    this.vertices = [];
    this.adjList = new Map();
  }

  addVertex(v) {
    this.vertices.push(v);
    this.adjList.set(v, []);
  }

  addEdge(v, w) {
    this.adjList.get(v).push(w);
    this.adjList.get(w).push(v);
  }

  getVertices() {
    return this.vertices;
  }

  getAdjList() {
    return this.adjList;
  }

  dfs(startingNode) {
    const visited = {};
    this._dfs(startingNode, visited);
  }

  _dfs(vertex, visited) {
    visited[vertex] = true;
    console.log(vertex);
    const neighbors = this.adjList.get(vertex);
    for (let i = 0; i < neighbors.length; i++) {
      const neighbor = neighbors[i];
      if (!visited[neighbor]) {
        this._dfs(neighbor, visited);
      }
    }
  }
}
```

#### 广度优先搜索

广度优先搜索是一种用于遍历或搜索树或图的算法。它从根节点或起始节点开始，沿着一条路径遍历到底，直到到达叶子节点或无法继续为止，然后回溯到前一个节点，继续沿着另一条路径遍历，直到遍历完整个树或图。

```javascript
class Graph {
  constructor() {
    this.vertices = [];
    this.adjList = new Map();
  }

  addVertex(v) {
    this.vertices.push(v);
    this.adjList.set(v, []);
  }

  addEdge(v, w) {
    this.adjList.get(v).push(w);
    this.adjList.get(w).push(v);
  }

  getVertices() {
    return this.vertices;
  }

  getAdjList() {
    return this.adjList;
  }

  bfs(startingNode) {
    const visited = {};
    const queue = [];
    visited[startingNode] = true;
    queue.push(startingNode);
    while (queue.length !== 0) {
      const vertex = queue.shift();
      console.log(vertex);
      const neighbors = this.adjList.get(vertex);
      for (let i = 0; i < neighbors.length; i++) {
        const neighbor = neighbors[i];
        if (!visited[neighbor]) {
          visited[neighbor] = true;
          queue.push(neighbor);
        }
      }
    }
  }
}
```
