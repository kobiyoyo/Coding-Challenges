sumZero(arr)¶
Write a function called sumZero which accepts a sorted array of integers.
The function should find the first pair where the sum is 0. 
Return an array that includes both values that sum to zero or no record if a pair does not exist.

Time: O(n)O(n)
Space: O(1)O(1)

````ruby
def sumZero arr
  right = arr.length  - 1
  left  = 0
  target = 0
  while left < right do
    sum =  arr[left] + arr[right]
    if sum == target
      return [arr[left],arr[right]]
    elsif sum < target
      left += 1
    else
      right -= 1
    end
  end
  "no record found"
end


puts sumZero([-3, -2, -1, 0, 1, 2, 3]); 
puts sumZero([-2, 0, 1, 3]);
puts sumZero([1, 2, 3]);
puts sumZero([1, 2, 3,-2]);
````
