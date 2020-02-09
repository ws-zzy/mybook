[tweet counts per frequency](https://leetcode-cn.com/problems/tweet-counts-per-frequency/)

这个复杂度我还不会算。

`c++`的标准库用的还是不熟练，`map`是有自动排序的，所以这里很方便。

```c++
class TweetCounts {
public:
    TweetCounts() {

    }
    void recordTweet(string tweetName, int time) {
        record[tweetName][time] ++;
    }
    
    vector<int> getTweetCountsPerFrequency(string freq, string tweetName, int startTime, int endTime) {
        int f = 60;
        if (freq == "hour") f *= 60;
        if (freq == "day") f *= 60 * 24;
        vector<int> ans(0);
        int t = startTime;
        while (t <= endTime) {
        	auto low = record[tweetName].lower_bound(t);
        	auto up = record[tweetName].upper_bound(min(t+f-1, endTime));
        	int cnt = 0;
        	for (auto it = low; it != up; it++) 
        		cnt += it->second;
        	ans.push_back(cnt);
        	t += f;
        }
        return ans;
    }
private:
	unordered_map<string, map<int, int>> record;
};

/**
 * Your TweetCounts object will be instantiated and called as such:
 * TweetCounts* obj = new TweetCounts();
 * obj->recordTweet(tweetName,time);
 * vector<int> param_2 = obj->getTweetCountsPerFrequency(freq,tweetName,startTime,endTime);
 */
 ```