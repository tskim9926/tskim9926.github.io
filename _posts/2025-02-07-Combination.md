# 조합 Combination

## 개념
- 주어진 원소들 중 일부를 선택하는 방법
- 순서를 고려하지 않는 경우
- 순열(Permutation): 순서가 중요 -> (a, b) != (b, a)
- 조합(Combination): 순서가 중요하지 않음 -> (a, b) == (b, a)

## 원리
C(n, r) = n! / (n - r)! / r!

```
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

// 조합을 저장할 벡터
vector<int> combination;

// 조합을 구하는 백트래킹 함수
void getCombinations(vector<int>& nums, int start, int r)
{
	if (combination.size() == r) // r개를 선택한 경우 출력
	{
		for (int num : combination)
		{
			cout << num << " ";
		}
		cout << '\n';
		return;
	}

	for (int i = start; i < nums.size(); ++i)
	{
		combination.push_back(nums[i]); // 현재 원소 추가
		getCombinations(nums, i + 1, r); // 다음 원소 선택 (순서 유지)
		combination.pop_back(); // 원소 제거 (백트래킹)
	}
}

int main()
{
	vector<int> nums = { 1, 2, 3, 4 }; // 조합을 구할 원소들
	int r = 2; // 2개를 선택하는 조합
	getCombinations(nums, 0, r);

	return 0;
}
