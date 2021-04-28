sumZero(arr)¶
Write a function called sumZero which accepts a sorted array of integers.
The function should find the first pair where the sum is 0. 
Return an array that includes both values that sum to zero or no record if a pair does not exist.


````ruby

Time: O(n)O(n)
Space: O(1)O(1)

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






## CountUniqueValues(arr)
Implement a function called countUniqueValues, which accepts a sorted array, and counts the unique values in the array. There can be negative numbers in the array, but it will always be sorted.

````ruby


Solution 1

Time: O(n)O(n)
Space: O(1)O(1)

def countUniqueValues arr
  return 0 if arr.length < 0
  j = 0
  len = arr.length - 1
  for i in 0..len
    if arr[i - 1] != arr[i]
      j += 1
    end
  end
  print j
end


Solution 2
Time: O(n)O(n)
Space: O(1)O(1)

def countUniqueValues arr
  return 0 if arr.length < 0
  arr.uniq.length
end

countUniqueValues([1, 1, 1, 1, 1, 2]); 
countUniqueValues([-2, -1, -1, 0, 1]); 
countUniqueValues([]); 

````

