- [Greedy Algorithms](#greedy-algorithms)
- [Approximation Algorithms](#approximation-algorithms)
- [NP-complete problems](#np-complete-problems)
    - [How to tell if a problem is NP-Complete?](#how-to-tell-if-a-problem-is-np-complete)
- [Excercises Answers](#excercises-answers)

## Greedy Algorithms
- Simple algorithms in which at each step you pick the locally optimal solution and at the end you end up with the globallly optimal solution
    - You want to steal something fron the store but you can only store 35 kg. So you choose the most expensive object that fits, and then you  do it again. This won't always give you the best solution but it will give a pretty good one.
- Simple algorithms are not perfect, but they are pretty good which means they won't give you the best solution but will get you to a solution pretty close to the optimal.

## Approximation Algorithms
- Greedy algorithm used when calculating the perfect solution is imposible due to the time complexity of it.
    - Some problem in which you would need to calculate each of the posible scenarios
- Aproximation Algorithms judged by:
    - How fast they are
    - How close they are to the optimal solution

## NP-complete problems
- NP stands for Non-deterministic Polynomial
- NP-complete problems are problems which can not be solved in polynomial time in any known way.
    - They are not solvable in a realistic time
- Examples:
    - Traveling sales person
    - set-covering
        - Like the radio station example.
- In this problem you solve them with a greedy algorithm

### How to tell if a problem is NP-Complete?
- Your algorithm runs quickly with a handful of items but really slows down with more items.
- “All combinations of X” usually point to an NP-complete problem
- Do you have to calculate “every possible version” of X because you can’t break it down into smaller sub-problems? Might be NP-complete
- If your problem involves a sequence (such as a sequence of cities, like traveling salesperson), and it’s hard to solve, it might be NP-complete.
- If your problem involves a set (like a set of radio stations) and it’s hard to solve, it might be NP-complete.
- Can you restate your problem as the set-covering problem or the traveling-salesperson problem? Then your problem is definitely NP-complete.


  
**NOTA: Polynomial time like O(n^2) or any time complexity**
- the time required for a computer to solve a problem, where this time is a simple polynomial function of the size of the input.

## Excercises Answers
- **8.1 You work for a furniture company, and you have to ship furniture
all over the country. You need to pack your truck with boxes. All
the boxes are of different sizes, and you’re trying to maximize the space you use in each truck. How would you pick boxes to maximize space? Come up with a greedy strategy. Will that give you the optimal solution?**

Pick the biggest box that fits and then keep doing it again and again. This won't always give you the best answer but it will give you a good approximation.

- **8.2 You’re going to Europe, and you have seven days to see everything you can. You assign a point value to each item (how much you want to see it) and estimate how long it takes. How can you maximize the point total (seeing all the things you really want to see) during your stay? Come up with a greedy strategy. Will that give you the optimal solution?**
  
Go to the places in which you want to go the most and that fits in the time you have. Then repeat. It won't but is a good aproximation.

- **For each of these algorithms, say whether it’s a greedy algorithm or not.**
    - **8.3 Quicksort**: NO
    - **8.4 Breadth-first search**: YES
    - **8.5 Dijkstra’s algorithm**: YES

- **8.6 A postman needs to deliver to 20 homes. He needs to find the shortest route that goes to all 20 homes. Is this an NP-complete problem?**

YES

- **8.7 Finding the largest clique in a set of people (a clique is a set of people who all know each other). Is this an NP-complete problem?**
  
YES

- **8.8 You’re making a map of the USA, and you need to color adjacent states with different colors. You have to find the minimum number of colors you need so that no two adjacent states are the same color. Is this an NP-complete problem?**

YES