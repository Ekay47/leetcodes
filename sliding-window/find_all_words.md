# 给定两个字符串 s 和 p，找到 s 中所有 p 的 异位词 的子串，返回这些子串的起始索引。不考虑答案输出的顺序。

public List<Integer> findAnagrams(String s, String p) {
        int[] idx = new int[27];
        List<Integer> res = new ArrayList<>();
        if(s.length()<p.length())return res;
        for(int i=0;i<p.length();i++){
            char ch = p.charAt(i);
            idx[ch-'a']++;
            char sch =  s.charAt(i);
            idx[sch-'a']--;
        }

        int left = 0;
        for(left=0;left<(s.length()-p.length());left++){
            if(isEmpty(idx))res.add(left);
            idx[s.charAt(left)-'a']++;
            idx[s.charAt(left+p.length())-'a']--;
        }
        if(isEmpty(idx))res.add(left);
        return res;
    }

    public boolean isEmpty(int[] idx){
        return Arrays.stream(idx).allMatch(num -> num == 0);
    }

    
