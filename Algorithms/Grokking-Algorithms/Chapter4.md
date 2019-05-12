- [Divide and Conquer](#divide-and-conquer)
    - [Tip](#tip)
- [Quicksort](#quicksort)
    - [Tip](#tip)
    - [Time complexity:](#time-complexity)
- [Inductive proofs](#inductive-proofs)
- [Big O Constants](#big-o-constants)
- [Excercises Solved](#excercises-solved)

## Divide and Conquer
- 2 Steps
    1. Figure out the base case. This is the simples posible case.
    2. Divide or decrease you problem until it becomse the base case.

---
##### Tip
If you write a recursive function with an array the base case is usually the empty array

---

## Quicksort
- **Base Case** - empty arrays or arrays with only one element because they are like sorted

1. check if len of array is smaller than 2 if it is then return the array
2. if not, then pick a pivot
3. Partition the array into two sub arrays, one with numbers smaller than the pivot and another with those bigger
4. call quicksort on both arrays
5. return the result of the quicksort small + pivot + quicksort big

```
def quicksort(arr):
    if (len(arr) < 2):
        return (arr)
    pivot = arr[0]
    smaller = [i for i in arr[1:] if i <= pivot]
    bigger = [i for i in arr[1:] if i > pivot]
    return quicksort(smaller) + [pivot] + quicksort(bigger)
```

---
##### Tip
If you’re implementing quicksort, choose a random element as the pivot. The average runtime of quicksort is O(n log n)!

---

##### Time complexity:
- Worst case:
    - You choose the beginning or the end of a sorted array as a pivot, so you will actually just divide the array all the time. This will cause you to have a O(n) in the stack and O(n) which gives you:
$$O(n^2)$$
- Average case:
    -  You choose the pivot which is the middle value so you divide by two the array always and then you only go down the stack log(n) times. On each stack call you do O(n) to get the values so you get O(n) * O(log(n)) which is: 
$$O(n * log(n))$$
## Inductive proofs
- Way to show that you can solve something
- You use two cases:
    - **Base case** - you demonstrate you can use it to solve on the easiest way (Ex: you can sort an array of 1)
    - **Inductive Case** - You demonstrate that you can use the base case to solve the rest of the problems (Ex: If quicksort works for an array of 1 it will work for an array of 2, and it will work for an array of 3, etc.)

## Big O Constants
- When you are writing big O notation you are actually multiplying the time complexity times the amount of time for each calculation
$$C * O(time complexity)$$
- Usually this constant does not matter because if you have algorithms with different time complexity then the diference between the time of one algorithm or the other won't matter

 | 10 ms * n                    | 1 sex * log(n)                    |
 | ---------------------------- | --------------------------------- |
 | 10 ms * 4 billion = 463 days | 1 sec log(4 billion) = 32 seconds |
- It only matters if the two algorithms have the same time complexity


## Excercises Solved
##### 4.1 Write out the code for the earlier sum function.
```
def sum(arr):
    if (len(arr) == 1):
        return arr[0]
    return arr[0] + sum(arr[1:])
```
##### 4.2 Write a recursive function to count the number of items in a list.
```
def recursive_count(arr):
    if (len(arr) == 1):
        return 1
    return 1 + recursive_count(arr[1:])
```
##### 4.3 Find the maximum number in a list.
```
def r_max(arr):
    if (len(arr) == 2):
        return arr[0] if arr[0] >= arr[1] else arr[1]
    tmpMax = max(arr[1:])
    return arr[0] if arr[0] >= tmpMax else tmpMax
```
##### 4.4 Remember binary search from chapter 1? It’s a divide-and-conquer algorithm, too. Can you come up with the base case and recursive case for binary search?
- **Base cases**: if your middle guess is right return the number else if the arr is of length 1 and is not right return null
- **Recursive case**: If the value is bigger than middle then return binary_search(arr[middle + 1:]) or the other half around if it is smaller

#### How long would each of these operations take in Big O notation?
#### 4.5 Printing the value of each element in an array.
$$O(n)$$
#### 4.6 Doubling the value of each element in an array.
$$O(n)$$
#### 4.7 Doubling the value of just the first element in an array.
$$O(1)$$
#### 4.8 Creating a multiplication table with all the elements in the array. So if your array is [2, 3, 7, 8, 10], you first multiply every element by 2, then multiply every element by 3, then by 7, and so on.
$$O(n^2)