---
{"dg-publish":true,"permalink":"/obsidian///fds//hw/","created":"2024-04-10T00:02:19.258+08:00","updated":"2024-09-08T15:25:05.374+08:00"}
---

33333333333333333# HW1
# 计算时间复杂度
1. 根据递归![Pasted image 20240423184255.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240423184255.png)
2. 
# HW4
## 节点数与孩子树
![Pasted image 20240410010528.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410010528.png)
1. 思路
	
# HW5
## BST节点的删除
1. 思路：左子树找最大/右子树找最小来代替
2. 例题：![Pasted image 20240410004237.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410004237.png)
3. 如果是将有子节点的节点去代替根节点，这个叶子直接跟在原节点的父节点
## 决策树
1. 题目![Pasted image 20240410004741.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410004741.png)
	1. ANS：A
	2. 解读：树的形状需要<mark style="background: #FFF3A3A6;">保持</mark>左子树节点一直<mark style="background: #FFF3A3A6;">>=</mark>右子树（或者相反）
# HW6
## 线性时间构造MinHeap
1. 思路
>从$n$/2-1的节点索引开始，递归地递减上浮节点(root:1)
2. 题目：![Pasted image 20240410001037.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410001037.png)
3. 解答
	1. 代码[[obsidian/个人知识库/大一/FDS/数据结构/4.堆的课堂笔记#⑤线性时间构造MinHeap\|4.堆的课堂笔记#⑤线性时间构造MinHeap]]
	2. 自然语言
		1. 线性构建：
			1. 从非叶节点开始，只关注当前节点是否比子节点大
			2. 如果子节点更小则交换，并且递归调用子节点（下沉到底）
			3. 直至根节点被调用
		2. 插入元素：
			1. 从尾部初始化
			2. 与根节点比较，决定是否上浮
			3. 依次递归
		>注意这两者不同

## d-堆的索引
### 题目：
![Pasted image 20240410003035.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410003035.png)
## 前序与中序构建唯一二叉树
### 原理
1. 前序：根左右
2. 中序：左根右
3. 所以先从前序的第一个找到根，从中序将树分为左右子树
4. 递归完成上述
## 函数：上浮与下沉
```c
void PercolateUp( int p, PriorityQueue H )
{
    if(p<1 || p > H->Size){
        //printf("Invalid input!n");
        return;
    }
    for(int i=p;i>0;){
        int parent = i/2;
        if(H->Elements[parent] > H->Elements[i]){
            int tmp = H->Elements[parent] ;
            H->Elements[parent] = H->Elements[i];
            H->Elements[i] = tmp;
            i = parent;
        }
        else
            break;
    }
    return;
}

void PercolateDown( int p, PriorityQueue H )
{
    if(p < 1 || p>H->Size){
        //printf("Invalid input!\n");
        return;
    }
    int child;
    for(child = 2*p;child <= H->Size;child = 2*p){
        if(child+1 < H->Size && H->Elements[child+1] < H->Elements[child])
            child+=1;
        if(H->Elements[p] > H->Elements[child]){
            int tmp = H->Elements[p];
            H->Elements[p] = H->Elements[child];
            H->Elements[child] = tmp;
            p = child;
        }
        else
            break;
    }
    return;
}
```
## 编程：CBT+BST的层序输出
```c
#include <stdio.h>
#include <stdlib.h>

// 定义二叉树节点的结构体
typedef struct TreeNode {
    int val; // 节点值
    struct TreeNode* left; // 左子节点指针
    struct TreeNode* right; // 右子节点指针
} TreeNode;

// 定义队列结构体，用于层序遍历
typedef struct {
    TreeNode** elements; // 存储队列元素的数组
    int front; // 队列的头指针
    int rear; // 队列的尾指针
    int size; // 队列当前的元素数量
    int capacity; // 队列的最大容量
} Queue;

// 函数原型声明
TreeNode* CreatNode(int val);
void BubbleSort(int* arr, int n);
TreeNode** BuildCBT(int* arr, int n);
void InorderFillValues(TreeNode* node, int* arr, int* index);
void LevelOrderTraversal(TreeNode* root, int n);
Queue* CreatQueue(int capacity);
void Enqueue(Queue* q, TreeNode* node);
TreeNode* Dequeue(Queue* q);
void FreeQueue(Queue* q);

int main() {
    int n; // 存储用户输入的节点数
    scanf("%d", &n);
    int* arr = (int*)malloc(n * sizeof(int)); // 动态分配数组存储节点值
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]); // 读取节点值
    }

    BubbleSort(arr, n); // 对节点值进行冒泡排序

    TreeNode** nodes = BuildCBT(arr, n); // 构建完全二叉树框架
    int index = 0;
    InorderFillValues(nodes[0], arr, &index); // 中序遍历填充树的值

    LevelOrderTraversal(nodes[0], n); // 执行层序遍历并打印结果

    // 释放内存资源
    free(arr);
    free(nodes);
    return 0;
}

// 创建一个新的TreeNode节点
TreeNode* CreatNode(int val) {
    TreeNode* node = (TreeNode*)malloc(sizeof(TreeNode)); // 分配内存
    node->val = val; // 设置节点值
    node->left = NULL; // 初始化左子节点为空
    node->right = NULL; // 初始化右子节点为空
    return node;
}

// 使用冒泡排序算法对数组进行排序
void BubbleSort(int* arr, int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp; // 交换元素
            }
        }
    }
}

// 构建完全二叉树的框架，不考虑节点具体值
TreeNode** BuildCBT(int* arr, int n) {
    TreeNode** nodes = (TreeNode**)malloc(n * sizeof(TreeNode*)); // 分配节点指针数组
    for (int i = 0; i < n; i++) {
        nodes[i] = CreatNode(0); // 创建节点，初始值为0
    }
    for (int i = 0; i < n; i++) {
        if (2 * i + 1 < n) nodes[i]->left = nodes[2 * i + 1]; // 设置左子节点
        if (2 * i + 2 < n) nodes[i]->right = nodes[2 * i + 2]; // 设置右子节点
    }
    return nodes;
}

// 通过中序遍历的方式填充树的值
void InorderFillValues(TreeNode* node, int* arr, int* index) {
    if (node == NULL) return; // 如果节点为空，则返回
    InorderFillValues(node->left, arr, index); // 递归填充左子树
    node->val = arr[(*index)++]; // 设置节点值，并移动数组索引
    InorderFillValues(node->right, arr, index); // 递归填充右子树
}

// 创建一个队列，用于层序遍历
Queue* CreatQueue(int capacity) {
    Queue* q = (Queue*)malloc(sizeof(Queue)); // 分配队列结构体内存
    q->elements = (TreeNode**)malloc(capacity * sizeof(TreeNode*)); // 分配队列元素数组内存
    q->front = 0;
    q->rear = 0;
    q->size = 0;
    q->capacity = capacity;
    return q;
}

// 向队列中添加一个元素
void Enqueue(Queue* q, TreeNode* node) {
    if (q->size == q->capacity) return; // 如果队列已满，则不添加
    q->elements[q->rear] = node; // 将节点添加到队尾
    q->rear = (q->rear + 1) % q->capacity; // 循环队列更新队尾位置
    q->size++; // 队列大小增加
}

// 从队列中取出一个元素
TreeNode* Dequeue(Queue* q) {
    if (q->size == 0) return NULL; // 如果队列为空，则返回NULL
    TreeNode* node = q->elements[q->front]; // 取出队头元素
    q->front = (q->front + 1) % q->capacity; // 循环队列更新队头位置
    q->size--; // 队列大小减少
    return node;
}

// 层序遍历二叉树并打印节点值
void LevelOrderTraversal(TreeNode* root, int n) {
    int flag = 1;
    Queue* q = CreatQueue(n); // 创建足够大的队列
    Enqueue(q, root); // 将根节点加入队列
    while (q->size > 0) { // 当队列不为空时
        TreeNode* node = Dequeue(q); // 从队列中取出一个节点
        if(flag){
            printf("%d", node->val); // 第一次打印节点值
            flag = 0;
        }else{
             printf(" %d", node->val); // 后续打印打印节点值
        }
        if (node->left) Enqueue(q, node->left); // 如果左子节点存在，加入队列
        if (node->right) Enqueue(q, node->right); // 如果右子节点存在，加入队列
    }
    printf("\n");
    FreeQueue(q); // 释放队列内存
}

// 释放队列内存
void FreeQueue(Queue* q) {
    free(q->elements); // 释放队列元素数组内存
    free(q); // 释放队列结构体内存
}

```
# HW7
## 编程
1. 要求
	1. 第一行给出n表示存在n个节点
	2. 之后每行给出的格式举例如下
		1. I 2 5   表示2,5并
		2. C 1 4   表示检查1 4是否在同一个集合
	3. 额外的输出：
		1. 检查最后有几个独立的集合
2. code:
```c
#include<stdio.h>
#include<stdlib.h>
int Find(int* arr,int x);
void UnionBySize(int x,int y,int* arr);

int main()
{
    int n,x,y,countSet=0;
    char operator;
    scanf("%d",&n);
    int* parent=(int*)malloc(sizeof(int)*n);
    for(int i=0;i<n;i++){
        parent[i] = -1;
    }
    scanf(" %c",&operator);
    while(operator != 'S'){
        scanf("%d %d",&x,&y);
        switch(operator){
            case 'I':
                if(Find(parent,x) != Find(parent,y))
                UnionBySize(x,y,parent);
                break;
            case 'C':
                if(Find(parent,x) == Find(parent,y)){
                    printf("yes\n");
                }else
                    printf("no\n");
                break;
                }
        scanf(" %c",&operator);
    }
    for(int i=0;i<n;i++){
        if(parent[i] < 0)
            countSet+=1;}
    if(countSet == 1){
        printf("The network is connected.\n");
    }else{
        printf("There are %d components.\n",countSet);
    }
}

int Find(int* arr,int x)
{
    if(arr[x]<0)
        return x;
    else
        return arr[x] = Find(arr,arr[x]);
}

void UnionBySize(int x,int y,int* arr)
{
    int root_x = Find(arr,x);
    int root_y = Find(arr,y);
    if(root_x != root_y){
        //如果x所在树的节点数更多，将y插入x
        if(arr[root_x] < arr[root_y]){
            arr[root_x]+=arr[root_y];//更新x所在树的节点数
            arr[root_y] = root_x;
        }else{
            arr[root_y]+=arr[root_x];//更新y所在树的节点数
            arr[root_x] = root_y;
        }
    }
}
```
# HW8
## 非连通G的E->V
1. 题目：![Pasted image 20240419194641.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419194641.png)
2. 答案：`10`
3. 分析：
	1. 8个顶点最多有7x8/2=28条边，9个顶点最多有8x9/2=36条边
	2. 取9个顶点，但是用到35条边，然后再令取一个孤立的顶点
	3. 这样就满足一共有35条边，且不连通
## 模拟拓扑算法
1. 题目![Pasted image 20240419201440.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419201440.png)
2. 关键：特别注意，只有<mark style="background: #FFF3A3A6;">入度为0时才会入队！</mark>
## (函数)根据给定的图判断拓扑排序是否合理
1. 思路：
	我们可以**直接**对图进行拓扑排序，利用回溯等手段得到所有可能的拓扑排序的结果；
	然而，存在一种<mark style="background: #FFF3A3A6;">更加高效</mark>的方式——根据图构建一个存储入度的数组（如果还不存在的话），然后遍历排序的结果，每次都检查顶点的入度是否为0：如果是，则将这个顶点所指向的顶点的入度--；否则，返回false.
2. 简化思路的代码实现：
```c
bool IsTopSeq(LGraph Graph, Vertex Seq[]) {
    // 初始化入度数组，数组大小为 MaxVertexNum + 1 以直接使用顶点编号
    int inDegrees[MaxVertexNum + 1] = {0}; 

    // 计算所有顶点的入度
    for (Vertex v = 0; v < Graph->Nv; v++) {
        PtrToAdjVNode currentNode = Graph->G[v].FirstEdge;
        // 遍历顶点v的邻接表，更新所有邻接顶点的入度
        while (currentNode != NULL) {
            inDegrees[currentNode->AdjV + 1]++; // 调整顶点索引以适配从1开始的编号
            currentNode = currentNode->Next;
        }
    }
    
    // 检查序列是否为有效的拓扑排序
    for (int i = 0; i < Graph->Nv; i++) {
        Vertex currentVertex = Seq[i];
        if (inDegrees[currentVertex] != 0) {
            // 如果当前顶点的入度不为0，则序列不是有效的拓扑排序
            return false;
        }

        // 减少当前顶点指向的所有顶点的入度
        PtrToAdjVNode currentNode = Graph->G[currentVertex - 1].FirstEdge;
        while (currentNode != NULL) {
            inDegrees[currentNode->AdjV + 1]--;
            currentNode = currentNode->Next;
        }
    }
    return true;
}

```
## (编程)检查哈密顿回路
1. 问题分解
	1. 由给出的信息构建图结构
		1. 无向图
	2. 由给出的数据判断是否形成了圈
		1. 检查输入：
			1. 经过其他所有顶点且只经过一次；
			2. 起始点相同
		2. 检查下一个顶点是否在上一个顶点的链表元素里
2. 代码展示
```c
#include<stdio.h>
#include<stdlib.h>

# define maxSize 200

typedef struct graphNode{
    int position;
    struct graphNode* next;
}graphNode;

typedef struct Graph{
    int numVertex;
    graphNode* adjList[maxSize];
}Graph;

void InitializeGraph(Graph* G,int size);//根据顶点数初始化图
void addEdges(Graph* G,int vertex1,int vertex2);//构建无向图
int checkOnce(int* arr,int size);//判断除了最后一个元素，所有元素是否仅出现了一次
void checkHamiltonCycle(Graph* G,int* tmpArray,int size);//判断数组中的元素是否满足哈密顿回路
int hasEdge(Graph* G,int former,int latter);//判断顶点之间是否有边

int main()
{
    int vertexSize,edge,vertex1,vertex2;
    scanf("%d %d",&vertexSize,&edge);
    Graph G;
    InitializeGraph(&G,vertexSize);
    
    //根据给出的边数edge读取信息构建adjList
    for(int i=0 ;i<edge; i++){
        scanf("%d %d",&vertex1,&vertex2);
        addEdges(&G,vertex1-1,vertex2-1);
    }
    
    int testVertex,numOfInput;
    scanf("%d",&numOfInput);
    for(int i=0; i<numOfInput; i++){
        scanf("%d",&testVertex);
        int* tmpArray = (int*)malloc(sizeof(int)*testVertex);
        for(int j=0; j<testVertex; j++){
            scanf("%d",&tmpArray[j]);
            tmpArray[j]--;
        }
        if(testVertex != vertexSize+1 || tmpArray[0] != tmpArray[vertexSize] || !checkOnce(tmpArray,testVertex)){
            printf("NO\n");
            continue;
        }
        checkHamiltonCycle(&G,tmpArray,testVertex);
    }
}



void InitializeGraph(Graph* G,int size){
    G->numVertex = size;
    for(int i=0; i<size; i++)
        G->adjList[i] = NULL;
}

void addEdges(Graph* G,int vertex1,int vertex2){
    graphNode* newNode = (graphNode*)malloc(sizeof(graphNode));
    newNode->position = vertex2;
    newNode->next = G->adjList[vertex1];
    G->adjList[vertex1] = newNode;
    
    //为无向图，因此为双方都加边
    newNode = (graphNode*)malloc(sizeof(graphNode));
    newNode->position = vertex1;
    newNode->next = G->adjList[vertex2];
    G->adjList[vertex2] = newNode;
}
//通过对前一个顶点的链表进行遍历，直至找到后一个顶点或者为NULL
void checkHamiltonCycle(Graph* G,int* tmpArray,int size){
    int former,latter;
    for(int i=0; i<size-1; i++){
        former = tmpArray[i];
        latter = tmpArray[i+1];
        if(hasEdge(G,former,latter) == 0){
            printf("NO\n");
            return;
        }
    }
    printf("YES\n");
    return;
}

int hasEdge(Graph* G,int former,int latter){
    graphNode* tmp = G->adjList[former];
    while(tmp!=NULL){
        if(tmp->position == latter)
            return 1;
        tmp = tmp->next;
    }
    return 0;
}

int checkOnce(int* arr,int size){
    int count[maxSize]={0};
    for(int i=1; i<size; i++){
        count[arr[i]] = 1;
    }
    for(int i=0; i<size-1; i++){
        if(count[i] == 0)
            return 0;
    }
    return 1;
}

```
# HW9
## 最短路径因权值变化的影响
- 原本的最短路径P，在`所有edge的权值均+2`之后不一定依旧为最短路径
- 解释：考虑P经历的边数较多的情况。此时对P的影响较大
## 找到Dijkstra算法的标记路径
- 含义：模拟算法的贪心性质（每次选择Dis最小的点），进行标记
- 题目：[[obsidian/个人知识库/大一/FDS/数据结构/7.图论#Dijkstra 算法\|7.图论#Dijkstra 算法#模拟实现：]]
	✅2-4-3-6-5-7
# HW10

## 卫星站
```c
#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<limits.h>

#define numV 500


typedef struct edgeNode {
	int adjVertex;
	int weight;
	struct edgeNode* next;
}edgeNode;



typedef struct {
	int vertex;
	edgeNode* firstEdge;
}vertexNode;

typedef struct {
	int numVertex;
	int numEdge;
	vertexNode* adjList;
}Graph;


//function
int maxFlowCheck(Graph* G, int src, int dst);
int BFS(Graph* G, int src, int dst, int* path);
void updateGraph(Graph* G, int* path, int src);
int findMinFlow(Graph* G, int* path, int src);
int FindWeight(int start, int end, Graph* G);
void updateEdge(int start, int end, Graph* G, int minFlow);
int checkId(char arr[numV][4], char* str, int* count);//题目说最多有500条边，因此最多有1000个顶点


Graph* initialGraph(int numVertex) {
	Graph* G = (Graph*)malloc(sizeof(Graph));
	G->numVertex = numVertex;
	G->adjList = (vertexNode*)malloc(sizeof(vertexNode) * (numVertex + 1));
	for (int i = 0; i < numVertex; i++)
		G->adjList[i].firstEdge = NULL;
	return G;
}


int maxFlowCheck(Graph* G, int src, int dst) {
	
	//printf("Checking flow from %d to %d\n", src, dst);
	
	//存储是否遍历过的known数组以及路径path
	//这是因为在每次更新边的关系之后，known以及path需要重置，因此不可以与图中的vertex绑定

	int maxFlow = 0;
	int path[numV];//为了能够让调用的BFS返回,在BFS外部创建指针，并用指针作为参数
	for (int i = 0; i < numV; i++)
		path[i] = -1;

	while (BFS(G, src, dst, path)) {
		//注意path的初始化与更新
		//更新流量图G
		// 找到从 dst 到 src 的最小容量边
		int minFlow = findMinFlow(G, path, dst);  // 从 dst 开始回溯到 src
		if (minFlow == 0) break;  // 如果没有路径或者最小流为 0，则终止循环
		// 更新网络中的流量
		updateGraph(G, path, dst);
		maxFlow += minFlow;
		for (int i = 0; i < numV; i++)
			path[i] = -1;  // 重置 path 数组为 -1
	}
	return maxFlow;
}

int BFS(Graph* G, int src, int dst, int* path) {
	int queue[numV];
	int visited[numV] = { 0 }; // 访问数组初始化为未访问
	int front = 0, rear = 0; // 队列的头和尾指针

	queue[rear++] = src; // 将源点入队
	visited[src] = 1; // 标记源点为已访问
	path[src] = -1; // 源点没有父节点

	while (front != rear) {
		int current = queue[front++]; // 出队一个元素
		if (current == dst)
			return 1; // 如果当前节点是目标节点，返回成功
		edgeNode* tmp = G->adjList[current].firstEdge; // 获取当前节点的边列表
		while (tmp != NULL) {
			int adjver = tmp->adjVertex; // 获取邻接顶点
			// 如果邻接顶点未被访问
			if (!visited[adjver] && tmp->weight > 0) {
				visited[adjver] = 1; // 标记为已访问
				path[adjver] = current; // 记录邻接顶点的父节点为当前节点
				queue[rear++] = adjver; // 将邻接顶点入队
			}
			tmp = tmp->next; // 访问下一条边
		}
	}
	return 0; // 如果队列为空，说明没有找到路径，返回失败
}



void updateGraph(Graph* G, int* path, int dst) {
	int minFlow = findMinFlow(G, path, dst);
	for (int v = dst; path[v]!= -1; v = path[v]) {
		int u = path[v];
		updateEdge(u,v, G, minFlow);
	}
}

//找到增广路径中的最小流量
//注意，应当从dst出发
int findMinFlow(Graph* G, int* path, int dst) {
	if (path[dst] == -1) {
		return 0;  // 如果目标节点没有前驱，说明没有找到路径
	}
	int minFlow = INT_MAX; // 设置一个非常大的初始值
	for (int v = dst; path[v] != -1; v = path[v]) {
		int u = path[v];
		int currentFlow = FindWeight(u, v, G);
		if (currentFlow < minFlow) {
			minFlow = currentFlow; // 更新最小流量
		}
	}
	return minFlow;
}


//由给出的顶点获得之间的边的权值
int FindWeight(int start, int end, Graph* G) {
	edgeNode* tmp = G->adjList[start].firstEdge;
	while (tmp!= NULL && tmp->adjVertex != end)
		tmp = tmp->next;
	if (tmp == NULL)
		return -1;
	return tmp->weight;
}


//更新流量图，包括为正向减值和负向加值
void updateEdge(int start, int end, Graph* G, int minFlow) {
	edgeNode* tmp = G->adjList[start].firstEdge;
	while (tmp!= NULL && tmp->adjVertex != end)
		tmp = tmp->next;
	if (tmp  != NULL)
		tmp->weight -= minFlow;

	//添加反方向的边
	tmp = G->adjList[end].firstEdge;
	while (tmp != NULL && tmp->adjVertex != start)
		tmp = tmp->next;
	if (tmp == NULL) {
		edgeNode* newNode = (edgeNode*)malloc(sizeof(edgeNode));
		newNode->adjVertex = start;
		newNode->next = G->adjList[end].firstEdge;
		newNode->weight = minFlow;
		G->adjList[end].firstEdge = newNode;
	}
	else {
		tmp->weight += minFlow;
	}

}

int checkId(char arr[numV][4], char* str, int* count) {
	for (int i = 0; i < *count; i++) {
		if (strcmp(arr[i], str) == 0)
			return i;
	}
	strcpy(arr[*count], str);
	(*count)++;
	return (*count - 1);
}

//得到最大流
int main() {
	int maxFlow,u,v,numEdge,weight,count;
	char* start = (char*)malloc(sizeof(char) * 4);
	char* end = (char*)malloc(sizeof(char) * 4);
	char vertexArr[numV][4];
	Graph* G = initialGraph(numV);

	scanf("%s %s %d", start, end,&numEdge);
	//构建以字符串指针为元素的数组 char** vertexArr,
	// 每次检查start与end是否在vertexArr当中，若否，vertexArr[k++]标记为对应的字符串
	//每次先遍历字符串数组（i记录索引)，如果找到就返回i作为对应字符串在图中的顶点索引
	strcpy(vertexArr[1], start);
	strcpy(vertexArr[2], end);
	count = 3;
	for (int i = 0; i < numEdge; i++) {
		scanf("%s %s %d", start, end,&weight);
		u = checkId(vertexArr, start,&count);
		v = checkId(vertexArr,end,&count);
		edgeNode* newNode = (edgeNode*)malloc(sizeof(edgeNode));

		newNode->adjVertex = v;
		newNode->weight = weight;
		newNode->next = G->adjList[u].firstEdge;
		G->adjList[u].firstEdge = newNode;
	}
	//由给出的图的信息构建图
	//先给出起点，终点对应的字符串，以及边数numEdge
	//接着给出numEdge行，每行都包括起始点和weight
		//利用哈希表将字符串名称映射为整数索引
		//每次映射的值++



	/*for (int i = 1; i < count; i++) {
		edgeNode* tmp = G->adjList[i].firstEdge;
		while (tmp != NULL) {
			printf("%d", tmp->adjVertex);
			tmp = tmp->next;
		}
		printf("\n");
	}
	printf("src is %s\n", vertexArr[1]);
	for(int i=1;i<count;i++)
	printf("%s\n", vertexArr[i]);
	*/
	maxFlow = maxFlowCheck(G, 1, 2);
	//最大流算法
		//利用BFS寻找增广路径
		//更新流量图与最大流量信息
		//返回最大流	
	if (maxFlow == 0)
		return 0;
	printf("%d\n", maxFlow);
}
```
# Midterm
## 补充
1. <mark style="background: #ADCCFFA6;">偏序关系</mark>：满足自反、<mark style="background: #FFF3A3A6;">反对称</mark>、传递的关系
	1. $R(x,y)与R(y,x)$不能同时满足
2. 在一个有向图中存在环的情况下，一定<mark style="background: #FFF3A3A6;">不存在拓扑排序</mark>
	- 是有向无环图$DAG$的顶点的线性排序，要求$u\rightarrow v$的严格方向性
	- 存在环时，方向性无法得以满足
	- 因此，环的存在违背了拓扑排序的基本要求
	- （但是，可以说用拓扑排序来检验是否存在环，只是无法输出全部顶点）
## 并查集的路径压缩
- 发生时间：Find($x$)
- 要点：<mark style="background: #FFB86CA6;">并非完全压缩</mark>！
	- 根据代码可知[[obsidian/个人知识库/大一/FDS/数据结构/6.并查集 The Disjoint Set\|6.并查集 The Disjoint Set]]
	- 是从x开始寻找该集合的根节点
	- 最后将该过程当中遍历到的子节点都指向根节点
	- 因此，不<mark style="background: #FFF3A3A6;">包括x的子节点与别的支路的节点</mark>
## 线性与非线性
- 一般对~的讨论是从<mark style="background: #FFF3A3A6;">逻辑结构</mark>层面进行的，而非物理存储结构
- ❓![Pasted image 20240429162620.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240429162620.png)
	✅ <mark style="background: #FF5582A6;">C</mark> ： 字符串也具有一一对应的线性关系，而完全二叉树则具有层次性与分支结构，因此为non-linear
## 完全二叉树的叶子节点数
- 不要忽略<mark style="background: #FFF3A3A6;">倒数第二层</mark>的叶子！
- 公式
	- 根节点为第0层，则**前h层**的节点总数为$2^{h+1}-1$个
	- **第h层**的节点数为$2^h$个
- ❓![Pasted image 20240429163242.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240429163242.png)
	- ✅ <mark style="background: #FF5582A6;">B</mark> ：先算出有9层满，然后计算10层的数目，接着计算第10层所影响的父节点数，回到第9层算出剩下的叶子数。最后将两部分的叶子节点数增加。
- 举例✅![a6a627a2a3dd9bcb6538967fd7c6a25.jpg](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/a6a627a2a3dd9bcb6538967fd7c6a25.jpg)
## 给出V与E求最大连通数
- 要点：
	- 要尽可能得到单独的顶点（每个顶点就是一个连通分量），此时能确保得到最大的连通数
	- 因此，要尽可能将边快速用完
	- 显然，1E对2V的效率较低，可以让N个点组成的系统中两两相连，此时最多消耗$\frac {N(N-1)} 2$条边
	- 然后取剩下的顶点单独作为连通分量，最后加1
- ❓![Pasted image 20240429164003.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240429164003.png)
	✅ <mark style="background: #FF5582A6;">C</mark> : 先取N=7用完17条边，剩余43个顶点。因此，43+1=44.
# HW11
## 判断题：
1. ❓After the first run of Insertion Sort, it is possible that no element is placed in its final position.
	1. 意思是：在第一次插入排序结束后，是否可能没有一个元素在正确的位置上
	2. 理解了题目的意思之后，不难发现这个说法是正确的
2. ❓Apply DFS to a directed acyclic graph, and output the vertex before the end of each recursion. The output sequence will be:
	1. ✅reversely topologically sorted
	2. 意思是：在执行DFS的递归调用时，递归将结束时开始输出当前的顶点值并回溯（而非标记之后直接输出）。因此是逆序的拓扑排序
## 编程：强连通分量
### Tarjan's
```c
void StronglyConnectedComponents(Graph G, void (*visit)(Vertex V))
{
    int count = 0, rear = 0;
    Vertex stack[MaxVertices];
    int disc[MaxVertices];
    int low[MaxVertices];
    int inStack[MaxVertices] = {0};  // 记录哪些顶点在栈中

    // 初始化 disc 和 low 数组
    for (int i = 0; i < MaxVertices; i++) {
        disc[i] = -1;
        low[i] = -1;
    }

    // 深度优先搜索函数
    void DFS(Vertex u) {
        // 初始化顶点 u 的 discovery time 和 low 值
        disc[u] = low[u] = count++;
        // 将顶点 u 入栈，并标记为在栈中
        stack[rear++] = u;
        inStack[u] = 1;

        // 遍历顶点 u 的所有邻接顶点 v
        PtrToVNode tmp = G->Array[u];
        while (tmp != NULL) {
            Vertex v = tmp->Vert;
            if (disc[v] == -1) {  // 如果顶点 v 未被访问
                DFS(v);  // 递归访问顶点 v
                low[u] = (low[u] < low[v]) ? low[u] : low[v];  // 更新 low[u]
            } else if (inStack[v]) {  // 如果顶点 v 在栈中
                low[u] = (low[u] < disc[v]) ? low[u] : disc[v];  // 更新 low[u]
            }
            tmp = tmp->Next;
        }

        // 如果顶点 u 是强连通分量的根
        if (disc[u] == low[u]) {
            Vertex w;
            // 从栈中弹出顶点，直到顶点 u
            do {
                w = stack[--rear];
                inStack[w] = 0;
                visit(w);  // 输出顶点 w
            } while (w != u);
            printf("\n");
        }
    }

    // 遍历所有顶点，如果顶点未被访问，则进行 DFS
    for (int i = 0; i < G->NumOfVertices; i++) {
        if (disc[i] == -1) {
            DFS(i);
        }
    }
}
```
### 分析：
- 如果 `disc[u] == low[u]`，则从栈中弹出顶点，直到顶点 `u`，构成一个强连通分量。
#### `inStack` 的作用
1. **防止重复添加顶点到栈中**：
    - `inStack` 数组记录了哪些顶点已经在栈中。当遍历顶点的邻接顶点时，如果一个邻接顶点已经在栈中，那么它的 `low` 值和 `disc` 值已经在当前 DFS 路径上被处理过了，不需要再次处理。
2. **正确更新 `low` 值**：
    - 当遍历到一个在栈中的邻接顶点时，表明在当前 DFS 路径上存在一个回边。为了正确更新当前顶点的 `low` 值，需要使用 `inStack` 数组来确认这个邻接顶点在栈中。只有在这种情况下，才更新 `low` 值为邻接顶点的 `disc` 值。
3. **识别强连通分量**：
    - 当检测到一个强连通分量时，需要从栈中弹出顶点。如果没有 `inStack` 数组，在递归和回溯的过程中很难准确地确定哪些顶点是属于当前强连通分量的一部分。
# HW12
## 函数：非递归的归并
>将N个元素看作N个序列（初始化），然后每次取相邻的两个序列进行归并；循环上述操作，直至得到最后的序列。
### 我的神奇脑回路
📝设置i,j作为移动的指针，每次选取两个相邻的序列（注意控制i,j的递增状态），然后从左往右地移动i,j指针。
🌰经过gpt修正的版本：
```c
void merge_pass( ElementType list[], ElementType sorted[], int N, int length )
{
    int i, j;

    void sort_once(ElementType list[], ElementType sorted[], int left, int mid, int right)
    {
        int i = left, j = mid, k = left;
        
        while (i < mid && j < right) {
            if (list[i] <= list[j]) {
                sorted[k++] = list[i++];
            } else {
                sorted[k++] = list[j++];
            }
        }
        while (i < mid) 
            sorted[k++] = list[i++];
        while (j < right) 
            sorted[k++] = list[j++];
    }

    for (i = 0; i < N; i += 2 * length) {
        int left = i;
        int mid = (i + length < N) ? i + length : N;
        int right = (i + 2 * length < N) ? i + 2 * length : N;
        sort_once(list, sorted, left, mid, right);
    }
}
```

## 编程
- 要求：
	题目围绕插入排序和堆排序的问题展开。并且要求对一个给定的序列按照从小到大排序；
	我们注意到，插入排序的逻辑是：依次抽取给定的序列的元素，找到合适的位置，因此每一步循环总是<mark style="background: #FFF3A3A6;">从前开始有序</mark>。另一方面，对于**从小到大**的堆排序，我们需要构造<mark style="background: #ADCCFFA6;">最大堆</mark>，并且每次取用最大元素放到数组未排序部分的最末端；因此，每一步循环总是从<mark style="background: #FFF3A3A6;">后面依次向前有序</mark>！
	题目将给出待排序的序列，以及排序过程中某一步的结果。要求我们据此判断使用了上述哪一种排序方法，并且给出用该方法下一步循环得到的序列结果。
- 分析：
	- 题目的解决显然分为两部分——①判断所用的排序方式；②根据该方式进一步排序
	- 第一步是容易的，我们只要判断前几个数字和后几个数字是否满足排序关系即可
	- 对于第二步，我们需要另外写两份函数，根据选择调用对应的算法
- 🧐问题：
	- 如何判断方式
		- 如果给定的原序列本身就是部分有序（开头或者结尾），那么不能简单地判断
### 解答：
🌰:
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

// 分析排序方式：插入排序返回1，堆排序返回2
int judgeSort(int* arr, int* judge, int size) {
    int i, count = 0;

    // 找到部分有序的最后一个元素位置
    while (count < size - 1 && judge[count] <= judge[count + 1]) {
        count++;
    }

    // 检查是否为插入排序
    for (i = count + 1; i < size; i++) {
        if (judge[i] != arr[i]) {
            return 2; // 不满足插入排序条件，则为堆排序
        }
    }
    return 1; // 满足插入排序条件
}

void insertionSort(int* seq, int* sort, int length) {
    int count = 0;
    while (count < length - 1 && sort[count] <= sort[count + 1]) {
        count++;
    }
    int sortNum = sort[count + 1];
    int i;
    for (i = count + 1; i > 0 && sort[i - 1] > sortNum; i--) {
        sort[i] = sort[i - 1];
    }
    sort[i] = sortNum;

    for (int i = 0; i < length; i++) {
        if (i == 0)
            printf("%d", sort[i]);
        else
            printf(" %d", sort[i]);
    }
    printf("\n");
}

void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

void maxHeapify(int* arr, int n, int i) {
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && arr[left] > arr[largest]) {
        largest = left;
    }

    if (right < n && arr[right] > arr[largest]) {
        largest = right;
    }

    if (largest != i) {
        swap(&arr[i], &arr[largest]);
        maxHeapify(arr, n, largest);
    }
}

void buildMaxHeap(int* arr, int n) {
    for (int i = n / 2 - 1; i >= 0; i--) {
        maxHeapify(arr, n, i);
    }
}

int findMax(int* seq, int* checkedId, int size) {
    int max = -1, maxId = -1;
    for (int i = 0; i < size; i++) {
        if (checkedId[i] == 0 && seq[i] > max) {
            max = seq[i];
            maxId = i;
        }
    }
    if (maxId != -1)
        checkedId[maxId] = 1;
    return max;
}

void heapSort(int* seq, int* sort, int size) {
    int count = size - 1;

    // 找到部分有序的最后一个元素位置
    while (count > 0 && sort[count] >= sort[count - 1]) {
        count--;
    }

    // 确保只对未排序部分进行堆化
    buildMaxHeap(sort, count + 1);

    // 交换堆顶元素和最后一个未排序的元素
    swap(&sort[0], &sort[count]);

    // 调整堆
    maxHeapify(sort, count, 0);

    // 输出结果
    for (int i = 0; i < size; i++) {
        if (i == 0)
            printf("%d", sort[i]);
        else
            printf(" %d", sort[i]);
    }
    printf("\n");
}


int main() {
    int length, method;
    int* sequence;
    int* partialSorted;
    scanf("%d", &length);
    sequence = (int*)malloc(sizeof(int) * length);
    partialSorted = (int*)malloc(sizeof(int) * length);

    // 读入原始序列与部分排序序列
    for (int i = 0; i < length; i++)
        scanf("%d", &sequence[i]);
    for (int i = 0; i < length; i++)
        scanf("%d", &partialSorted[i]);

    // 由第二份序列分析对应的排序方式：有序构建的方向
    method = judgeSort(sequence, partialSorted, length);
    switch (method) {
    case 1:
        printf("Insertion Sort\n");
        insertionSort(sequence, partialSorted, length);
        break;
    case 2:
        printf("Heap Sort\n");
        heapSort(sequence, partialSorted, length);
        break;
    }

    free(sequence);
    free(partialSorted);
    return 0;
}

```
# HW13
## 优先处理较小子数组的快排
- 🌰描述：
	***During the sorting, processing every element which is not yet at its final position is called a "run". To sort a list of integers using quick sort, it may reduce the total number of recursions by processing the small partion first in each run.***
- ✅解释：![Pasted image 20240529185041.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240529185041.png)
## 链表结构对排序的影响
- 描述：采用链表而非数组的数据结构，来进行排序时，算法会受到什么影响呢？
- 分析：
	- <mark style="background: #FFF3A3A6;">插入算法将得到优化</mark>：这是每次选择合适的位置对未排序的元素进行**插入**，这一操作契合链表方便插入的特性；
	- <mark style="background: #FFF3A3A6;">希尔排序会降低效率</mark>：这是因为虽然希尔排序是在插入排序的基础上进行的，但是是选择`gap`对不连续的部分进行部分排序。在这个过程中，链表需要多次移动，才能比较对应的数据。因此效率低下
	- <mark style="background: #FFF3A3A6;">堆排序会降低效率</mark>：这是因为涉及到了堆顶元素与数组末尾元素的**交换**，此后要进一步对**非相邻的元素进行比较**来维持堆的性质。
	- <mark style="background: #FFF3A3A6;">冒泡排序将是高效</mark>的：这是因为依次比较相邻的元素大小，如果顺序异常可以直接交换数据域的值。
- 综上，**插入**排序和**冒泡**排序将会在链表数据结构的排序中高效表现。
## 傻逼题
![Pasted image 20240529201222.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240529201222.png)