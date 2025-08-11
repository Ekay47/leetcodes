# 无重复字符的最长子串
给定一个字符串 s ，请你找出其中不含有重复字符的 最长 子串 的长度。

class Solution {
    public int lengthOfLongestSubstring(String s) {
        int res = 0;
        Map<Character, Integer> map = new HashMap<>();
        int i = 0;
        int left = 0;
        while (i < s.length()) {
            char ch = s.charAt(i);
            if(map.containsKey(ch)){
                res = Math.max(res, map.size());
                int j = left;
                left = map.get(ch) + 1;
                for(;j<left;j++){
                    map.remove(s.charAt(j));
                }
                map.put(ch, i);
            }else{
                map.put(ch, i);
            }
            i++;
        }
        res = Math.max(res, map.size());
        return res;
    }
}

class Solution {
    public int lengthOfLongestSubstring(String s) {
        int res = 0;
        int[] idx = new int[128];
        int i = 0;
        int left = 0;
        while (i < s.length()) {
            char ch = s.charAt(i);
            left = Math.max(left, idx[ch]);
            res = Math.max(res, i-left+1);
            idx[ch] = i + 1;
            i++;
        }
        return res;
    }
}

