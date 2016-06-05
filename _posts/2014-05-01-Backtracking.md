---
layout: post
title:  "Backtracking"
tldr: false
audio: false
categories: algorithm backtracking
---
    
## Backtracking
  
<br>
<br>
<br>
<br>

---

## Examples

<br><br>


### Leetcode 39 Combination Sum

##### Problem description: 

Given a set of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

The same repeated number may be chosen from C unlimited number of times.

Note:
All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.

	For example, given candidate set [2, 3, 6, 7] and target 7, 
	A solution set is: 
	[
	  [7],
	  [2, 2, 3]
	]

##### Solution: 


##### Code

Below is the Pseudo code for check and compute for `cj`: 



{% highlight java %}
public class Solution {
    public void sortColors(int[] nums) {
        int N = nums.length;
        int s = 0, t = N - 1, i = 0;
        int tmp;
        while (i <= t) {
            if (nums[i] == 0) {
                tmp = nums[i];
                nums[i++] = nums[s];
                nums[s++] = tmp;
            } else if (nums[i] == 2) {
                tmp = nums[i];
                nums[i] = nums[t];
                nums[t--] = tmp;
            } else {
                i++;
            }
        }
    }
}
{% endhighlight %}


* Time: O(N log N)
* Space: O(1)


<br>
<br>
<br>
<br>


---


### Leetcode 40 Combination Sum II

##### Problem description
Given a collection of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

Each number in C may only be used once in the combination.

Note:
All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.

	For example, given candidate set [10, 1, 2, 7, 6, 1, 5] and target 8, 
	A solution set is: 
	[
	  [1, 7],
	  [1, 2, 5],
	  [2, 6],
	  [1, 1, 6]
	]



##### Solution

##### Code

{% highlight java %}
public class Solution {
    
    Map<Integer, Integer> map = new HashMap<>();

    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        for (int x : candidates) {
            if (!map.containsKey(x)) map.put(x, 1);
            else map.put(x, map.get(x) + 1);
        }

        List<List<Integer>> resList = new ArrayList<>();

        if (map.containsKey(target))
            resList.add(new ArrayList<>(Arrays.asList(target)));

        for (int i = 1; target - i >= i; i++) {
            haha(resList, new ArrayList<Integer>(), i, target - i);
        }
        return resList;
    }


    private void haha(List<List<Integer>> resList, List<Integer> list, int x, int y) {
        if (!map.containsKey(x)) return;
        if (map.get(x) == 0) return;

        //remove this element
        map.put(x, map.get(x) - 1);

        List<Integer> tmpList;

        if (map.containsKey(y)) {
            if (map.get(y) > 0) {
                tmpList = copyList(list);
                tmpList.add(x);
                tmpList.add(y);
                resList.add(tmpList);
            }
        }

        tmpList = copyList(list);
        tmpList.add(x);

        for (int i = x; y - i >= i; i++) {
            haha(resList, tmpList, i, y - i);
        }

        //return this element
        map.put(x, map.get(x) + 1);

    }

    private List<Integer> copyList(List<Integer> list) {
        List<Integer> resList = new ArrayList<>();
        for (int x : list) resList.add(x);
        return resList;
    }


}
{% endhighlight %}







<br>
<br>
<br>
<br>

---


### Leetcode 216. Combination Sum III

##### Problem description
Find all possible combinations of k numbers that add up to a number n, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.


	Example 1:
	Input: k = 3, n = 7
	Output:
	[[1,2,4]]
	
	Example 2:
	Input: k = 3, n = 9
	Output:
	[[1,2,6], [1,3,5], [2,3,4]]



##### Solution

##### Code

{% highlight java %}
public class Solution {
    
    Map<Integer, Integer> map = new HashMap<>();

    public List<List<Integer>> combinationSum3(int k, int n) {
        for (int i = 1; i < 10; i++) map.put(i, 1);
        List<List<Integer>> resList = new ArrayList<>();

        if (map.containsKey(n) && k == 1) {
            resList.add(new ArrayList<>(Arrays.asList(n)));
        } else {
            for (int i = 1; n - i >= i; i++) {
                haha(resList, new ArrayList<Integer>(), i, n - i, k);
            }
        }
        return resList;
    }


    private void haha(List<List<Integer>> resList, List<Integer> list, int x, int y, int k) {
        if (!map.containsKey(x)) return;
        if (map.get(x) == 0) return;


        //remove this element
        map.put(x, map.get(x) - 1);

        List<Integer> tmpList;

        if (list.size() + 2 == k) {
            if (map.containsKey(y)) {
                if (map.get(y) > 0) {
                    tmpList = copyList(list);
                    tmpList.add(x);
                    tmpList.add(y);
                    resList.add(tmpList);
                }
            }
        } else {

            tmpList = copyList(list);
            tmpList.add(x);
            for (int i = x; y - i >= i; i++) {
                haha(resList, tmpList, i, y - i, k);
            }
        }

        //return this element
        map.put(x, map.get(x) + 1);

    }

    private List<Integer> copyList(List<Integer> list) {
        List<Integer> resList = new ArrayList<>();
        for (int x : list) resList.add(x);
        return resList;
    }
}
{% endhighlight %}







<br>
<br>
<br>
<br>

----

{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}