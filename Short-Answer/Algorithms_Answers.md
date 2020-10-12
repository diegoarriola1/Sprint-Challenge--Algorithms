#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a) O(n)
We have 1 loop that will terminate based on how many times it takes to increment A to equal N.
The means the runtime for this code will grow at the same rate as N. For instance if N is 1 the loop will only have to run 1 time.


b)O(n log n)
The runtime complexity of this block of code would be O(n log n) (linearithmic), where n is the input size. This is because the outer for loop runs n times, for a runtime complexity of O(n). Meanwhile, the value of j in the inner while loop is doubling rather than incrementing, resulting in a runtime complexity of O(log ). For nested loops, we want to multiply the runtime complexities, so we would get a combined runtime complexity of O(n log n).


c) O(n)
Because we only have linear operations, while we are taking a lot of memory space, the run time stays at n.

## Exercise II

I'm assuming n is a list of floors, and I'll have a 2nd argument that is the floor where the egg will crack. Check the length of n. If it's less than or equal to 1 return the value of n Find the halfway point in your list. Break the list at the halfway point into 2 lists. If the floor we are looking for is in the first list, call the egg drop function and start the process again with the first half of the list. If the floor we are looking for is the second list, call the egg drop function and start the process again with the second half of the list.

Runtime: O(log n). Even though I'm using recursion, because we are halving the inputs every time we call the function, it's very efficient. I ran my code at 100 floors vs. 50,000 floors and the function ran 8 times vs 17 times, respectively. This shows us that even though the difference in inputs is great, the rate of our runtime is not growing at the same rate of our input. It is growing some though which is why it cannot be O(n).


Code:

def egg_drop(n, f):
    if len(n) <= 1:
      return n
    #divide the floors into two halves until the output is less than f
    mid = len(n) // 2
    x = n[:mid]
    y = n[mid:]
    if f <= x[-1]:
      return egg_drop2(x, f)
    elif f >= y[0]:
      return egg_drop2(y, f)
    else:
      return "Floor not in building"
