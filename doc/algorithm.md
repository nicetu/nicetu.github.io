# 算法

## 简介

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
