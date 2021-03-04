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
    	sp.append('c')
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

    	String -> Char[]    :  .toCharArray()
    	Array -> String     :  Arrays.toString(arr)
    	Array -> List       :  Arrays.asList(1,2,3)
    	Integer -> String   :  Integer.toString(num)
    	List -> String      :  .toString()
    	List -> Array       :  .toArray()
    	List<T> -> Array<T> :  .toArray(arr)

## Sorting:

    	Arrays.sort(arr,Collections.reverseOrder())
    	Arrays.sort()
    	Arrays.sort(arr,start,end)

## Useful Functions:

    	Min/Max:
    		Math.min(a,b)
    		Math.max(a,b)

## Specific Task (Application)

<details open>
<summary>Heap</summary>
<br>
<details>
    <summary>Sort Character by Frequency</summary>
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
    <h5> A-Z order </h5>

```java

```
</details>
<details>
    <summary>Top K Frequent Number</summary>
    <h5> A-Z order </h5>

```java

```
</details>

<details>
    <summary></summary>
    <h5> </h5>

```java

```
</details>

<br>
</details>

<details open>
<summary>Bucket Sort</summary>
<br>
<details open>
    <summary>Sort Character by Frequency</summary>
    <h5> A-Z order </h5>

```
        Bucket Label = Frequency 
        Max Frequency = String Size = Bucket Size 

        1. Count frequency of each char using map 
        2. Add frequency of each char to bucket 
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

