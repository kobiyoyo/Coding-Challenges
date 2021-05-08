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
## MinSubArrayLen(arr, num)¶
Write a function called minSubArrayLen which accepts two parameters - an array of positive integers and a positive integer.

This function should return the minimal length of a contiguous subarray of which the sum is greater than or equal to the integer passed to the function. If there isn’t one, return 0 instead.
````ruby
Time: O(n)O(n)
Space: O(1)O(1)
def minSubArrayLen arr, num
 i = 0
 j = 0 
 sum = 0 
 result = Float::INFINITY
 len = arr.length - 1
 while i < len
  if sum < num && j < len
    sum += arr[j]
    j += 1
  elsif sum >= num
    result = [result,j - i].min
    sum -= arr[i]
    i += 1
  else
    break
  end
 end
 return result == Float::INFINITY ? 0 : result
end


p minSubArrayLen([2, 3, 1, 2, 4, 3], 7)
p minSubArrayLen([2, 1, 6, 5, 4], 9)
p minSubArrayLen([3, 1, 62, 19], 52)
````
