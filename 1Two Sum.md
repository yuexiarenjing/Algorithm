#Qeustion:
```
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution.

Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
Approach 1 Brute Force
```
public int[] twoSum(int[] sums, int target){
	for (int i = 0; i < sums.length; i++) {
		for (int j = i + 1; j < sums.length; j++) {
			if(sums[j] == target - nums[i]){
				return new int[] { i, j };
			}
		}
	}
	throw new IllegalArgumentException("No two sum solution");
}
```
Approach 2 Two-pass Hash Table
```
public int[] twoSum(int[] sums, int target){
	Map<Integer, Integer>	map = new HashMap<>();
	for (int i = 0; i < sums.length; i++) {
		map.put(nums[i], i);
	}
	for (int i = 0; i < nums.length; i++) {
		int complement = target - nums[i];
		if(map.contaionsKey(complement) && map.get(complement) != i){
			return new int[] { i, map.get(complement) };
		}
	}
	throw new IllegalArgumentException("No two sum solution");
}
```
Approach 3 One-pass Hash Table
```
public int[] twoSum(int[] sums, int target){
	Map<Integer, Integer> map = new HashMap<>();
	for (int i = 0; i < nums.length; i++) {
		int complement = target - sums[i];
		if(map.contaionsKey(complement)){
			return new int[] { map.get(complement), i };
		}
		map.put(nums[i], i);
	}
	throw new IllegalArgumentException("No two sum solution");
}
```
