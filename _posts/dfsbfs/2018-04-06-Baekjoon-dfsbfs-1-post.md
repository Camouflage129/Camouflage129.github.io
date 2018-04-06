---
layout: post

title: 1260. DFS BFS

categories: [dfsbfs]

---
[백준 1260번 문제보러가기](https://www.acmicpc.net/problem/1260)<br>

**==문제풀이 힌트==**<br>

DFS가 체크해야 할 부분이 많다.<br>

BFS는 정말 알고리즘 그대로 구현하면 되나, DFS의 경우에는 연결안된 노드가 있는경우,<br>

더 이상 탐색할 곳이 없어 이전으로 돌아가서 다시 탐색해야하는 경우를 잘 생각하여 구현해야한다.<br>

```cpp
#pragma warning (disable:4996)
#include<iostream>
#include<queue>
#include<stack>
#include<algorithm>
using namespace std;

bool check_check(bool *check, int N) {
	for (int i = 0; i < N; i++) {
		if (!check[i])
			return false;
	}
	return true;
}

void dfs(bool *graph[], stack<int> &stack, bool *check, int N) {
	int flag = stack.size();
	for (int i = 0; i<N; i++) {
		if (graph[stack.top() - 1][i] && !check[i]) {
			check[i] = true;
			stack.push(i + 1);
			printf("%d ", stack.top());
			break;
		}
	}
	if (!check_check(check, N)) {
		if (flag != stack.size())	
			dfs(graph, stack, check, N);
		else {	//더 이상 이동할 곳이 없을 때, 전 노드로 가서 다시 이동
			stack.pop();
			dfs(graph, stack, check, N);
		}
	}
}

void bfs(bool *graph[], queue<int> &que, bool *check, int N) {
	for(int i=0; i<N; i++) {
		if (graph[que.front()-1][i] && !check[i]) {
			check[i] = true;
			que.push(i+1);
		}
	}
	printf("%d ", que.front());
	que.pop();
	if(que.size() != 0)
		bfs(graph, que, check, N);
}


int main() {
	int N, M, V;
	scanf("%d %d %d", &N, &M, &V);

	//변수 선언
	stack<int> stack;
	queue<int> que;
	bool *check = new bool[N];
	bool **graph = new bool*[N];
	fill_n(check, N, true);
	for (int i = 0; i < N; i++) {
		graph[i] = new bool[N];
		fill_n(graph[i], N, 0);
	}

	//그래프 값 입력
	int x, y;
	for (int i = 0; i < M; i++) {
		scanf("%d %d", &x, &y);
		graph[x-1][y-1] = graph[y-1][x-1] = true;
		check[x-1] = check[y-1] = false;	//연결이 아에 안 된 노드를 True로 해놓기 위함(dfs용)
	}

	//dfs
	stack.push(V);
	check[V - 1] = true;
	printf("%d ", stack.top());
	dfs(graph, stack, check, N);
	printf("\n");

	//bfs
	que.push(V);
	fill_n(check, N, false);
	check[V - 1] = true;
	bfs(graph, que, check, N);
	printf("\n");
}
```

==풀이==**<br>

주석이 꽤나 상세하므로 잘 보면 알 수 있다.<br>

길을 지나 왔다는 것을 check 변수로 check하는데 연결 안된 노드는 True인 상태로 놓기위해<br>

간선을 입력받을 때, 각 연결된 노드들은 False로 지나가야 한다는 것을 체크해놓는다.<br>

그리고 모든 노드가 다 지나갔는지를 check하는 chekc_check함수로<br>

dfs를 종료할지 계속 실행할지를 체크하고,<br>

만약 더 이상 이동할 곳이 없어 다시 이전으로 돌아가야 한다면,<br>

stack에서 pop하고 다시 dfs를 돌리면 된다.<br>

bfs는 알고리즘 그대로 어려운것 없이 구현되있으므로 생략<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}