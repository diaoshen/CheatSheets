## C++
* Useful  Type:

		int (16 bit)
		long int (32 bit) 
		long long int (64 bit)

* Constant:

		http://www.cplusplus.com/reference/climits/
		INT_MAX ,  INT_MIN    (16 bit)
		LONG_MIN , LONG_MAX , INT32_MIN , INT32_MAX  (32 bit)
		LLONG_MIN , LLONG_MAX , INT64_MIN , INT64_MAX (64 bit)

* String: 

		.length() 
		.at(i) 
		.append(src , length)
		.substr(start_pos , len)

* Vector:

		vector<string> varName(length,InitialValue)
		vector<int> v{1,2,3}
		.insert(start_pos  , src start , src end)
		.insert(start_pos , value_to_insert)
		.begin()
		.end() 
		.clear()
		.push_back()

* Set:

		set<string> foo = {};
		.insert()
		.find()   -> returns index if found else end 
		.size()
		.begin()
		.end()

* Map:

		map<char, int> foo 
		map<char,int,custom_comparator> foo 
		foo['a'] = 10
		.insert(std::pair<char,int>('a',10))
		.find()   -> returns index if found else end 

* Pair:

		pair<int,int> foo
		foo.first 
		foo.second 

* Conversion:

		Integer -> String   :  to_string(i)			

* Sorting:

		sort(start, end , [custom sort function])

* Iterate:

		String:
				for(auto i = 0 ; i < str.length() ; i++)
		Vector:
				for(auto it = vec.begin(); it != vec.end(); it++)
		Set:
				for(set<int>::iterator it = myset.begin() ; it != myset.end() ; it++)
		Map:
				for(map<int,int>::iterator it = myMap.begin() ; it != myMap.end() ; it++)
					it->first 
					it->second 

* LeetCode Usable Libraries:

		Swap:
				swap(a,b)
		Min/Max:
				min(a,b)
				max(a,b)

## JAVA
* Useful Type

		long 

* Useful Constant

		Long.Min_VALUE 	

* String:

		.charAt()	

* Array:

		Arrays.sort(arr) 
		.length 	
		return new int[] {1,2,3}

* List:

		List<String> foo = new ArrayList<String>()
		.add()	

* HashSet: Good for removing duplicates with fast operations 

		HashSet<Integer> h = new HashSet<Integer>()
		.contains()  O(1) 
		.add()	

* HashMap:

		HashMap<Integer, String> foo = new HashMap<Integer, String>()
		for(Integer key : foo.keySet())
		.get(key)		
		.containsKey(target)
		.put(key,value)

* Conversion:

		String -> Char[]   :  .toCharArray()
		Array -> String    :  Arrays.toString(arr)
		Integer -> String  :  Integer.toString(num)	

* Sorting:

		Arrays.sort(arr,Collections.reverseOrder())
		Arrays.sort()
		Arrays.sort(arr,start,end)

* Useful Functions:

		Min/Max:
			Math.min(a,b)
			Math.max(a,b)
		

