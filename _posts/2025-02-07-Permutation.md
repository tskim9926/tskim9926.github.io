# 순열 Permutation

## 개념
주어진 집합에서 원소들의 순서를 고려하여 배열하는 방법 (순서가 중요 !)

## 원리
P(n, r) = n! / (n - r)!

```
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

void permute(vector<int>& nums, int start)
{
	// 재귀 종료 조건 : start가 nums 크기와 같다면 모든 원소가 다 배치된 것
	if (start == nums.size())
	{
		for (int num : nums)
		{
			cout << num << " "; // 현재 순열 출력
		}
		cout << endl;
		return;
	}

	for (int i = start; i < nums.size(); ++i)
	{
		// 원소를 swap하여 순열을 만듦
		swap(nums[start], nums[i]);
		permute(nums, start + 1); // 다음 원소로 이동
		swap(nums[start], nums[i]); // 원상복구 (백트래킹)
	}
}

int main()
{
	vector<int> nums = { 1, 2, 3 }; // 순열을 구할 원소들
	permute(nums, 0); // 0번 인덱스부터 시작
	
	return 0;
}
