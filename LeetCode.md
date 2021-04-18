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

### 17. [std::priority_queue](#Priority Queue)

### 18. [std::set](#Set)

### 19. [std::unordered_set](#Unordered-Set)

### 20. [std::ordered_map](#Ordered-Map)

### 21. [std::pair](#Pair)

### //JAVA TODO

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

    	std::*max_element(iter::begin , iter::end) //Max element in container
    	std::distance(iter::begin , iter::end) //Distance between 2 element
    	std::reverse(iter::begin , iter::end) //Use for reverse sort
    	std::sort(iter::start, iter::end , [custom sort function or lamda])
    	std::copy(src iter::start , src iter:end ,  dst iter)
    	std::to_string(int,double,float)
    	std::accumulate(iter::start , iter::end) // Sum up all val in container
    	std::find(iter::begin , iter::end , target) // Returns iter to target , else iter::end

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
    	//TODO

## Conversion

    	Integer -> String   :  to_string(i)
    	String -> Integer/Double/Float  : std::to_string(int,double,float)

## Sort

    sort(iter::begin , iter::end)

## Reverse Sort

    1. sort(iter::begin , iter::end , greater<int>())
    2. sort(iter::rbegin , iter::rend)
    3. sort(iter::begin , iter::end , [](int &x , int &y){
    		return x > y
       });
    4.
       bool comp(int &a , int &b) { return a > b; }
       sort(iter::begin , iter::end , comp)
    5. reverse(iter::begin , iter::end)

## Custom Sort

-   Sort by # of 1 bits , if # of 1 bit is the same then sort by A-Z order

```
// Using lamda as the comparator

sort(arr.begin() , arr.end() , [](const int& a, const int& b){
	int countA = __builtin_popcount(a);
	int countB = __builtin_popcount(b);
	return countA == countB ? a < b  :  countA < countB;
});

```

## Iterate Methods

    Ranged based:
    	for(auto &item : v) {
    		auto index = &item - &v[0]
    	}
    Iterator based:
    	for(auto it = v.begin(); it != v.end(); it++) {
    		auto index = std::distance(v.begin() , it)
    	}

## Iterate

    	String:
    			for(auto i = 0 ; i < str.length() ; i++)
    			for(auto item : str)
    	Vector:
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

## Reverse Iterate

    	Map:
    		for(auto it = myMap.rbegin(); it != myMap.rend(); it++)

## LeetCode Usable Libraries:

    	Disable Sync and Tie:
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

# Data Structures

## String

    	.length()
    	.at(i)
    	.back()
    	.append(src) || .append(src, #char to append) || .append(src, startPos , #char to append)
    	.substr(start_pos) || .substr(start_pos , len)
    	.find() // Returns string::npos if not found
    	.insert(start_pos , len)

## Vector

    	vector<string> varName(length,[InitialValue])
    	vector<int> v{1,2,3}
    	vector<int> v = {1,2,3}
    	.insert(iter to start_pos  , iter to src start , iter to src end)
    	.insert(iter to start_pos , value_to_insert)
    	.begin()  ||  begin(v)
    	.end()  || end(vect)
    	.rbegin()
    	.rend()
    	.clear()
    	.push_back()
    	.back()
    	upper_bound( iter::start , iter::end , val)
    	lower_bound( iter::start , iter::end , val)

## Stack

    	stack<int> st
    	.push(element)
    	.pop()
    	.top()
    	.size()
    	.empty()

## Queue

    	queue<int> q
    	.front()
    	.back()
    	.push(element)
    	.pop()
    	.size()
    	.empty()


## Priority Queue
	max heap by default
    	priority_queue<int> pq
    	priority_queue<int> pq(nums.begin(), nums.end())
    	.top()
    	.pop()
    	.push()

## Set

    	set<string> foo = {};
    	.insert()
    	.find()   -> returns index if found else iter::end
    	.size()
    	.begin()
    	.end()

## Unordered Set

    	unordered_set<int> set
    	.count()
    	.insert(item)

## Ordered Map

    	map<char, int> foo
    	map<char,int,custom_comparator> foo
    	if(foo['a]) // will create this key and set to 0 if doesn't exist
    	foo['a'] = 10
    	.insert(std::pair<char,int>('a',10))
    	.find()   -> returns index if found else iter::end

## Unordered Map

    	unordered_map<string,int> m
    	m['blah] // creates this key/val pair and set to 0 if doesn't exist

## Pair

    	pair<int,int> foo
    	foo.first
    	foo.second

