- [Hash tables](#hash-tables)
    - [Hash Functions](#hash-functions)
    - [Time Complexity](#time-complexity)
    - [Use cases](#use-cases)
    - [Collisons](#collisons)
        - [Avoiding Collisions:](#avoiding-collisions)
    - [Performance](#performance)
- [Excercise answers](#excercise-answers)


## Hash tables

- Hash tables work with an array that stores the values and the you use a **hash function** to know in which slot is the value stored. 
- Basically the hashfunction returns you an index of where is your value stored.
- A.K.A. - hash maps, maps, dictionaries, and associative arrays.
### Hash Functions
-  Functions in which you input a string and you get back a number
-  It has some requirements:
    -  Must be consistent (always return the same number)
    -  It should map diferent words to diferent numbers
- Hash functions know how big the array is and only returns valid indexes
- Hash tables are good for modeling relationships from one item to another item

### Time Complexity
$$O(1)$$
Because you only need to look in the slot you are using.

### Use cases
- Phonebooks
- In the internet to go from the domain name to the IP address
- To prevent duplicates, you only want something to happen once per something so you use a hashtable to see if that object has a value, and if it does it means it was already used
- To cache data - you save the static websites so that you don't need to calculate what to send back. You save that data in a hashtable using the link as a key, then if the key exists and has a value

### Collisons
- It is almost imposible for a hashfunctions to always map to diferent keys, so when you get two values in the same key it is called a **collision**
- When you get a collision you can work around it in different ways:
    - Do a linked list in the slot. Ex:
        - Apples(62) -> Avocados(1.49)->NULL; both fall in slot 0 because of A
- When you get a collision you start slowing down performance that is why **The hash function is so important**
- If the link lists get long then the hashtable will be slow. But with a good hash function this shouldn't happen.
  
#### Avoiding Collisions:
-  You need 2 things:
    -  A low load factor
        - Measures how many empty slots are left
        -  Calculated by (number of items in hashtable) / (total number of slots)
        -  Load factor greater than 1 means you have more items than array slots so you need to increase the size of the hashtable. this is called **resizing**:
            1. Create a new array bigger than the previous one, usually you double the size of it
            2. insert the elements again 
        -   Rule of thumb: Resize when load factor gets to .7 or more
        -   lower load factor = less collisions
    -  A good hash function
        -  Distributes values in the array evenly

### Performance
- In average case the hashtable will do: O(1)
- In worst case: O(n)
    - All values fall in the same index
- To keep a good performance you need to avoid collisions

---

## Excercise answers
#### Which of these hash functions are consistent?
#### 5.1 f(x) = 1
Yes
#### 5.2 f(x) = rand()
No
#### 5.3 f(x) = next_empty_slot()
No
#### 5.4 f(x) = len(x)
Yes