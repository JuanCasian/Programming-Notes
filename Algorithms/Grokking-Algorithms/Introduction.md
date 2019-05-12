- [Grokking Algorithms](#grokking-algorithms)
    - [Binary Search](#binary-search)
            - [Time Complexity:](#time-complexity)
    - [Big O notation](#big-o-notation)
    - [Excercise Answers](#excercise-answers)

# Grokking Algorithms

## Binary Search

Searching algorithm that divides an ordered input by half everytime to get into the correct value. It then returns the position or null if it does not appear.

#### Time Complexity:
$$
O(log_2(n))
$$

```
def binary_search(list, item):
    low = 0
    high = len(list) - 1

    while (low <= high):
        mid = (low + high) / 2
        guess = list[mid]
        if (guess == item):
            return mid
        if (guess > item):
            high = mid - 1
        else:
            low = mid + 1
    return None
```

## Big O notation

- Algorithm tim is measured in terms of *growth* of the algorithm.
- Representation of the **time complexity**
    -  **Time Complexity** is the measure of how the runtime of an algorithm changes as the input of the algorithm changes. How quickly the run time of an algorithm increases as the size of the input increases.
-  It is represented as:
$$
O(time/complexity)
$$
- Most common time complexities:
$$ O(log(n)) $$
$$ O(n) $$
$$ O(n*log(n)) $$
$$ O(n^2) $$
$$ O(n!) $$

## Excercise Answers

#### 1.1 Suppose you have a sorted list of 128 names, and you’re searching through it using binary search. What’s the maximum number of steps it would take?
7
#### 1.2 Suppose you double the size of the list. What’s the maximum number of steps now?
8
#### 1.3 You have a name, and you want to find the person’s phone number in the phone book.
$$ O(log(n)) $$
Because you can do algorithm like binary search in which you get an ordered input.

#### 1.4 You have a phone number, and you want to find the person’s name in the phone book. (Hint: You’ll have to search through the whole book!)
$$ O(n) $$
Because in worst case you will need to go into the end of the array, because the input is not ordered.

#### 1.5 You want to read the numbers of every person in the phone book.
$$ O(n) $$

#### 1.6 You want to read the numbers of just the As. (This is a tricky one! It involves concepts that are covered more in chapter 4. Read the answer—you may be surprised!)
$$ O(n) $$

