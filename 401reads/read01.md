# Pain vs. Suffering

* Suffering is pain without purpose. Pain with no higher goal. Pain with no dreams, no ambition, no aspiration.
## What’s your perspective?
* Te have to get into pain to reach what we want 
## Why are you doing this?
* To invest in a different life. A better life.
## Do you want what comes at the end of this journey?
* Ofcourse  
## Are you doing this for you?
* For me and for others who wait alot from me 

# Beginners Guide to Big O Notation

### Big O notation is used in Computer Science to describe the performance or complexity of an algorithm.

### Big O specifically describes the worst-case scenario and can be used to describe the execution time required or the space used

* O(1) describes an algorithm that will always execute at the same time (or space) regardless of the size of the input data set.

* O(N) describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set

* O(N²) represents an algorithm whose performance is directly proportional to the square of the size of the input data set

* O(2^N) denotes an algorithm whose growth doubles with each addition to the input


## Logarithms

### This type of algorithm is described as O(log N). 
* it produces a growth curve that peaks at the beginning and slowly flattens out as the size of the data sets increase e.g. an input data set containing 10 items takes one second to complete, a data set containing 100 items takes two seconds, and a data set containing 1,000 items will take three seconds. Doubling the size of the input data set has little effect on its growth as after a single iteration of the algorithm the data set will be halved and therefore on a par with an input data set half the size. This makes algorithms like binary search extremely efficient when dealing with large data sets.

# Names and Values in Python:

* when we refer x to 23 then say y =x we refer y to 23 not to x
* if we refer x to "world" then refer it to "hello" x we be hello and world will not have a name 
* assignment never copy data, so when we change a list and it has to names the change we be seen in to variables 
* mutable aliasing 
* a mutable value 
* more than one name
* the value change 
* all names see the change

#### mutable can't alias 
1. immutable value 
2. cant change it in place 
3. like ints,floats,string,tuples

#### Change 
1. change an int: rebinding 
2. change a list: mutating
3. we can rebinding a list

* function arguments are assignments

* In functions you can change actual value if it mutable values using method not reassign 
* names have a scope but not have a type
* values have no scope but have a type