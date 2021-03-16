# Java

## Table of Contents

## Useful Type

    	long

## Useful Constant

    	Long.Min_VALUE
    	Integer.MAX_VALUE
    	Integer.MIN_VALUE
    	null

## String:
```java
    	.length()
    	.charAt()
    	.compareTo(string2) // same if returns 0
    	.substring
    	.toCharArray()
    	String.valueOf(x)
```
## StringBuilder:
```java
    	StringBuilder sb = new StringBuilder()
    	sb.append('c')
        sb.insert(0, content)
        sb.setLength(0)
    	sb.toString()
```
## Array:
```java
    	Arrays.sort(arr)
    	Arrays.asList(1,2,3) // creates immutable list
    	.length
    	return new int[] {1,2,3}
```
## List:

    List is an interface
    The following class implements list interface :
    	ArrayList,LinkedList,Vector,Stack
```java
    List<Character> bucket[] = new List[s.length() + 1] // this list is fixed size!
    Liar<Integer> list = Arrays.asList(1,2,3) // immutable
```
## List::ArrayList:
```java
    	List<String> foo = new ArrayList<String>()
    	ArrayList<String> foo = new ArrayList<String>()
    	.add()
    	.toString()
```
## List::LinkedList:

    	//TODO

## Stack:
```java
    	Stack<Integer> stack = new Stack<int>()
    	.push()
    	.isEmpty()
    	.pop // does both return and pop
```
## Queue:
```java
    	Queue<Integer> q
    	.offer()
    	.add()
    	.peek() // retrieve only
    	.poll() // retrieve and remove
    	.size()
```
## PriorityQueue / Heap
```java
    	// Max Heap
    	PriorityQueue<Map.Entry<Character,Integer>> pq = new PriorityQueue<>((a,b) -> b.getValue() - a.getValue())

    	// Max Heap with custom comparator
    	PriorityQueue<Map.Entry<Character, Integer>> pq = new PriorityQueue<>(
    		new Comparator<Map.Entry<Character, Integer>>() {
    			@Override
    			public int compare(Map.Entry<Character, Integer> a, Map.Entry<Character, Integer> b) {
    				if(b.getValue()==a.getValue()){ return (int)a.getKey()-(int)b.getKey();}
    				return b.getValue() - a.getValue();
    			}
    		}
    	);

    	// Min Heap


    	.addAll(map.entrySet())
    	.poll()
```
## HashSet: Good for removing duplicates with fast operations
```java
    	HashSet<Integer> h = new HashSet<Integer>()
    	.contains() 
    	.add()
```        
## HashMap:
```java
    	Map<Character,Integer> map = new HashMap<>()
    	HashMap<Integer, String> foo = new HashMap<Integer, String>()
    	for(Integer key : foo.keySet())
    	.keySet() // <Set<K>
    	.values() // Collection<V>
    	.entrySet() // Set<Map.Entry<K,V>>
    	.get(key)
    	.getOrDefault(key,defaultValue)
    	.containsKey(target)
    	.put(key,value)
    	.isEmpty()
    	.size()
    	.clear()
```
## Conversion:
        Character -> Int       :  Character.getNumericValue()   |  x - '0'
    	String -> Char[]       :  .toCharArray()
        Char[] -> String       :  new String(temp)
    	Array -> String        :  Arrays.toString(arr)
    	Array -> List          :  Arrays.asList(1,2,3)
    	Integer -> String      :  Integer.toString(num)
    	List -> String         :  .toString()
    	List -> Array          :  .toArray()
    	List<T> -> Array<T>    :  .toArray(arr)
        List<Integer> -> int[] :  res.stream().mapToInt(i->i).toArray();
## Compare 

        Integer  :   Integer.compare(a,b)
        String   :   s1.equals(s2)  , s1.compareTo(s2)


## Comparator
```java
    new Comparator<T>() {
        @Override 
        public int comapre(T lhs , T rhs) {
            // Return 1 if rhs should be before lhs 
            // Return -1 if lhs should be before rhs 
            // Return 0 other (stay same order)
        }
    }

    Summary :
    lhs - rhs  for A-Z 
    rhs - lhs  for Z-A
```
## Comparable 

## Sorting:

    	Arrays.sort(arr,Collections.reverseOrder())
    	Arrays.sort()
    	Arrays.sort(arr,start,end)
        Collections.sort(arr, comparator)

## Useful Functions:

    	Min/Max:
    		Math.min(a,b)
    		Math.max(a,b)

## Specific Task (Application)
<details><br><summary>Array</summary>
<details>
    <summary>1528. Shuffle String</summary>

```java
class Solution {
    public String restoreString(String s, int[] indices) {
        char[] temp = s.toCharArray();
        for(int i = 0 ; i < indices.length; i++) {
            temp[indices[i]] = s.charAt(i);
        }
        return new String(temp);
    }
}
```
</details>
<details>
    <summary>1539. Kth Missing Positive Number</summary>

```java
/*
    Idea is keep track of how many # is missing as you go.
    when # of missing > k then do some math to figure out the res
*/
class Solution {
    public int findKthPositive(int[] arr, int k) {    
        int miss = 0;
        int prev = 0;
        for(int num : arr) {
            int diff = num - prev;
            miss += diff - 1; // -1 b/c dont count urself 
            if(miss >= k) {
                return num - (miss - k + 1);
            }
            prev = num;
        }
        /* captures cases like [1,2,3,4] 2   or [5,6,7,8,9] 9  */
        return prev + (k - miss); 
    }
}
```
</details>
<br></details> <!-- End Array -->
<details><summary>Binary Search</summary><br>
<details>
    <summary>General Binary Search Template </summary>

```java
/*
    [l,r)  search range includes l but not r 
    another way to put it is ... left is reachable and right is not.
*/
    int left = 0, right = arr.length 
    while(left < right) {
        int mid = (left + right) / 2
        if() left = mid + 1
        else right = mid
    }
/*
    (l,r) search range includes l and r  ,  that is both l and r is reachable 
*/
    int left = 0, right = arr.length - 1 
    while(left <= right) {
        int mid = (left + right) / 2
        if() left = mid + 1 
        else right = mid - 1
    }
```
</details>
<details>
    <summary>1539. Kth Missing Positive Number</summary>

```java
/*
    # of missing number in index i  is  arr[i] - (i + 1)
    Using this idea , use binary search to find the 1st number with missing number > k. From that point just move backward or forward to find the final answer.
*/
class Solution {
    public int findKthPositive(int[] arr, int k) {    
        if(arr[0] > k) return k;
		// Use Binary Search to find 1st # > k 
		int left = 0;
		int right = arr.length - 1;
		int numMissing;
		int mid;

		while(left < right) {
			mid = (left+right) / 2;
			numMissing =  arr[mid] - (mid + 1);
			if(numMissing < k) left = mid + 1;
			else right = mid;
		}
		numMissing = arr[left] - (left + 1);
		if(numMissing < k) {
			return arr[left] + (k - numMissing); // go forward
		}else {
			return arr[left] - (numMissing - k + 1); // go backward
		}
    }
}
```
```java
/*
    Simplified previous version. 


    miss = arr[i] - (i+1) = arr[i] - i - 1
    Res = arr[i] - (miss - k + 1) 

    = arr[i] - (arr[i] - i - 1 - k + 1)
    = arr[i] - arr[i] + i + 1 + k - 1
    = i + k 

    
    Use example [2,3,4,7,11] k = 5 
    Binary search will end the search at 11 which is index 4
    miss = 11 - (4 + 1) = 6
    Res = 11 - (6 - 5 + 1 ) = 11 - 2 = 9
*/
public static int findKthPositive(int [] A, int k) {
    int l = 0, r = A.length, m;
    while (l < r) {
        m = (l + r) / 2;
        int left = A[m] - 1 - m;
        if (A[m] - 1 - m < k)
            l = m + 1;
        else
            r = m;
    }
    return l + k;
}
```
</details>
<br></details> <!-- End Binary Search -->
<details><summary>Heap</summary><br>
<details>
    <summary>Sort Element by Frequency</summary>
    <h5> A-Z order </h5>

``` 
        1. Count frequency of each character 
        2. Insert each map entry to maxheap
``` 
```java
        String s = "aabbbcccc";
        Map<Character, Integer> map = new HashMap<>();
		for(char c : s.toCharArray()) {
			map.put(c, map.getOrDefault(c, 0) + 1);
		}
        PriorityQueue<Map.Entry<Character, Integer>> maxHeap = new PriorityQueue<>((a,b) -> b.getValue() - a.getValue());
		maxHeap.addAll(map.entrySet());
```
</details>
<details>
    <summary>Sort Word by Frequency</summary>
    <h5> A-Z order </h5>

```
        1. Count frequency of each word 
        2. Insert each map entry to maxheap 
```
```java
        String words[] = {"word1","word2","word2","word3","word3","word3"};
        Map<String, Integer> map = new HashMap<>();
        for(String s : words) {
            map.put(s, map.getOrDefault(s, 0) + 1);
        }
        PriorityQueue<Map.Entry<String,Integer>> maxHeap = new PriorityQueue<>((a,b) -> b.getValue() - a.getValue());
        maxHeap.addAll(map.entrySet());
```
</details>
<details>
    <summary>Top K Frequent Words</summary>

```java
    1. Sort Words by Frequency
    2. Get from top of heap k times to build result 
```
</details>
<details>
    <summary>Top K Frequent Number</summary>
    <h5> A-Z order </h5>

```java
    public int[] topKFrequent(int[] nums, int k) {
        // build  Max heap from all element
        // loop k times to get max from max heap
        HashMap<Integer, Integer> map = new HashMap<>();
        for(Integer x : nums) {
            map.put(x, map.getOrDefault(x,0) + 1);
        }
        PriorityQueue<Map.Entry<Integer,Integer>> maxHeap = new PriorityQueue<>((a,b) -> b.getValue() - a.getValue());
        maxHeap.addAll(map.entrySet());
        int[] res = new int[k];
        for(int i = 0 ; i < k; i++) {
            res[i] = maxHeap.poll().getKey();
        }
        return res;
    }
```
</details>
<details>
    <summary>1029. Two City Scheduling</summary>

```java
/**
    Idea is to priortize picking person with greater difference. 
    1. Sort the pairs by difference in Z-A order , if two diff equals, sort by greater sum 
    2. Now for each element in MAXPQ, can safely select CityA or B by looking at whichever is lower cost.
*/

class Solution {
    public int twoCitySchedCost(int[][] costs) {
        PriorityQueue<int[]> pq = new PriorityQueue<>((a,b) -> {
            int diffA = Math.abs(a[0] - a[1]);
            int diffB = Math.abs(b[0] - b[1]);
            if(diffA == diffB) {
                return (b[0]+b[1]) - (a[0]+a[1]);
            }
            return diffB - diffA;
        });
        int res = 0;
        for(int[] row : costs) {
            pq.add(row);
        }
        
        int numA = costs.length / 2;
        int numB = numA;
        while(!pq.isEmpty()) {
            int[] node = pq.poll();
            // Still have spot in A  and going A is cheaper than B 
            if( (numA > 0 && node[0] <= node[1])  || numB == 0) {
                res += node[0];
                numA--;
            }
            // Still have spot in B and going B is cheaper than A
            else if((numB > 0 && node[1] < node[0]) || numA == 0) {
                res += node[1];
                numB--;
            }
        }
        return res;
    }
}
```
```java
/*
    1. Choose A for all 
    2. Compute the refund amount for each person that is how much more is needed if person i switches to B 
        Refund[i] = Cost of B - Cost of A. This value will be negative if going B is cheaper than A
    3. Sort refund to see who gets more refund by switching to B 
    4. Now select half of the people to switch to B  based on the sorted refund array 
*/
class Solution {
	
	public int twoCitySchedCost(int[][] costs) {
		
		int totalCost = 0;
        // Chooses A for all 
		for(int[] cost : costs) 
			totalCost += cost[0];
		
        // Find out how much each refund each person if switch to B 
		int[] refund = new int[costs.length];
		for(int i = 0; i < costs.length; i++) 
			refund[i] = costs[i][1] - costs[i][0];
		
		Arrays.sort(refund);
		
        // Select exactly half of people with highest refund amount switch to B
		for(int i = 0; i < refund.length / 2; i++) 
			totalCost += refund[i];
	
		return totalCost;
	}
}
```
```java
/*
    dp(i,j) = minimum cost of choosing i people to A and j people to B
    dp(i,j) = min(cost of choose A + dp(i-1 , j )  ,  cost of choose B + dp(i, j-1))
*/
class Solution {
    public int twoCitySchedCost(int[][] costs) {
        int N = costs.length / 2;
        int[][] dp = new int[N + 1][N + 1];
        for (int i = 1; i <= N; i++) {
            dp[i][0] = dp[i - 1][0] + costs[i - 1][0];
        }
        for (int j = 1; j <= N; j++) {
            dp[0][j] = dp[0][j - 1] + costs[j - 1][1];
        }
        for (int i = 1; i <= N; i++) {
            for (int j = 1; j <= N; j++) {
                dp[i][j] = Math.min(dp[i - 1][j] + costs[i + j - 1][0], dp[i][j - 1] + costs[i + j - 1][1]);
            }
        }
        return dp[N][N];
    }
}
```
</details>
<br>
</details>

<details >
<summary>Bucket Sort</summary>
<br>
<details >
    <summary>Sort Element by Frequency</summary>
    <h5> A-Z order </h5>

```
        
        Bucket Key = Frequency 
        Max Frequency = String Size = Bucket Size 

        1. Count frequency of each Element , which can be numbers,words,characters...
        2. Add frequency of each element to bucket 
```

```java
        String s = "aabbbcccc";
        Map<Character, Integer> map = new HashMap<>();
		for(char c : s.toCharArray()) {
			map.put(c, map.getOrDefault(c, 0) + 1);
		}

        int bucketSize = s.length() + 1;
		List<Character> bucket[] = new List[bucketSize];
		for(char key : map.keySet()) {
			int val = map.get(key);
			if(bucket[val] == null) bucket[val] = new ArrayList<>();
			bucket[val].add(key);
		}
```
</details>
<br>
</details>


<details>
<br>
<summary>Two Pointers</summary>
<details>
    <summary>Two Sum</summary>

```java
    1. Sort the container 
    2. Have two pointers left,right on each end
    3. advance left pointer if left+right < target , which will increase sum closer to target 
       advance right pointer if left+right > target , which will decrease sum closer to target 

    Arrays.sort(nums);
    int left = 0;
    int right = nums.length -1;
    while(left < right) {
        int sum = nums[left] + nums[right];
        if(sum < target) left++;
        if(sum > target) right--;
        if(sum == target) return new int[]{nums[left],nums[right]};
    }
```
</details>
<details>
    <summary>Three Sum</summary>
    <h5>Find all unique triplets in array that sum to target</h5>

```java
    1. Sort container 
    2. Pick a number then the problem reduce to Two Sum 

    Note: must do a duplicate check to get unique triplets 

    Arrays.sort(nums);
    List<List<Integer>> res = new ArrayList<>();
    for(int i = 0 ; i < nums.length - 2; i++) {
        if(i > 0 && nums[i] == nums[i-1]) continue; // skip duplicate 
        int left = i+1;
        int right = nums.length - 1;
        while(left < right) {
            int sum = nums[i] + nums[left] + nums[right];
            if(sum == target) {
                res.add(Arrays.asList(nums[i],nums[left],nums[right]));
                left++;
                right--;
                while(left < right && nums[left] == nums[left - 1]) left++; // Skip duplicate
                while(left < right && nums[right] == nums[right + 1]) right--; // Skip duplicate
            }
            if(sum < target) left++
            if(sum > target) right--;
        }
    }   
```
</details>
<details>
    <summary>Three Sum Closest</summary>
    <h5>Sum of three integer closest to target, assume exactly 1 solution</h5>

```java
    
    /*
        same as 3sum but no need to check duplicate 
        Store the minimum gap so far 
    */
    Arrays.sort(nums);
    int res = 0;
    int min = Integer.MAX_VALUE;
    for(int i = 0 ; i < nums.length-2 ; i++) {
        int j = i+1;
        int k = nums.length -1;
        while(j < k) {
            int sum = nums[i] + nums[j] + nums[k];
            if(sum < target) j++;   
            else if(sum == target) return sum;
            else k--;
            int gap = Math.abs(target-sum);
            if(gap < min) {
                res = sum;
                min = gap;
            }
        }
    }
    return res;
```
</details>
<details>
    <summary>Three Sum Smaller</summary>
    <h5>Count # of triplets smaller than target</h5>

```java
    /*
        Idea is that once a triplet(i,j,k) is found to be less than target
        then all the numbers between j and k is also smaller than target
    */
    int res = 0;
    Arrays.sort(num);
    for(int i = 0; i < nums.length; i++) {
        int left = i + 1;
        int right = nums.length - 1;
        while(left < right) {
            int sum = nums[i] + nums[left] + nums[right];
            if(sum < target) {
                res += right-left 
                left++;
            } else k--;
        }
    }
    return res;
```
</details>
<details>
    <summary>Four Sum</summary>
    <h5>Find all unique 4 numbers a,b,c,d in array that sum up to target</h5>

```java
    /*
        Idea is to pick 2 numbers then use 2Sum 
    */
    Arrays.sort(nums);
    for(int i = 0 ; i < nums.length-3; i++) {
        if(i > 0 && nums[i] == nums[i-1]) continue;
        for(int j = i + 1; j < nums.length-2; j++) {
            if(j > i+1 && nums[j] == nums[j-1]) continue;
            int left = j + 1;
            int right = nums.length - 1;
            while(left < right) {
                int sum = nums[i] + nums[j] + nums[left] +  nums[right];
                if(sum == target) {
                    res.add(Arrays.asList(nums[i],nums[j],nums[left],nums[right]));
                    left++;
                    right--;
                    while(left < right && nums[left] == nums[left-1]) left++;
                    while(left < right && nums[right] == nums[right+1]) right--; 
                } else if(sum < target) left++;
                else right--;
            }
        }
    }
    return res;
```
</details>
<details>
    <summary>Four Sum II</summary>
    <h5> </h5>

```java

```
</details>
<details>
    <summary>K Sum</summary>
    <h5>Get a list of list(k elements) that sums to target</h5>

```java
    public List<List<Integer>> kSum(int[] nums, int target) {
        List<List<Integer>> result = new ArrayList<>();
        Arrays.sort(nums);
        kSum(result, new ArrayList<>(), nums, 0, target, 4);
        return res;
    }

    private void kSum(List<List<Integer>> result, List<Integer> curr, int[] nums, int start, int target, int k) {
        if(nums == null                      ||
           start + k > nums.length           ||
           nums[start] * k > target          ||
           nums[nums.length -1] * k > target) return;

        if(k == 2) {
            int left = start;
            int right = nums.length - 1;
            while(left < right) {
                int sum = nums[left] + nums[right];
                if(sum == target) {
                    List<Integer> temp = new ArrayList<>(curr);
                    temp.add(nums[left]);
                    temp.add(nums[right]);
                    result.add(temp);

                    left++;
                    right--;
                    while(left < right && nums[left] == nums[left - 1]) left++; // Skip duplicate 
                    while(left < right && nums[right] == nums[right + 1]) right--; // Skip duplicate
                }
            }
        } else {
            for(int i = start; i < nums.length; i++) {
                if(i > start && nums[i] == nums[i-1]) continue;
                curr.add(nums[i]);
                kSum(result, curr, nums, i, target - nums[i], k-1);
                curr.remove(curr.size() -1); // backtrack
            }
        }
    }
    
```
</details>
<br>
</details>


<details>
<summary>Map/HashTable</summary>
<br>
<details>
    <summary>Two Sum</summary>
    
```java
    /*
        Idea is to hash all numbers as you see them and check if the complement exists in map. 
    */
    Map<Integer, Integer> numMap = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        if (numMap.containsKey(target - nums[i])) {
            int[] answerPair = {numMap.get(target - nums[i]), i};
            return answerPair;
        } else {
            numMap.put(nums[i], i);
        }
    }
```
</details>
<details>
    <summary>Two Sum IV - Input is a BST</summary>
    <h5>Return true if there exists two element that sums to target</h5>

```java
    Set<Integer> set = new HashSet<>();
    public boolean findTarget(TreeNode root, int k) {
        if(root == null) return false;
        if(set.contains(k - root.val)) return true;
        set.add(root.val);
        return findTarget(root.left , k) || findTarget(root.right, k);
    }
```
</details>
<details>
    <summary>4Sum II</summary>
    <h5>How many tuples(i,j,k,l) there are such that A[i] + B[j] + C[k] + D[l] is 0</h5>

```java
    /*
        Idea is to get the frequency of all possible A+B sums then the problem reduce to 2Sum 
    */
    HashMap<Integer,Integer> map = new HashMap<>();
    int count = 0;
    for (int x: A)
        for (int y: B)
            map.put(x+y,map.getOrDefault(x+y,0)+1);

        for (int x: C) {
        for (int y: D) {
            if(map.containsKey(-(x+y))) {
                count += map.get(-(x+y));
            }
        }
        }
    return count;
```
</details>
<details>
    <summary>1539. Kth Missing Positive Number</summary>

```java

/*
    Start counting from 1 to inf.
    check if number is in array.. if not then you know is missing. 
    Terminate when kth search miss happens. 
*/
class Solution {
    public int findKthPositive(int[] arr, int k) {
        Set<Integer> nums = new HashSet<>();
        for (int i = 0; i < arr.length; i++) {
            nums.add(arr[i]);
        }
        int count = 1;
        while (k > 0) {
            if (!nums.contains(count++)) k--;
        }
        return count - 1;
    }
}
/*
    Faster Solution by just doing some math to find out res 
    that is.. keep track of how many # is missing so far..
*/
class Solution {
    public int findKthPositive(int[] arr, int k) {    
        int miss = 0;
        int prev = 0;
        for(int num : arr) {
            int diff = num - prev;
            miss += diff - 1; // -1 b/c dont count urself 
            if(miss >= k) {
                return num - (miss - k + 1); // go backward
            }
            prev = num;
        }
        /* captures cases like [1,2,3,4] 2   or [5,6,7,8,9] 9  */
        return prev + (k - miss); // go forward
    }
}
```
</details>
<br></details> <!-- End Map/HashTable -->
<details><summary>Depth First Search</summary><br>
<details>
    <summary>394. Decode String</summary>

```java
    /*
        Input: s = "3[a2[c]]"
        Output: "accaccacc"

        Use a stack to save content prior to seeing a number 
        Use another stack to save repeat amount 

    */
    public String decodeString_Stack(String s) {
        Stack<Integer> stackNum = new Stack<>();
        Stack<StringBuilder> stackCha = new Stack<>();
        StringBuilder str = new StringBuilder();
        int num = 0;
        for (int i = 0; i < s.length(); i++){
            if (Character.isDigit(s.charAt(i))){
                num = num * 10 + s.charAt(i) - '0';
            }
            else if (s.charAt(i) == '['){
                stackNum.push(num); //saves substring collected before [
                stackCha.push(str);

                //Reset
                num= 0;
                str = new StringBuilder();
            }
            else if (s.charAt(i) == ']'){
                StringBuilder temp = str; // substring collected so far is to be repeated 
                str = stackCha.pop(); // restore the substring that comes before [
                int numTimes = stackNum.pop();
                for (int j = 0; j < numTimes; j++){
                    str.append(temp);
                }
            }
            else{
                str.append(s.charAt(i));
            }
        }
        return str.toString();
    }
```
</details>
<details>
    <summary>501. Find Mode in Binary Search Tree</summary>
    <h5>Find the most frequent element in BST</h5>

```java
    /*
        Idea is to run DFS inOrder traversal which will visit all the nodes in A-Z order 
        then count each node if is the same or reset count if is different. 
    */
    int count;
	int max;
    TreeNode prev;
	public int[] findMode(TreeNode root) {
		if(root == null) return new int[0];
		count = 1; // frequency of current node
		max = 1; // max frequency so far
		List<Integer> res = new ArrayList<>();
		dfs(root,res);
		return res.stream().mapToInt(i->i).toArray();
    }

	private void dfs(TreeNode root, List<Integer> res) {
		if(root == null) return;
        // Left
		dfs(root.left, res);
        // ME
		if(prev != null) {
			if(prev.val == root.val) count++;
			else count = 1;
		} 
		if(count == max) {
			res.add(root.val);
		} else if( count > max) {
			max = count;
			res.clear();
			res.add(root.val);
		}
		prev = root;
        // Right 
		dfs(root.right, res);
	}

```
</details>
<details>
    <summary>112. Path Sum</summary>
    <h5>Pre-Order Traversal / Path Traversal </h5>

```java
class Solution {
    public boolean hasPathSum(TreeNode root, int targetSum) {
        if (root == null) return false;
        if(root.left == null && root.right == null && targetSum == root.val ) return true;
        return hasPathSum(root.left , targetSum - root.val) || hasPathSum(root.right, targetSum - root.val);
    }   
}
```
</details>
<details>
    <summary>113. Path Sum II</summary>

```java
/* 
    Do a pre-order traversal and pass along a path
    when this path reaches the end then add to res if path sums to targetSum 
    path backtrack is required 
*/
class Solution {
    List<List<Integer>> res;
    public List<List<Integer>> pathSum(TreeNode root, int targetSum) {
        res = new ArrayList<>();
        helper(root,  targetSum , new ArrayList<Integer>());
        return res;
    }
    
    private void helper(TreeNode root, int targetSum, ArrayList<Integer> path ) {
        if(root == null) return;
        if(root.left == null && root.right == null && root.val == targetSum) {
            path.add(root.val);
            res.add(new ArrayList<Integer>(path));
            path.remove(path.size() - 1); //backtrack 
            return;
        }
        path.add(root.val);
        helper(root.left, targetSum - root.val , path ); 
        helper(root.right, targetSum - root.val , path );
        path.remove(path.size() - 1); // backtrack 
        
    }
}
```
</details>
<details>
    <summary>98. Validate Binary Search Tree</summary>

```java
/*
    If a tree is BST , then inorder traversal should visit all elements in A-Z order
*/
class Solution {
    TreeNode prev;
    Boolean res = true;
    public boolean isValidBST(TreeNode root) {
        dfs(root);
        return res;
    }
    
    private void dfs(TreeNode root) {
        if(res == false || root == null) return;
        isValidBST(root.left);   
        if(prev != null && prev.val >= root.val) res = false;
        prev = root;
        isValidBST(root.right);    
    }
    
}
```
```java
/*
    Recursion : using properties of a BST 
*/
class Solution {
    public boolean isValidBST(TreeNode root) {
        return helper(root, null,null);
    } 
    
    private boolean helper(TreeNode root , TreeNode min , TreeNode max) {
        if(root == null) return true;
        if(min != null && root.val <= min.val) return false;
        if(max != null && root.val >= max.val) return false;
        return helper(root.left, min, root) && helper(root.right, root, max);
    }
}
```
</details>
<details>
    <summary>22. Generate Parentheses</summary>

```java
/*
    DFS + Backtrack + Branch n Bound

    For each option opt in Options["(" , ")"]
        choose opt 
        explore
        unchoose opt 
*/
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> res = new ArrayList<>();
        helper(res, new char[n * 2], 0, 0, 0);
        return res;
    }

    public void helper(List<String> res, char[] temp, int index, int left, int right) {
        if (temp.length == index) {
            if (left == right) {
                res.add(new String(temp));
                return;
            }
        }
        if (index >= temp.length) return;
        // if remaining spot >= left , b/c if is not.. then not enough spot to balance (
        boolean potential = (temp.length - 1) >= left;
        // # of (   >   # of )  , b/c if is not.. then is an invalid start
        boolean rightPotential = left > right;
        temp[index] = '(';
        if (potential) helper(res, temp, index + 1, left + 1, right);
        temp[index] = ')';

        if (rightPotential) helper(res, temp, index + 1, left, right + 1);
    }

}
```
</details>
<details>
    <summary></summary>
    <h5> </h5>

```java

```
</details>
<br> </details> <!-- End DFS -->
<details><br>
<summary>Dynamic Programming</summary>
<details>
    <summary>64. Minimum Path Sum</summary>
    <h5>mxn grid find minimum cost from 0,0 to m-1,n-1  , can only move down or right</h5>

```java
/*
    dp(i,j) = min( dp(i+1,j) , dp(i,j+1) ) if i+1,j+1 is in range 
    dp(i,j) = dp(i, j+1) if i+1 is not in range and j+1 is 
    dp(i,j) = dp(i+1 , j ) if j+1 is not in range and i+1 is 
*/
public int minPathSum(int[][] grid) {
        int m = grid.length - 1 , n = grid[0].length - 1;
        for(int i = m ; i >= 0 ; i --) {
        for(int j = n ; j >= 0 ; j--) {
            if(i == m && j != n) grid[i][j] += grid[i][j+1];
            if(i != m && j == n) grid[i][j] += grid[i+1][j];
            if(i != m && j != n) grid[i][j] = Math.min(grid[i+1][j] , grid[i][j+1]) + grid[i][j];
        }
        }
        return grid[0][0];
    }
}

// Alternative :  Realizing path can go any direction, that is treating the m-1,n-1 as starting point also work 
public int minPathSum(int[][] grid) {
    int m = grid.length, n = grid[0].length;
    for(int i = 0; i < m; i++){
        for(int j = 0; j < n; j++){
        if(i == 0 && j != 0) grid[i][j] += grid[i][j-1];
        if(i != 0 && j == 0) grid[i][j] += grid[i-1][j];
        if (i != 0 && j != 0) grid[i][j] += Math.min(grid[i-1][j], grid[i][j-1]);
        }
    }
    return grid[m-1][n-1];
}

// Alternative Top Down Approach 
public int minPathSum(int[][] grid) {
    return helper(grid, 0 , 0, new int[grid.length][grid[0].length]);
}

private int helper(int[][] grid, int i , int j , int[][] dp) {
    // out of bound 
    if(i == grid.length  || j == grid[0].length) return Integer.MAX_VALUE;
    
    // If answer is computed before 
    if(dp[i][j] != 0) return dp[i][j];
    
    // base case 
    if(i == grid.length - 1 && j == grid[0].length - 1) return grid[i][j];
    
    dp[i][j] = grid[i][j] + Math.min(helper(grid, i+1, j , dp) , helper(grid, i , j+1, dp));
    return dp[i][j];
}
```
</details>
<details>
    <summary>62. Unique Paths</summary>
    <h5># of unique paths from 0,0 to lower right corner in a mxn grid , can only move down or right</h5>

```java
/*
    dp(i,j) =  dp(i+1,j) + dp(i,j+1) ) if i+1,j+1 is in range 
*/
// Bottom up
public int uniquePaths(int m, int n) {
    int[] dp = new int[n];
    dp[0] = 1;
    for(int i = 0 ; i < m; i++) {
        for(int j = 1 ; j < n; j++) {
            dp[j] = dp[j] + dp[j-1] // UP + LEFT 
        }
    }
    return dp[n-1];
}
// Bottom up  , again can reverse the for loop treating start point at lower right corner 
public int uniquePaths(int m, int n) {
    int[][] dp = new int[m][n];
    dp[0][0] = 1;
    for(int i = 0 ; i < m; i++) {
        for(int j = 0 ; j < n; j++) {
            if(i == 0 && j > 0) dp[i][j] = dp[i][j-1];
            if(i > 0 && j == 0) dp[i][j] = dp[i-1][j];
            if(i !=0 && j != 0) dp[i][j] = dp[i-1][j] + dp[i][j-1];
        }
    }
    return dp[m-1][n-1];
}
// Top Down Approach 
public static int helper(int[][] dp , int i , int j) {
    // out of bound 
    if(i == dp.length || j == dp[0].length) return 0;

    // ans computed previously
    if(dp[i][j] != 0) return dp[i][j];

    // base case ( 1 unit away from dst ) left or above
    if((i == dp.length - 1 && j == dp[0].length - 2) || 
        (i == dp.length -2 && j == dp[0].length -1)) {
        dp[i][j] = 1;
        return 1;
    }

    dp[i][j] = helper(dp, i , j+1) + helper(dp, i+1, j);
    return dp[i][j];
}

public static int uniquePaths(int m, int n) {
    if(m == 1 && n == 1) return 1;
    return helper(new int[m][n],0,0);
}
```
</details>
<details>
    <summary>63. Unique Paths II</summary>
    <h5>Same as Unique Paths I , except a cell can be blocked if grid[i][j] == 1</h5>

```java
// Idea is same as 62. Unique Paths, now if a cell is obstacle then dp[i][j] is 0 otherwise same logic as 62.
public int uniquePathsWithObstacles(int[][] obstacleGrid) {
    int width = obstacleGrid[0].length;
    int[] dp = new int[width];
    dp[0] = 1;
    for (int[] row : obstacleGrid) {
        for (int j = 0; j < width; j++) {
            if (row[j] == 1)
                dp[j] = 0;
            else if (j > 0)
                dp[j] += dp[j - 1];
        }
    }
    return dp[width - 1];
}

// Top Down Approach 
public static int helper(int[][] dp , int i , int j,int [][] obstacleGrid) {
    // out of bound 
    if(i == dp.length || j == dp[0].length) return 0;
    
    // Ans computed previously 
    if(dp[i][j] != 0) return dp[i][j];
    
    // base case some easy case 
    if(obstacleGrid[i][j] == 1) {
        dp[i][j] = 0;
        return 0;
    }
    if(i == dp.length - 1 && j == dp[0].length -1) {
        dp[i][j] = 1;
        return 1;
    }

    dp[i][j] = helper(dp, i , j+1 , obstacleGrid) + helper(dp, i+1, j , obstacleGrid);

    return dp[i][j];
}

public static int uniquePathsWithObstacles(int[][] obstacleGrid) {
    int m = obstacleGrid.length;
    int n = obstacleGrid[0].length;
    if(obstacleGrid[m-1][n-1] == 1) return 0;
    if(obstacleGrid[0][0] == 1) return 0;
    if(m == 1 && n == 1) return 1;
    return helper(new int[m][n],0,0,obstacleGrid);
}
```
</details>
<details>
    <summary>1029. Two City Scheduling</summary>

```java
/*
    dp(i,j) = minimum cost of choosing i people to A and j people to B
    dp(i,j) = min(cost of choose A + dp(i-1 , j )  ,  cost of choose B + dp(i, j-1))
*/
class Solution {
    public int twoCitySchedCost(int[][] costs) {
        int N = costs.length / 2;
        int[][] dp = new int[N + 1][N + 1];
        for (int i = 1; i <= N; i++) {
            dp[i][0] = dp[i - 1][0] + costs[i - 1][0];
        }
        for (int j = 1; j <= N; j++) {
            dp[0][j] = dp[0][j - 1] + costs[j - 1][1];
        }
        for (int i = 1; i <= N; i++) {
            for (int j = 1; j <= N; j++) {
                dp[i][j] = Math.min(dp[i - 1][j] + costs[i + j - 1][0], dp[i][j - 1] + costs[i + j - 1][1]);
            }
        }
        return dp[N][N];
    }
}
```
</details>
<br></details> <!-- End Dynamic Programming -->
<details><br><summary>Greedy Algorithm</summary>
<details>
    <summary>1029. Two City Scheduling</summary>
    <h5>Greedy Choice is to first assign person greatest impact that is diff(b-a) is the highest </h5>

```java
/**
    Idea is to priortize picking person with greater difference. 
    1. Sort the pairs by difference in Z-A order , if two diff equals, sort by greater sum 
    2. Now for each element in MAXPQ, can safely select CityA or B by looking at whichever is lower cost.
*/

class Solution {
    public int twoCitySchedCost(int[][] costs) {
        PriorityQueue<int[]> pq = new PriorityQueue<>((a,b) -> {
            int diffA = Math.abs(a[0] - a[1]);
            int diffB = Math.abs(b[0] - b[1]);
            if(diffA == diffB) {
                return (b[0]+b[1]) - (a[0]+a[1]);
            }
            return diffB - diffA;
        });
        int res = 0;
        for(int[] row : costs) {
            pq.add(row);
        }
        
        int numA = costs.length / 2;
        int numB = numA;
        while(!pq.isEmpty()) {
            int[] node = pq.poll();
            // Still have spot in A  and going A is cheaper than B 
            if( (numA > 0 && node[0] <= node[1])  || numB == 0) {
                res += node[0];
                numA--;
            }
            // Still have spot in B and going B is cheaper than A
            else if((numB > 0 && node[1] < node[0]) || numA == 0) {
                res += node[1];
                numB--;
            }
        }
        return res;
    }
}
```
```java
/*
    1. Choose A for all 
    2. Compute the refund amount for each person that is how much more is needed if person i switches to B 
        Refund[i] = Cost of B - Cost of A. This value will be negative if going B is cheaper than A
    3. Sort refund to see who gets more refund by switching to B 
    4. Now select half of the people to switch to B  based on the sorted refund array 
*/
class Solution {
	
	public int twoCitySchedCost(int[][] costs) {
		
		int totalCost = 0;
        // Chooses A for all 
		for(int[] cost : costs) 
			totalCost += cost[0];
		
        // Find out how much each person gets refund if switch to B 
		int[] refund = new int[costs.length];
		for(int i = 0; i < costs.length; i++) 
			refund[i] = costs[i][1] - costs[i][0];
		
		Arrays.sort(refund);
		
        // Select exactly half of people with highest refund amount switch to B
		for(int i = 0; i < refund.length / 2; i++) 
			totalCost += refund[i];
	
		return totalCost;
	}
}
```
</details>
<br></details> <!-- End Greedy Algorithm -->



<details>
    <summary></summary>
    <h5> </h5>

```java

```
</details>
