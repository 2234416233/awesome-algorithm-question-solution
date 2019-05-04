# Minimum Size Subarray Sum (无序数组和大于或等于某值的最小子数组)



## From

[LeetCode 209](https://leetcode.com/problems/minimum-size-subarray-sum/description/)



## Question

Given an array of **n** positive integers and a positive integer **s**, find the minimal length of a **contiguous** subarray of which the sum ≥ **s**. If there isn't one, return 0 instead.

**Example: **

```
Input: [2,3,1,2,4,3], s = 7
Output: 2
Explanation: the subarray [4,3] has the minimal length under the problem constraint.
```



## Solution  

### C++

```c++
#include <vector>

using namespace std;

int minSubArrayLen(int s, vector<int>& nums) {

    //using moving window

    int l = 0;  //left end
    int r = -1; //right end
    int sum = 0;
    int res = nums.size() + 1;

    while (l < nums.size()){
        if ( r+1 < nums.size() && sum < s){
            r++;
            sum += nums[r];
        }else{
            sum -= nums[l];
            l++;
        }

        if(sum>=s){
            res = min(res,r-l+1);
        }
    }

    if (res == nums.size() + 1){
        return 0;
    }

    return res;

}
```


### Java

```java
class Solution {
    public int minSubArrayLen(int s, int[] nums) {
        
         int l = 0;  //left end
         int r = -1; //right end
         int sum = 0;
         int n = nums.length;
         int res = n + 1;

    while (l < n){
        
        if ( r+1 < n && sum < s){
            
            r++;
            sum += nums[r];
            
        }else{
            sum -= nums[l];
            l++;
        }

        if(sum >= s){
            
            res = Math.min(res, r-l+1);
        }
    }

    if (res == n + 1){
        
        return 0;
    }

    return res;

    }
}

```


