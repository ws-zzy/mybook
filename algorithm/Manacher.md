[longest palindromic substring](https://leetcode-cn.com/problems/longest-palindromic-substring/)

Manacher算法的主要思想是对称性。

首先添加一定不在这个字符串的字符，使得字符串长度变成奇数。
对于每个位置进行中心拓展。

如果当前的位置被包含在一个之前已经找到的长串$s$回文中，那么这个位置在长串$s$的对称位置可以提供一个已经中心拓展过的信息。

时间复杂度$O(n)$。

```c++
class Solution {
public:
    string longestPalindrome(string s) {
        int n = s.size();
        if (n < 2) return s;
        string t = "$";
        for (int i = 0; i < n; i++) {
        	t += "#";
        	t += s[i];
        }
        t += "#@";
        
        n = n*2+3;
        vector<int> p(n, 0);
        int id = 0, mx = 0;
        int max_len = -1;
        int index = 0;
        for (int i = 1; i < n-1; i ++) {
        	p[i] = mx > i ? min(p[2*id-i], mx-i) : 1;
        	while (t[i+p[i]] == t[i-p[i]]) 
        		p[i]++;
        	if (mx < p[i] + i) {
        		mx = p[i] + i;
        		id = i;
        	}
        	if (max_len < p[i] - 1) {
        		max_len = p[i] - 1;
        		index = i;
        	}
        }
        int start = (index-max_len) / 2;
        return s.substr(start,  max_len);
    }
};
```

