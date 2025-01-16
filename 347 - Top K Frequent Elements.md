# 347: Top K Frequent Elements - Solution Approach

## Problem Understanding🤔

Given an array of integers and a number k, we need to find the k most frequent elements in the array. The order of the result doesn't matter.

## Solution Approach🎯

We can solve this using a bucket sort approach with these steps:

- Count frequency of each number using HashMap
- Create frequency buckets (array of lists)
- Place numbers in their frequency buckets
- Collect top K frequent elements from highest frequencies

## Code Implementation💻

```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        // Step 1: Count frequencies
        Map<Integer, Integer> map = new HashMap<>();
        for(int n : nums) {
            map.put(n, map.getOrDefault(n, 0) + 1);
        }
        
        // Step 2: Create frequency buckets
        List<Integer>[] bucket = new List[nums.length + 1];
        
        // Step 3: Place numbers in frequency buckets
        for(int key : map.keySet()) {
            int freq = map.get(key);
            if(bucket[freq] == null) {
                bucket[freq] = new ArrayList<>();
            }
            bucket[freq].add(key);
        }
        
        // Step 4: Collect top K elements
        List<Integer> result = new ArrayList<>();
        for(int i = nums.length; i > 0 && result.size() < k; i--) {
            if(bucket[i] != null) {
                result.addAll(bucket[i]);
            }
        }
        
        // Convert to array
        int[] topK = new int[k];
        for(int i = 0; i < k; i++) {
            topK[i] = result.get(i);
        }
        return topK;
    }
}
```

## Example Walkthrough

For input: nums = [1,1,1,2,2,3], k = 2

- Frequency count: {1:3, 2:2, 3:1}
- Bucket array: index represents frequency
- Bucket[3] contains [1]
- Bucket[2] contains [2]
- Bucket[1] contains [3]
- Result: [1,2] (most frequent elements)

## Time and Space Complexity⚡

- Time Complexity: O(n) where n is the length of the input array
- Space Complexity: O(n) for the HashMap and bucket array

## Key Points💡

- Bucket sort approach avoids the need for sorting
- HashMap efficiently tracks frequency counts
- Solution handles duplicate frequencies naturally
- Result order doesn't matter as per problem requirements