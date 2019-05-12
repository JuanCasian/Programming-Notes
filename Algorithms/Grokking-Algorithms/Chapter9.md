- [Dynamic Programming](#dynamic-programming)
    - [When to use it?](#when-to-use-it)
    - [General tips](#general-tips)
    - [Longest common substring](#longest-common-substring)
        - [Implementation](#implementation)
    - [Longest common subsequence](#longest-common-subsequence)
    - [Uses](#uses)
- [Excercise Answers](#excercise-answers)
  
## Dynamic Programming
- you start by solving subproblems and then build up to solving the big problem
- All dynamic programming algorithms start with a grid
- In dynamic programing you can only use take tha full path, you can't use it on problems to stole some rice instead of the whole bag
- Dynamic programming only works when each subproblem is discrete—when it doesn’t depend on other subproblems.
- You try to maximize something

### When to use it?
- Dynamic programming is useful when you’re trying to optimize something given a constraint.
- You can use dynamic programming when the problem can be broken into discrete subproblems, and they don’t depend on each other.

### General tips
- Every dynamic-programming solution involves a grid.
- The values in the cells are usually what you’re trying to optimize.
- Each cell is a subproblem, so think about how you can divide
your problem into subproblems. That will help you figure out what the axes are.

### Longest common substring
Length of the longest string they share
|     | h   | i   | s   | h   |
| --- | --- | --- | --- | --- |
| f   | 0   | 0   | 0   | 0   |
| i   | 0   | 1   | 0   | 0   |
| s   | 0   | 0   | 2   | 0   |
| h   | 1   | 0   | 0   | 3   |

1. Fill the grid, if the letter don't match put 0
2. If the letter matches put 1 + the value of top left neighbor
3. Solution is the largest number in the string

#### Implementation
```
def find_grid_max(grid):
    maxval = 0
    maxrow = 0
    maxcol = 0
    for i in range(0, len(grid)):
        for j in range(0, len(grid[i])):
            curr = grid[i][j]
            if (curr > maxval):
                maxval = curr
                maxrow = i
                maxcol = j
    return (maxval, maxrow, maxcol)

def lcs(str1, str2):
    grid = []
    for row in range(len(str1)):
        grow = []
        for column in range(len(str2)):
            grow.append(0)
        grid.append(grow)
    nrows = len(str1)
    ncols = len(str2)
    for i in range(0, nrows):
        for j in range(0, ncols):
            if (str1[i] == str2[j]):
                if (i - 1 >= 0 and j - 1 >= 0):
                    grid[i][j] = 1 + grid[i - 1][j - 1]
                else:
                    grid[i][j] = 1
    val, row, col = find_grid_max(grid)
    print(str1[row - val + 1: row + 1])
```

### Longest common subsequence
How many letters do they share in the same position
|     | f   | o   | s   | h   |
| --- | --- | --- | --- | --- |
| f   | 1   | 1   | 1   | 1   |
| o   | 1   | 2   | 2   | 2   |
| r   | 1   | 2   | 2   | 2   |
| t   | 1   | 2   | 2   | 2   |

|     | f   | o   | s   | h   |
| --- | --- | --- | --- | --- |
| f   | 1   | 1   | 1   | 1   |
| i   | 1   | 1   | 1   | 1   |
| s   | 1   | 1   | 2   | 2   |
| h   | 1   | 1   | 2   | 3   |

1) Fill the grid, if the letters don't match pick the greatest in the same row or column
2) If they do match then value is 1 + the value of the top-left neighbor
3) The last value of the grid is the answer

### Uses
- Biologists use the longest common subsequence to find similarities in DNA strands. They can use this to tell how similar two animals or two diseases are. The longest common subsequence is being used to find a cure for multiple sclerosis.
  
- Have you ever used diff (like git diff)? Diff tells you the differences between two files, and it uses dynamic programming to do so.
  
- We talked about string similarity. Levenshtein distance measures how similar two strings are, and it uses dynamic programming. Levenshtein distance is used for everything from spell-check to figuring out whether a user is uploading copyrighted data.
  
- Have you ever used an app that does word wrap, like Microsoft Word? How does it figure out where to wrap so that the line length stays consistent? Dynamic programming!

## Excercise Answers
- **9.2 Suppose you’re going camping. You have a knapsack that will hold 6 lb, and you can take the following items. Each has a value, and the higher the value, the more important the item is:**
- **Water, 3 lb, 10**
- **Book, 1 lb, 3**
- **Food, 2 lb, 9**
- **Jacket, 2 lb, 5**
- **Camera, 1 lb, 6**

**What’s the optimal set of items to take on your camping trip?**

|                    | 1 lb | 2 lb | 3lb  | 4 lb   | 5 lb    | 6 lb     |
| ------------------ | ---- | ---- | ---- | ------ | ------- | -------- |
| **Water 10, 3lb**  | 0    | 0    | 10 W | 10 W   | 10 W    | 10 W     |
| **Book 3, 1lb**    | 3 B  | 3 B  | 10 W | 13 W B | 13 W B  | 13 W B   |
| **Food 9, 2lb**    | 3 B  | 9 F  | 10 W | 13 W B | 19 W F  | 21 W B F |
| **Jackeet 5, 2lb** | 3 B  | 9 F  | 10 W | 13 W B | 19 W F  | 21 W B F |
| **Camera  6, 1lb** | 6 C  | 9 F  | 10 W | 16 W C | 19  W F | 25 W C F |

Water food camera

**9.3 Draw and fill in the grid to calculate the longest common substring
between blue and clues.**

|     | b   | l   | u   | e   |
| --- | --- | --- | --- | --- |
| c   | 0   | 0   | 0   | 0   |
| l   | 0   | 1   | 0   | 0   |
| u   | 0   | 0   | 2   | 0   |
| e   | 0   | 0   | 0   | 3   |
| s   | 0   | 0   | 0   | 0   |
