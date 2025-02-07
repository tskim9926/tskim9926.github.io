# Dynamic Programming

## 개념
- 복잡한 문제를 작은 하위 문제로 나누어 푸는 알고리즘
- 중복되는 하위 문제를 해결할 때 유용
- 같은 계산을 여러번 하지 않도록 메모이제이션 기법을 사용하여 계산 결과를 저장

## 원리
1. 최적 부분 구조 : 문제를 해결하는 최적 방법이 부분 문제들의 최적 해법으로 구성
2. 중복되는 부분 문제 : 동일한 하위 문제를 여러번 해결하는 경우로 구성

## 구현 방식
1. Top-Down : 재귀적으로 문제를 해결하고, 계산된 값을 메모이제이션하여 중복 계산을 피함
2. Bottom-up : 하위 문제제부터 차례대로 해결하여 최종적인 해를 구한다

## 구현 예제
```
#include <iostream>
#include <vector>
using namespace std;

vector<int> memo; // 메모이제이션을 위한 배열

int fibonacci(int n) // top-down method
{
	if (n <= 1) return n; // 기본 케이스

	if (memo[n] != -1) return memo[n]; // 이미 계산된 값이 있으면 그대로 반환

	// 계산되지 않았다면 재귀적으로 계산하고 메모이제이션
	memo[n] = fibonacci(n - 1) + fibonacci(n - 2);

	return memo[n];
}

int fibonacci2(int n) // bottom-up method
{
	if (n <= 1) return n; // 기본 케이스
	vector<int> dp(n + 1, 0); // dp array
	dp[1] = 1;

	// bottom-up method
	for (int i = 2; i <= n; ++i)
	{
		dp[i] = dp[i - 1] + dp[i - 2];
	}

	return dp[n];
}

int main()
{
	int n;
	cout << "Enter: n: ";
	cin >> n;

	memo.resize(n + 1, -1); // -1로 배열 초기화
	cout << "Fibonacci(" << n << ")= " << fibonacci(n) << endl;

  cout << "Fibonacci2(" << n << ")= " << fibonacci2(n) << endl;

	return 0;
}
