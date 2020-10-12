#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a) O(n)
We have 1 loop that will terminate based on how many times it takes to increment A to equal N.
The means the runtime for this psuedo code will grow at the same rate as N. For instance if N is 1 the loop will only have to run 1 time. If N is 2, the function will loop 2 times. If N is 10, it loops 10 times. Etc etc.


b)O(n log n)
We are looping through the same input list twice with the for and while loops, which makes this code block an O(n^2) solution. The runtime for this code will grow quickly as the number of inputs increase and probably isn't an ideal solution if the numbers of inputs will be a large number. For instance if n is 2, this loop will only need to run 1 time. If n is 4, the loop will need to run 8 times. If n is 10, will need to run 40 times. If n is 25, this loop will run 125 times. You can see the runtime is increasing at a much faster rate than the rate than n increases.


c) O(n)
This is a recursive solution that is looping based on the number of bunnies. Depending on the number of bunnies we have (n) will determine how many times we have to call this function. We can test this by increasing our number of inputs and checking how many times the function is called. If we input 2 bunnies, we see the function is called 2 times. If we input 4, we see the function is called 4 times. Same with 10 bunnies, we loop the function 10 times.

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
