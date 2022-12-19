# search algorithm

## 最长回文子串

[longest-palindromic-substring](https://leetcode.cn/problems/longest-palindromic-substring/)

```java
public String longestPalindrome(String s) {
    String res = "";
    for(int i = 0; i < s.length(); i++) {
        for (int j = 0; j < 2; j++) {
            String tmp = check(s, i, i + j);
            if(tmp.length() > res.length()) res = tmp;
        }
    }
    return res;
}
// 中心扩散，检查回文串
public String check(String s, int left, int right) {
    String str = "";
    while(left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
        str = s.substring(left, right + 1);
        left--;
        right++;
    }
    return str;
}
```

## 最小覆盖子串

[minimum-window-substring](https://leetcode.cn/problems/minimum-window-substring/)
核心思想：滑动窗口

```java
public String minWindow(String s, String t) {
    Map<Character, Integer> map = new HashMap<>();
    AtomicInteger count = new AtomicInteger(0);
    for (int i = 0; i < t.length(); i++) {
        map.put(t.charAt(i), map.getOrDefault(t.charAt(i), 0) + 1);
        count.getAndIncrement();
    }

    int left = 0;
    int right = 0;
    String res = "";
    while (right < s.length()) {
        // 添加元素
        map.computeIfPresent(s.charAt(right), (key, value) -> {
            if (value > 0) {
                count.getAndDecrement();
            }
            return value - 1;
        });
        right++;
        // 移动窗口
        while (count.get() == 0 && left < right) {
            if (res.equals("") || s.substring(left, right).length() < res.length()) {
                res = s.substring(left, right);
            }
            map.computeIfPresent(s.charAt(left), (key, value) -> {
                if (value >= 0) {
                    count.getAndIncrement();
                }
                return value + 1;
            });
            left++;
        }
    }
    return res;
}
```
