- [How memory works](#how-memory-works)
- [Arraws and linked lists](#arraws-and-linked-lists)
    - [Arrays](#arrays)
    - [Linked lists](#linked-lists)
- [Selection Sort](#selection-sort)
    - [Time Complexity:](#time-complexity)
    - [Implementation](#implementation)
- [Excercise Answers](#excercise-answers)

## How memory works
Memory works like drawers, in which you can only store one thing in each drawer. 

## Arraws and linked lists
### Arrays
- The problem is that everytime you fill the array and want to add more you need to realocate memory for more space, which takes more computations.
- Allows both random and sequential access (can access any point without running the whole array)
#### Reading time complexity: O(1)
#### Insertion time complexity: O(n)
#### Deletion time complexity: O(n)
### Linked lists
- The problem is that you need to look through all of the nodes before the one you want.
- Only allows sequential access
#### Reading time complexity: O(n)
#### Insertion time complexity: O(1)
#### Deletion time complexity: O(1)

## Selection Sort
You go through the whole array or linked list and check for the highest or lowest value. Once you have it you add it to a new list or array. Keep doing it and you will end up with a sorted array or list.

#### Time Complexity: 
$$O(n^2)$$
It is like this because you need to run through the whole array or list everytime you want to find the highest or lowest value.

#### Implementation
```
```

## Excercise Answers
#### 2.1 Suppose you’re building an app to keep track of your finances. Every day, you write down everything you spent money on. At the end of the month, you review your expenses and sum up how much you spent. So, you have lots of inserts and a few reads. Should you use an array or a list?
A list because the you are inserting much more than what you read.

#### 2.2 Supposeyou’rebuildinganappforrestaurantstotakecustomer orders. Your app needs to store a list of orders. Servers keep adding orders to this list, and chefs take orders off the list and make them. It’s an order queue: servers add orders to the back of the queue, and the chef takes the first order off the queue and cooks it. Would you use an array or a linked list to implement this queue? (Hint: Linked lists are good for inserts/deletes, and arrays are good for random access. Which one are you going to be doing here?)

A link list with a pointer to the last element to have a smaller time complexity

#### 2.3 Let’s run a thought experiment. Suppose Facebook keeps a list of usernames. When someone tries to log in to Facebook, a search is done for their username. If their name is in the list of usernames, they can log in. People log in to Facebook pretty often, so there are a lot of searches through this list of usernames. Suppose Facebook uses binary search to search the list. Binary search needs random access—you need to be able to get to the middle of the list of usernames instantly. Knowing this, would you implement the list as an array or a linked list?
An array to be able to enter at any point.

#### 2.4 People sign up for Facebook pretty often, too. Suppose you decided to use an array to store the list of users. What are the downsides of an array for inserts? In particular, suppose you’re using binary search to search for logins. What happens when you add new users to an array?
You'll need to move all the memory slots because you need to reorder the whole array.

#### 2.5 In reality, Facebook uses neither an array nor a linked list to store user information. Let’s consider a hybrid data structure: an array of linked lists. You have an array with 26 slots. Each slot points to a linked list. For example, the first slot in the array points to a linked list containing all the usernames starting with a. The second slot points to a linked list containing all the usernames starting with b, and so on. Suppose Adit B signs up for Facebook, and you want to add them to the list. You go to slot 1 in the array, go to the linked list for slot 1, and add Adit B at the end. Now, suppose you want to search for Zakhir H. You go to slot 26, which points to a linked list of all the Z names. Then you search through that list to find Zakhir H. Compare this hybrid data structure to arrays and linked lists. Is it slower or faster than each for searching and inserting? You don’t have to give Big O run times, just whether the new data structure would be faster or slower.
Faster for adding but slower for searching.