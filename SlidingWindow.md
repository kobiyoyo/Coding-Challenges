## Sliding Window
This pattern involves creating a window which can either be an array or number from one position to another.
Depending on a certain condition, the window either increases or closes (and a new window is created).
Very useful for keeping track of a subset of data in an array/string etc.

This strategy is a bit trick so i need to break it down 

- Define two variables result and temp which will be equal to zero
- Create a for loop to add up the first n  values to result
- Assign result to temp
- Write a for loop that starts from the nth values to the arr length
- Inside the for loop (temp = temp - arr[i - n] + arr[i])
- Return the max between temp and result and assign to result
- Return result 

