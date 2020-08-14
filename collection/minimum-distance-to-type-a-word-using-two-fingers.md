[二指输入的的最小距离](https://leetcode-cn.com/problems/minimum-distance-to-type-a-word-using-two-fingers/)

一个小trick，构造一个函数来帮助计算行数列数之差的和，来计算两个字母的距离。

```c++
int getDistance(int p, int q) {
    int x1 = p / 6, y1 = p % 6;
    int x2 = q / 6, y2 = q % 6;
    return abs(x1 - x2) + abs(y1 - y2);
}
```

最暴力的想法，$dp[i][l][r]$ i 为 当前已经输入了i个字母，l表示左手放在字母l上，r表示右手放在字母r上。

```c++
dp[i][v][r] = min(dp[i][v][r], dp[i-1][l][r] + getDistance(l, v));
dp[i][l][v] = min(dp[i][l][v], dp[i-1][l][r] + getDistance(r, v));
```

表示左手去按第i个字符或者右手去按第i个字符

```c++
memset(dp[0], 0, sizeof(dp[0]));
```

在初始化时表示没有按字符时两个手随便放的代价都是0，从而表示两根手指的起始位置是零代价的。

```c++
class Solution {
public:
    int help(int a, int b) {
        int x = a / 6, y = a % 6;
        int x2 = b / 6, y2 = b % 6;
        return abs(x-x2)+abs(y-y2);
    }
    int min(unsigned int a, unsigned int b) {
        if (a > b) return b;
        return a;
    }
    int minimumDistance(string word) {
        int dp[301][26][26];
        memset(dp, -1, sizeof(dp));
        memset(dp[0], 0, sizeof(dp[0]));
        
        int n = word.size();
        for (int i = 1; i <= n; i++) {
            int v = word[i-1] - 'A';
            for (int l = 0; l < 26; l++) {
                for (int r = 0; r < 26; r++) {
                    if (dp[i-1][l][r] == -1) continue;
                    dp[i][v][r] = min(dp[i][v][r], dp[i-1][l][r] + help(l, v));
                    dp[i][l][v] = min(dp[i][l][v], dp[i-1][l][r] + help(r, v));
                }
            }
        }
        int v = word[n-1] - 'A';
        int ans = 0x7fffffff;
        for (int j = 0; j < 26; j++) {
            ans = min(ans, dp[n][v][j]);
            ans = min(ans, dp[n][j][v]);
        }
        return ans;
    }
};
```

时间复杂度$O(26*26*n)$

更进一步，当按到第i个字符时，左手或者右手是放在第i-1个字符上的，因此只需要枚举另一个手放的位置。

需要两个循环来判断从第i-1个字符按到第i个字符以及从之前任意字符按到第i个字符，i-1个字符不变。

```c++
class Solution {
public:
    int getDistance(int p, int q) {
        int x1 = p / 6, y1 = p % 6;
        int x2 = q / 6, y2 = q % 6;
        return abs(x1 - x2) + abs(y1 - y2);
    }

    int minimumDistance(string word) {
        int n = word.size();
        int dp[n][26][26];
        memset(dp, 0x3f, sizeof(dp));
        for (int i = 0; i < 26; ++i) {
            dp[0][i][word[0] - 'A'] = dp[0][word[0] - 'A'][i] = 0;
        }
        
        for (int i = 1; i < n; ++i) {
            int cur = word[i] - 'A';
            int prev = word[i - 1] - 'A';
            int d = getDistance(prev, cur);
            for (int j = 0; j < 26; ++j) {
                dp[i][cur][j] = min(dp[i][cur][j], dp[i - 1][prev][j] + d);
                dp[i][j][cur] = min(dp[i][j][cur], dp[i - 1][j][prev] + d);
                if (prev == j) {
                    for (int k = 0; k < 26; ++k) {
                        int d0 = getDistance(k, cur);
                        dp[i][cur][j] = min(dp[i][cur][j], dp[i - 1][k][j] + d0);
                        dp[i][j][cur] = min(dp[i][j][cur], dp[i - 1][j][k] + d0);
                    }
                }
            }
        }
        int ans = 0x7fffffff;
        for (int i = 0; i < 26; i++) {
            for (int j = 0; j < 26; j++) {
                ans = min(ans, dp[n-1][i][j]);
            }
        }
        return ans;
    }
};
```

时间复杂度$O(26*n)$

同时，这里的左手和右手是对称的，因此转移方程可以简化

```c++
class Solution {
public:
    int getDistance(int p, int q) {
        int x1 = p / 6, y1 = p % 6;
        int x2 = q / 6, y2 = q % 6;
        return abs(x1 - x2) + abs(y1 - y2);
    }

    int minimumDistance(string word) {
        int n = word.size();
        int dp[n][26];
        memset(dp, 0x3f, sizeof(dp));
        for (int i = 0; i < 26; ++i) {
            dp[0][i] = 0;
        }
        
        for (int i = 1; i < n; ++i) {
            int cur = word[i] - 'A';
            int prev = word[i - 1] - 'A';
            int d = getDistance(prev, cur);
            for (int j = 0; j < 26; ++j) {
                dp[i][j] = min(dp[i][j], dp[i - 1][j] + d);
                if (prev == j) {
                    for (int k = 0; k < 26; ++k) {
                        int d0 = getDistance(k, cur);
                        dp[i][j] = min(dp[i][j], dp[i - 1][k] + d0);
                    }
                }
            }
        }
        int ans = 0x7fffffff;
        for (int i = 0; i < 26; i++) {
            ans = min(ans, dp[n-1][i]);
        }
        return ans;
    }
};
```

