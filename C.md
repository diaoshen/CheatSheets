# C string 

#### cstring is null terminated `'\0'`
#### cstring is a  `char *`
![cstring](https://static.javatpoint.com/cpages/images/pointer-to-string.png)

### To use cstring 
```
#include <cstring>  // C++
#incude  <string.h> // C
```
### Example 
```
char greetings[6] = { 'H', 'e', 'l', 'l', 'o', '\0'}
char myString[]{ "string" } //C++ auto add '\0' 

char myString[]{ "string" }; // ok
myString = "rope"; // not ok!

```
## String Manipulation 
### Length of C string : returns length of string without null terminator 
```
size_t strlen ( const char * str );
```
### String Copy 
```
char * strcpy ( char * destination, const char * source );
char * strncpy ( char * destination, const char * source, size_t num );
```
### Memory Copy (string,structure) - copy block of memory 
```
void * memcpy ( void * destination, const void * source, size_t num );
```
### Memory Set  - fill block of memory 
```
void * memset ( void * ptr, int value, size_t num );
```

### std::string  --> char *
```
const char *cstr = str.c_str()

```
* #### Since c_str() returns const char * , copy is needed 
```
std::string str = "string";
char *cstr = new char[str.length() + 1]; // +1 for '\0'
strcpy(cstr, str.c_str());
// do stuff
delete [] cstr;
```

