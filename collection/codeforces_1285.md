[1285D - Dr. Evil Underscores](https://codeforces.com/contest/1285/problem/D)

对于第`i`位，如果数组中所有的数都是`1`或者`0`，那么我们通过选择可以使异或的结果为`0`；

如果既有`1`也有`0`，异或的结果的`i`位一定是`1`，但是我们可以选择置`1`或者`0`的一个最小值。

```c++
#include <iostream>
#include <vector>
using namespace std;

vector<int> a;
int solve(vector<int>& c, int bit) {
	if (c.size() == 0 || bit < 0) return 0;
	vector<int> l, r;
	for (auto& i : c) {
		if (((i >> bit) & 1) == 0) 
			l.push_back(i);
		else 
			r.push_back(i);
	}
	if (l.size() == 0) return solve(r, bit - 1);
	if (r.size() == 0) return solve(l, bit - 1);
	return min(solve(l, bit - 1), solve(r, bit - 1)) + (1 << bit);
}
int main() {
	ios_base::sync_with_stdio(0);
	cin.tie(0);
	int n;
	cin >> n;
	a.resize(n);
	for (auto& i : a) cin >> i;
	cout << solve(a, 30) << endl;
	return 0;
}
```

