---
layout: post
tldr: false
audio: false
title:  "Dynamic Programming"
date:   2015-02-10 15:14:54
categories: algorithm
---
    
## A good algorithm design paradigm 
 
+ correctness: get all the answer of the whole problem;  
+ efficiency: avoid re-computation.  


## Key ingredients   

1. identify a small number of sub-problems;   
2. can quickly and correctly solve "larger problems" given the solutions of "smaller subproblems";   
3. After solving all subproblems, can quickly compute the final solution.   

## Difference: DP and Divide and Conquer?   

1. dynamic programming solve small sub-problems, which may lead to re-compute the same sub-problem if we do not cache the answers;   
2. divide and conquer just solve unique sub-problems and combine the answers.   

<br>
<br>
<br>
<br>

---

## Examples

<br><br>


### Leetcode 32 Longest Valid Parentheses

##### Problem description: 

Given a string `s`, containing '(' or ')', find the length of longest valid well-formed parentheses substring.

Input	|Output
------- |  ---------
(()	| 2
)()())	| 4

##### Solution: O(N)

> Check if the `i`th element is `end` of a valid substring, if yes find the length. 

Properties for an `end` elemenet `cj`:

* not the first element
* equals to `)`
* can find privous `ci` equals `(` to match
* substring between `ci` and `cj` is valid
	
If `cj` satisfies all the privous properties, `s[i~j]` is at least a valid substring. And also, if there is a valid substring `s[x~i-1]` left to `s[i~j]`, so that `s[x~j]` is the longest substring ended by `cj`.

##### Code

Below is the Pseudo code for check and compute for `cj`: 
	
	check_if_end(j):
		if c[j] == '('
			dp[j] = 0
		else
			int i = j - dp[j-1] - 1;
			if i < 0 or c[i]==')'
				dp[j] = 0
			else
				dp[j] = (j-i+1) + dp[i-1];
				
	//edge case: i or i-1 is left out of boundary


Edge case:

* the '(' index i will match, p, is left out of boundary

Pseudo code for the whole problem

	solution():
		res = 0
		for each j in s.length
			len = check_if_end(j)
			res =  max(res, len)
		return res


* Time: O(N)
* Space: O(N)


<br>
<br>
<br>
<br>


---

### Leetcode 53 Maximum Subarray

##### Problem description
Find the contiguous subarray within an array(containing at least one number) which has the largest sum.

Input	|Output
------ |  -------
[-2,1,-3,4,-1,2,1,-5,4]|6

Hint: the subarray with the largest sum is [4,-1,2,1]

##### Solution: 

> Using array `sum` where `sum[i]` represents the maximum sum through `nums[x]` to `nums[i]`;

two types of `sum[i]`:

* `nums[i]`, when `i` is the head of the array, or `sum[i-1]`is negative and cannot help;
* `sum[i-1] + nums[i]`, when `sum[i-1]` is positive.

##### Code

Below is the Java implementation:
{% highlight java %}
public class Solution {
    public int maxSubArray(int[] nums) {
        int N = nums.length;
        if(N==0) return 0;
        
        int sum[] = new int[N];
        sum[0] = nums[0];
        int max = sum[0];
        for(int i=1;i<N;i++){
            sum[i]= sum[i-1]>0?(sum[i-1]+nums[i]):nums[i];
            max = Math.max(max, sum[i]);
        }
        return max;
    }
}
{% endhighlight %}

* Time: O(N)
* Space: O(N)


<br>
<br>
<br>
<br>


---

### Leetcode 62 Unique Paths

##### problem description

Given `m * n` grid, find the number of unique paths from top-left to bottom right (can only move either down or right at any point of time)?

Note: `m` and `n` will be at most 100.

##### Solution:

> `dp[i][j]` represents the number of unique ways move from top-left to `(i, j)`

Properties:

* `dp[0][0] = 0` because `(0, 0)` is the starting point; 
* `dp[i][j] = dp[i-1][j] + dp[i][j-1]` is not out of boundary;
* `dp[m-1][n-1]` is the result.

Key considerations:

* time complexity: O(m * n)
* space complexity: O(m * n) or O(n)

##### Code

{% highlight java %}
public class Solution {
    public int uniquePaths(int m, int n) {
        if(m==1 && n==1) return 1;
        int[] dp = new int[n];
        dp[0] = 1;
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(i==0 && j==0){}
                else if(i==0) dp[j]=dp[j-1];
                else if(j==0) dp[j]=dp[j];
                else dp[j]=dp[j]+dp[j-1];
            }
        }
        return dp[n-1];
    }
}
{% endhighlight %}

* Time: O(m * n)
* Space: O(n)

<br>
<br>
<br>
<br>


---

### Leetcode 63 Unique Paths II

##### Problem Description

Follow up for `Unique Paths`.
Consider if some obstacles are added to te grids, how many unique paths would there be?<br>
An obstacle and empty space is marked as `1` and `0` respectively in the grid.

##### Solution

> Add condition check: If one point is an obstacle, it is unreachable and cannot help other point to make more paths.

Properties:

* `dp[i][j] = 0`, if `g[i][j] = 1`;
* `dp[i][j] = dp[i-1][j] + dp[i][j-1]`, if `g[i][j] = 0`;
* should consider edge case.

##### Code


{% highlight java %}
public class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.length;
        int n = obstacleGrid[0].length;
        if(obstacleGrid[0][0]==1) return 0;
        int[] dp = new int[n];
        dp[0] = 1;
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(obstacleGrid[i][j]==1){
                    dp[j]=0;
                    continue;
                }
                if(i==0 && j==0){}
                else if(i==0) dp[j]=dp[j-1];
                else if(j==0) dp[j]=dp[j];
                else dp[j]=dp[j-1]+dp[j];
            }
        }
        return dp[n-1];
    }
}
{% endhighlight %}

* Time: O(m * n)
* Space: O(n)


<br>
<br>
<br>
<br>

---

### Leetcode 64 Minimum Path Sum

##### Problem Description

Given a `m * n` grid with non-negative numbers, find a path from top-left to bottom-right which minimizes the sum of all number along its path.
<br>
Note: You can move either down or right at any point in time.

##### Solution

> We can always find the best solution by watch left and top, then choose the better one.

Properties:

* `dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + grid[i][j]`;
* `dp[m-1][n-1]` is the final solution;
* should consider edge case.


##### Code

{% highlight java %}
public class Solution {
    public int minPathSum(int[][] grid) {
        int M = grid.length, N = grid[0].length;
        int[] dp = new int[N];
        for(int i=0;i<M;i++){
            for(int j=0;j<N;j++){
                if(i==0 && j==0) dp[j] = grid[i][j];
                else if(i==0) dp[j]=grid[i][j]+dp[j-1];
                else if(j==0) dp[j]=grid[i][j]+dp[j];
                else dp[j]=Math.min(dp[j-1]+grid[i][j], dp[j]+grid[i][j]);
            }
        }
        return dp[N-1];
    }
}
{% endhighlight %}

* Time: O(m * n)
* Space: O(n)




<br>
<br>
<br>
<br>

---

{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}