# Hashtables
## Terminology:

* Hash - A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. In the case of a hashtable,
* Buckets - A bucket is what is contained in each index of the array of the hashtable. Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.
* Collisions - A collision is what happens when more than one key gets hashed to the same location of the hashtable.


## Why do we use them?
1. Hold unique values
2. Dictionary
3. Library


## What Are they
* Hashtables are a data structure that utilize key value pairs. This means every Node or Bucket has both a key, and a value.

* The basic idea of a hashtable is the ability to store the key into this data structure, and quickly retrieve the value. 

* Time complexity O(1)  
* Arrays actually have fast access. If we know the index of the information we want  



* The hash code is used again to read something from the hash map. 

## Structure
### Hashing
a hash code turns a key into an integer.  

### Creating a Hash
A hashtable traditionally is created from an array. 

1. Add or multiply all the ASCII values together.
2. Multiply it by a prime number such as 599.
3. Use modulo to get the remainder of the result, when divided by the total size of the array.
4. Insert into the array at that index.


## Collisions
* A collision occurs when more than one key hashes to the same index in an array. 
* a “perfect hash” will never have any collisions.
* The more keys you have hashed to a specific index, the more key/value pair combos you can potentially have.

### Collisions solving
Collisions are solved by changing the initial state of the buckets.  Now if two keys resolve to the same index in the array then their key/value pairs can be stored as a node in a linked list. Each index in the array is called a “bucket” because it can store multiple key/value pairs.




### Hash maps do this to store values:

* accept a key
* calculate the hash of the key
* use modulus to convert the hash into an array index
* store the key with the value by appending both to the end of a linked list

### Hash maps do this to read value:

* accept a key
* calculate the hash of the key
* use modulus to convert the hash into an array index
* use the array index to access the short LinkedList representing a bucket
* search through the bucket looking for a node with a key/value pair that matches the key you were given

## Bucket Sizes
Hash Maps can have any number of buckets. If a hash map has only a few buckets it will be densely full and have many collisions. If a hash map has more buckets it will be more sparsely populated, there will be less collisions, but there may be a lot of extra empty space.


> Recognize: calculating load factors and choosing the optimal number of buckets, and determining the best hash functions is not within the scope of this class. This class intends to introduce you to what a hash table is, how it’s implemented, what hash codes are, how to handle collisions and how to reason generally about what it means for a hash table to be more empty or more full. This class does not intend to calculate theoretical optimal performance limits for how to best balance a Hash Table.


## Internal Methods
### Add()
#### When adding a new key/value pair to a hashtable:
1. send the key to the GetHash method.
2. Once you determine the index of where it should be placed, go to that index
3. Check if something exists at that index already, if it doesn’t, add it with the key/value pair.
4. If something does exist, add the new key/value pair to the data structure within that bucket.
### Find()
The Find takes in a key, gets the Hash, and goes to the index location specified. Once at the index location is found in the array, it is then the responsibility of the algorithm the iterate through the bucket and see if the key exists and return the value.

### Contains()
* The Contains method will accept a key, and return a bool on if that key exists inside the hashtable. 

### GetHash()
* The GetHash will accept a key as a string, conduct the hash, and then return the index of the array where the key/value should be placed.