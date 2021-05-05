## Sliding Window
This pattern involves creating a window which can either be an array or number from one position to another.
Depending on a certain condition, the window either increases or closes (and a new window is created).
Very useful for keeping track of a subset of data in an array/string etc.

This strategy is a bit tricky so i need to break it down 

- Define two variables result and temp which will be equal to zero
- Create a for loop to add up the first n  values to result
- Assign result to temp
- Write a for loop that starts from the nth values to the arr length
- Inside the for loop (temp = temp - arr[i - n] + arr[i])
- Return the max between temp and result and assign to result
- Return result 


## MaxSubarraySum(arr, n)
Write a function called maxSubarraySum which accepts an array of integers and a number called n. The function should calculate the maximum sum of n consecutive elements in the array.

````ruby
    Time: O(n)O(n)
    Space: O(1)O(1)
    
    def maxSubarraySum(arr,n)
      return nil if arr.length < n
      return arr.max if n == 1
      n = n - 1
      result = 0 
      temp = 0 
      for i in 0..n 
        result += arr[i]
      end
      temp = result
      len  = arr.length - 1
      for i in n..len
        temp = temp - arr[i - n] + arr[i]
        result = temp if temp > result
      end
      result
    end


p maxSubarraySum([1, 2, 5, 2, 8, 1, 5], 2)
p maxSubarraySum([1, 2, 5, 2, 8, 1, 5], 4)
p maxSubarraySum([4, 2, 1, 6], 1)
p maxSubarraySum([], 4)

````
