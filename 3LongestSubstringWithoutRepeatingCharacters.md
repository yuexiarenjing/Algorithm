#Question
```
Given a string, find the length of the longest substring without repeating characters.

Examples:

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```
Approach 1 Brute Force[Time Limit Exceeded]
```
public class Solution{
  public int lengthOfLongestSubstring(String s){
    int n = s.length();
    int ans = 0;
    for(int i = 0; i < n; i++)
      for(j = i + 1; j <= n; j++)
        if(allUnique(s, i, j) and = Math.max(ans, j - i));
    return ans;
  }
  
  public boolean allUnique(String s, int start, int end){
    Set<Character> set = new HashSet<>();
    for(int i = start; i < end; i++){
      Character ch = s.charAt(i);
      if(set,contains(ch)) return false;
      set.add(ch);
    }
    return true;
  }
}
```
Approach 2 Sliding Window[Accepted]
```
public class Solution{
  public int lengthOfLongestSubstring(String s){
    int n  = s.length();
    Set<Character> set = new HashSet<>();
    int ans = 0, i = 0, j = 0;
    while(i < n && j < n){
      //try to extend the range[i, j)
      if(!set.contains(s.charAt(j))){
        set.add(s.charAt(j++));
        ans = Math.max(ans, j - i);
      }
      else{
        set.remove(s.charAt(i++));
      }
    }
    return ans;
  }
}
```
Approach 3 Sliding Window Optimized[Accepted]
```
public class Solution{
  public int lengthOfLongestSubstring(String s){
    int n = s.length(), ans = 0;
    Map<Character, Integer> map new HashMap<>();//Current index of character
    //try to extend the range[i , j)
    for(int j = 0, i = 0; j <　n; j++){
      if(map.containsKey(s.charAt(j))){
        i = Math.max(map.get(s.charAt(j)), i);
      }
      ans = Math.max(and, j - i + 1);
      map.put(s.charAt(j), j+1);
    }
    return ans;
  }
}

public class Solution{
  public int lengthOfLongestSubstring(String s){
    int n = s.length(), ans = 0;
    int[] index = new int [128];//current index of character;
    //try to extend the raneg [i , j)
    for(int j = 0, i = 0; j < n ; j++){
      i = Math.max(index[s.charAt(j)], i);
      ans = Math.max(ans, j - i + 1);
      index[s.charAt(j)] = j + 1;
    }
    return ans;
  }
}
```
