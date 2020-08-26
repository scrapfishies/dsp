# Complexity

An algorithm's complexity is a measure of the resources it uses.  We care about the amount of memory an algorithm requires (space complexity), but most commonly, we discuss complexity we are referring to the time it takes an algorithm to run (time complexity).

We will discuss computational complexity in much more detail during the bootcamp, but now let's get started with a few resources about Big-O notation.

Big-O notation is used to classify the worst-case "speed" of an algorithm by looking at the order of magnitude of execution time. Read through the following to get a sense of what Big-O notation is and why it matters:

- [Stack Overflow: "What is a plain English explanation of 'Big O' notation?"](https://stackoverflow.com/questions/487258/what-is-a-plain-english-explanation-of-big-o-notation)
- [Chris Albon's write-up on the basics of Big-O](https://chrisalbon.com/computer_science/algorithms/big-o_notation/)
- [Big-O Cheat Sheet](https://www.bigocheatsheet.com/)
 
## Scrapfish Notes 

**Big-O** is a theoretical definition of the ***time complexity*** of an algorithm as a function of the size. The 'O' refers to 'order of magnitude of complexity'. *Time complexity* is the computational complexity that describes the amount of time it takes to run an algorithm, estimated by counting the number of elementary operations performed by the algorithm (supposing that each operation takes a fixed amount of time to perform). 
* Big-O is ***relative*** - we need to compare one or more algorithms to put it in context
* Big-O gives us an ***objective view*** on the *performance* of an algorithm: here is why x-algorithm is better than y-algorithm. 
* Big-O is sometimes referred to as the ***upper bounds***, where the algorithm is performing under the *worst case scenario*. 
* Notation example: `O(n)`

## Types in order of efficiency (best to worst)

**Visualizing Big O Complexity:**

![](https://miro.medium.com/max/1400/1*yiyfZodqXNwMouC0-B0Wlg.png)

![](https://miro.medium.com/max/1400/1*5ZLci3SuR0zM_QlZOADv8Q.jpeg)


### Excellent

**Constant Time**: `O(1)`: The runtime of the algorithm is *independent* of the size of the data set. If n is 1 or 1 million, it takes the same amount of time to execute the algorithm. 

![](https://miro.medium.com/max/626/1*AJ09oN6ANIz_5XUPv6cmgg.png)

Python example:
```javascript
data = [1, 2, 9, 8, 4, 5]

def get_first(data):
  return data[0]
```
It doesn't matter how big the input list is - it's only returning the first item, which will *always* have the same runtime.


**Logarithmic Time**: `O(log n)`: The runtime of the algorithm increases *logarithmically* as the size of the data set increases. 
* Logarithms are basicaly inverse exponents (`log2 of 8 = 3` --> `2^3 = 8`); and so if the input size *doubles*, the runtime increases by *one*.
* Classic example: ***binary search*** algorithms
* Sometimes referred to as *sublinear*

![](https://miro.medium.com/max/626/1*4MN1PhTNpluNK62Fj4OREg.png)

```javascript
# data must be sorted!
data = [1, 2, 3, 4, 5, 6, 7, 8, 9]

def binary_search(data, target):
  first, last = 0, len(data) -1
  
  while first <= last:
    midpoint = (first + last) // 2
    
    if data[midpoint] == target:
      return midpoint
    elif list[midpoint] < target:
      first = midpoint + 1
    else: 
      last = midpoint - 1
  
  return None      
```


### Verge of okay

**Linear Time**: `O(n)`: The runtime of the algorithm is *directly proportional* to the size of the data set.
* Linear time can be more performative than binary search up to a certain point because of the *sorted* requirement of binary search, which could be a substantial task given the data. 
* Classic example: ***linear search*** algorithms 

![](https://miro.medium.com/max/626/1*z_GjT7UHF1MeE__PnQictQ.png)

```javascript
data = [1, 2, 9, 8, 3, 4, 7, 6, 5]

def linear_search(data, target):
  for i in range(0, len(data)):
    if list[i] == target:
      return i
  return None      
```


### Not so great

**Quasilinear Time**: `O(n log n)`: Given a data set size of n, the algorithm executes `n` number of operations where each operations runs in logarithmic time (log n). 
* Good example: [Merge Sort](https://en.wikipedia.org/wiki/Merge_sort)
* [Merge Sort in Code](https://teamtreehouse.com/library/algorithms-sorting-and-searching/sorting-algorithms/code-for-merge-sort)
  
![](https://miro.medium.com/max/800/1*a7UnRSbux0RSgVqmFDN9_Q.png)


### Bad

**Polynomial Time**: `O(n^k)`: An algorithm that, for a given value of n, it's worst case runtime is the form of n^k. 
* Typically, ***nested `for` loops*** lead to polynomial time, where `k` is a loop (2 loops = `n^2`; 3 loops = `n^3`)
* **Quadratic Time**: `O(n^2)`: The runtime of the algorithm increases by a factor of n-squared as the size of the data increases
  * Example: [Bubble Sort](https://en.wikipedia.org/wiki/Bubble_sort)
* **Cubic Time**: `O(n^3)`
* etc. 

![](https://miro.medium.com/max/1000/1*kLelWVP6t2YjoVoyAyDgdQ.png)


### Horrible

**Exponential Time**: `O(k^n)`: A runtime where the number of operations increases exponentially as the size of the data set increases. These are considered *inefficient*. 
* Examples: Using ***brute force*** to solve a digit combination lock by guessing every single number.
  * `k` = the possible numbers in the combination lock: 0-9, so 10 choices
  * `n` = number of digits in the combination lock
  * for a 2 digit lock, there are `10^2` or 100 possibile combinations
  * for a 3 digit lock, there are `10^3` or 1,000 possible combinations
  * for a 4 digit lock, therea re `10^4` or 10,000 possible combinations
* Similarly, using brute force to crack passwords:
  * `k` = 69 possible characters (letters, numbers, special characters)
  * `n` = number of allowed characters in a password
  * A 20 charachter password has `69^20`, or 6e36 possible combinations (that's a 6 with *36 zeros* after it!)

**Combinatorial / Factorial Time**: `O(n!)`: Runtimes where as the size of n increases, the number of operations increases by n!. 
* Classic example: [Traveling Salesman Problem](https://en.wikipedia.org/wiki/Travelling_salesman_problem) - there are `n` towns, each of those towns is linked to 1 or more other towns by a road of a certain distance. The traveling salesman problem is to find the shortest tour that visits every town: 
  * If you have 3 towns(A, B, and C), there are 6 possible routes: `3!` = `3*2*1` = `6`
  * If you have 4 towns, it increases to 12 possibilities, `4!`
  * If you have 6 towns, it increases to 360, `6!`
  * by the time you get to 200 towns, there isn't enough time left in the universe to solve the problem with traditional computers. 


## More resources
* [Big-O Time Complexity: What it is a dnw hy it matters for your code](https://levelup.gitconnected.com/big-o-time-complexity-what-it-is-and-why-it-matters-for-your-code-6c08dd97ad59)
* [Understanding Time Complexity with Python Examples](https://towardsdatascience.com/understanding-time-complexity-with-python-examples-2bda6e8158a7)
* [A coffe break introduction to time complexity of algorithms](https://victoria.dev/blog/a-coffee-break-introduction-to-time-complexity-of-algorithms/)
