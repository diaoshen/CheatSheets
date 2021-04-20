# C++

## Table of Contents

### 1. [Data Type](#Type)

### 2. [Constants](#Constants)

### 3. [Math](#Math)

### 4. [Standard Library](#std)

### 5. [BitManipulation](#BitManipulation)

### 6. [Conversion](#Conversion)

### 7. [Sort](#Sort)

### 8. [Reverse Sort](#Reverse-Sort)

### 9. [Iterate Methods](#Iterate_Methods)

### 10. [Iterate](#Iterate)

### 11. [Reverse Iterate](#Reverse-Iterate)

### 12. [Leetcode Usable functions](#LeetCode-Usable-Libraries)

### 13. [std::string](#String)

### 14. [std::vector](#Vector)

### 15. [std::stack](#Stack)

### 16. [std::queue](#Queue)

### 17. [std::priority_queue](#Priority-Queue)

### 18. [std::set](#Set)

### 19. [std::unordered_set](#Unordered-Set)

### 20. [std::ordered_map](#Ordered-Map)

### 21. [std::pair](#Pair)

## Type

    	int (16 bit)
    	long int (32 bit)
    	long long int (64 bit)

## Constants

    	http://www.cplusplus.com/reference/climits/
    	INT_MAX ,  INT_MIN    (16 bit)
    	LONG_MIN , LONG_MAX , INT32_MIN , INT32_MAX  (32 bit)
    	LLONG_MIN , LLONG_MAX , INT64_MIN , INT64_MAX (64 bit)
    	nullptr

## Math

    	pow(base,exponent)
    	abs()
    	max()
    	min()

## std
```cpp
    	std::*max_element(iter::begin , iter::end) //Max element in container
    	std::distance(iter::begin , iter::end) //Distance between 2 element
    	std::reverse(iter::begin , iter::end) //Use for reverse sort
    	std::sort(iter::start, iter::end , [custom sort function or lamda])
    	std::copy(src iter::start , src iter:end ,  dst iter)
    	std::to_string(int,double,float)
    	std::accumulate(iter::start , iter::end) // Sum up all val in container
    	std::find(iter::begin , iter::end , target) // Returns iter to target , else iter::end
		std::begin(Container) //  Iterator pointing to first element in container 
		std::end(Container) // Iterator  pointing to  last element in container 
    	std::upper_bound( iter::start , iter::end , val)
    	std::lower_bound( iter::start , iter::end , val)
		std::min_element( iter::start , iter::end)
		std::max_element( iter::start , iter::end)
```

## BitManipulation

    	AND(&)  to extract a subset of the bits in the value
    	OR(|) to set a subset of the bits int he value
    	XOR(^) to toggle a subset of bits in the value

    	constexpr std::uint_fast8_t mask0{ 0b0000'0001 }; // represents bit 0
    	constexpr std::uint_fast8_t mask1{ 0b0000'0010 }; // represents bit 1
    	constexpr std::uint_fast8_t mask2{ 0b0000'0100 }; // represents bit 2
    	constexpr std::uint_fast8_t mask3{ 0b0000'1000 }; // represents bit 3
    	constexpr std::uint_fast8_t mask4{ 0b0001'0000 }; // represents bit 4
    	constexpr std::uint_fast8_t mask5{ 0b0010'0000 }; // represents bit 5
    	constexpr std::uint_fast8_t mask6{ 0b0100'0000 }; // represents bit 6
    	constexpr std::uint_fast8_t mask7{ 0b1000'0000 }; // represents bit 7

    	Even:
    		if num & 1 == 0 // LSD is a 0
    	Odd:
    		if num & 1 == 1 // LSD is a 1

    	Is bit 3 ON:
    		if num & mask3 > 0
    	Is bit 3 OFF:
    		if num & mask3 == 0

    	Set bit 3 to ON:
    		num |= mask3
    	Set bit 3 to OFF:
    		num &= ~mask3
    	Set bit 4 and 5 to ON:
    		num != (mask4 | mask5)
    	Set bit 4 and 5 to OFF:
    		num &= ~(mask4 | mask5)

    	Flip bit 2:
    		num ^= mask2
    	Flip bit 4 and 5:
    		num ^= (mask4 | mask5)
    	Flip any bit:
    		any bit to flip , just set to 1
    		     1 1 1 0 1 1 0 1   [input]
    		(^)  0 0 1 1 1 1 0 0    [mask]
    		------------------------------
    		     1 1 0 1 0 0 0 1  [output]

    	Extract bit
    		     1 1 1 0 1 1 0 1   [input]
    		(&)  0 0 1 1 1 1 0 0    [mask]
    		------------------------------
    		     0 0 1 0 1 1 0 0  [output]
    	To Count # of bits
    		1. __builtin_popcount()
    		2. Do a right shift til 0
    		3. bitset<32>.count()

    	std::bitset // <bitset>

## Conversion
```cpp
	/** int,double,float -> string */
	auto s = std::to_string(i)
	/* char[] , char* , cstr -> string */
	std::string str(chArray)
	/* string -> c_str */
	char* cstr = str.c_str()
```

## Lamda 
```cpp
```

## Custom Comparable
```cpp
	/**
		Returns true if i should go before j 
	*/

	/*  comp as a function */
	bool sortByAsc (int i,int j) { return i<j; }
	/*  comp as an object */
	struct sortByAsc {
	bool operator() (int i,int j) { return i<j;}
	} comp;

	/**
		Common Template struct :
		std::greater<T>
		std::greater_equal<T>
		std::equal_to<T>
		std::not_equal_to<T>
		std::less<T>
		std::less_equal<T>
	*/
	std::sort(iter::begin , iter::end , greater<int>())
```


## Sort
```cpp
    std::sort(iter::begin , iter::end) 
	std::sort(iter::begin, iter::end, customComparable)
```

## Reverse Sort
```cpp
	/*
		Options:
		1. using template struct
		2. using reverse iter 
		3. lamda comp 
		4. function comp 
		5. std::reverse 
	*/
    1. std::sort(iter::begin , iter::end , greater<int>())
    2. std::sort(iter::rbegin , iter::rend)
    3. std::sort(iter::begin , iter::end , [](int &x , int &y){
    		return x > y
       });
    4.
       bool comp(int &a , int &b) { return a > b; }
       std::sort(iter::begin , iter::end , comp)
    5. std::reverse(iter::begin , iter::end)
```
## Other Popular Custom Sort
```cpp
// Sort by # of 1 bits , if # of 1 bit is the same then sort by A-Z order
sort(arr.begin() , arr.end() , [](const int& a, const int& b){
	int countA = __builtin_popcount(a);
	int countB = __builtin_popcount(b);
	return countA == countB ? a < b  :  countA < countB;
});

```

## Iterate Methods
```cpp
    Ranged based:
    	for(auto &item : v) {
    		auto index = &item - &v[0]
    	}
    Iterator based:
    	for(auto it = v.begin(); it != v.end(); it++) {
    		auto index = std::distance(v.begin() , it)
    	}
```

## Iterate
```cpp
    	String:
    			for(auto i = 0 ; i < str.length() ; i++)
    			for(auto item : str)
    	Vector:
				for(int i=0; i<vec.size(); i++)
    			for(auto it = vec.begin(); it != vec.end(); it++)
    			for(auto item : vec)
    	Set:
    			for(set<int>::iterator it = myset.begin() ; it != myset.end() ; it++)
    	Map:
    			for(map<int,int>::iterator it = myMap.begin() ; it != myMap.end() ; it++) {
    				it->first
    				it->second
    			}

    			for(auto it : myMap) {
    				it.first
    				it.second
    			}

    			//Require C++17  Decomposition declaration
    			for(auto &x : m) {
    				auto &[key, val] = x;
    				cout << key >> " - > " << val << endl;
    			}
```
## Reverse Iterate
```cpp
    	Map:
    		for(auto it = myMap.rbegin(); it != myMap.rend(); it++)
```
## LeetCode Usable Libraries:
```cpp
    	//4 ways to Disable Sync and Tie:
    			static auto _=[](){std::ios::sync_with_stdio(false); cin.tie(0); cout.tie(0);};

    			auto speedup = []()
    			{
    				std::ios::sync_with_stdio(false);
    				std::cin.tie(nullptr);
    				std::cout.tie(nullptr);
    				return nullptr;
    			}();

    			// makes code faster, but larger. Just for LeetCode fun!
    			#pragma GCC optimise ("Ofast")
    			// makes stdin not synced so it is faster. Just for LeetCode fun!
    			static auto __ __attribute__((unused)) = []() {  // NOLINT
    			ios_base::sync_with_stdio(false);
    			cin.tie(nullptr);
    			return nullptr;
    			}();

    	Swap:
    			swap(a,b)
    	Min/Max:
    			min(a,b)
    			max(a,b)
```
# Data Structures

## String
```cpp
		string str = "";
		.size() // length of string
    	.length() // length of string
		str[i] // char at i 
    	.at(i) // char at i
    	.back() // last char 
		.front() // first char  
		str +=  "append" // append string 
		.append() // append string , more overloads (SEE cpp)
		.push_back() // append string 
		.pop_back()  //  delete last char 
    	.substr(start_pos) || .substr(start_pos , len)
    	.find() // Returns string::npos if not found
    	.insert(start_pos , len)
```
## Vector
```cpp
    	vector<string> varName(length,[InitialValue])
    	vector<int> v{1,2,3}
    	vector<int> v = {1,2,3}
    	.insert(iter to start_pos  , iter to src start , iter to src end)
    	.insert(iter to start_pos , value_to_insert)
    	.begin() // iter to start_pos  
    	.end()  // iter to end_pos 
    	.rbegin()  // iter to reverse start 
    	.rend() // iter to  reverse end 
    	.clear()
    	.push_back()
    	.back()
```
## Stack
```cpp
    	stack<int> st
    	.push(element)
    	.pop()
    	.top()
    	.size()
    	.empty()
```
## Queue
```cpp
    	queue<int> q
    	.front()
    	.back()
    	.push(element)
    	.pop()
    	.size()
    	.empty()
<<<<<<< HEAD
```
## Priority Queue / HEAP
```cpp
		/**
			Template parameters
				T : type of element 
				Container : underlying container , default vector 
				Compare : comparable , default using less<T>
		*/

		/* MIN HEAP */
		auto compareByPriority = [](auto &a , auto& b) {return a.priority > b.priority;};
		priority_queue<Process, vector<Process>, decltype(compareByPriority)> pq(compareByPriority); 

		/* MAX HEAP */
		auto compareByPriority = [](auto &a , auto& b) {return a.priority < b.priority;};
		priority_queue<Process, vector<Process>, decltype(compareByPriority)> pq(compareByPriority); 
=======

>>>>>>> 61e0d3d77979417bbd83639717cf2b17058f7a24

## Priority Queue
	max heap by default
    	priority_queue<int> pq
    	priority_queue<int> pq(nums.begin(), nums.end())
    	.top()
    	.pop()
    	.push()
```
## Set
```cpp
    	set<string> foo = {};
    	.insert()
    	.find()   -> returns index if found else iter::end
    	.size()
    	.begin()
    	.end()
```
## Unordered Set
```cpp
    	unordered_set<int> set
    	.count()
    	.insert(item)
```
## Ordered Map
```cpp
    	map<char, int> foo
    	map<char,int,custom_comparator> foo
    	if(foo['a]) // will create this key and set to 0 if doesn't exist
    	foo['a'] = 10
    	.insert(std::pair<char,int>('a',10))
    	.find()   -> returns index if found else iter::end
```
## Unordered Map
```cpp
    	unordered_map<string,int> m
    	m['blah] // creates this key/val pair and set to 0 if doesn't exist
```
## Pair
```cpp
    	pair<int,int> foo
    	foo.first
    	foo.second
```
