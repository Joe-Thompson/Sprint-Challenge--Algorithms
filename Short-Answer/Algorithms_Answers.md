#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a) O(n): will run n times till (a) is greater than our condition 


b) O(n log n): as n is increased our runtime will grow at a slightly faster rate 
 

c) O(n): the function is recursive and will run n times

## Exercise II

Thinking of the building as a sorted array, index 0 is the smallest and the 
len(building) is the top floor, we can use a binary search to find which floor
we can safely drop eggs from.  

The first step would be to define a pivot, in this case to limit the number
of broken eggs I would first find the length or height of the building and
divide by two to find the middle floor and drop my first egg. 

If the egg does not break we will discard all left values and move our 
pivot to the right.  If we follow the same logic as above and move our pivot
to the middle of our right side array we run the risk of over shooting our target floor.  
However, if we went with a linear approach and started testing each floor from our previous
pivot(+ 1) we run the risk of slowing down our search and moving away from the benefits of 
binary search.  I believe following the logic above and moving our pivot to the middle of our 
right side array would be the best approach, and most likely lead to less broken eggs

Likewise if the egg did break on our first drop we would discard the right side of the array  
and move our pivot to the middle of the left side of the array.

I believe we would have to base cases depending on our initial drop, and which side of the array 
we are working on.  

Right Side, looking for a broken egg:
Our right side base case is to find a floor that the egg breaks on.  Say we have 100 floors, we 
drop on floor 50 and the egg doesn't break, we move to floor 75 because we discarded floors 1 - 50
as floors that would not break the egg.  When we drop the egg from floor 75 it breaks, we now know 
the egg breaks on floor 75.  We now have a range from 51 - 75, we can now move iteratively backwards
to floor 51 and find our safe floor. 

Left Side, looking for a safe egg:
Our left side base case is to find a floor that does not break the egg.  We move our pivot to the middle
of our left side array and repeat the reverse logic found above in our right side situation.

 Runtime: O(n log n)