### Same(arr1, arr2)
Write a function called same, which accepts two arrays. The function should return true if every value in the array has it's corresponding value squared in the second array. The frequency of values must be the same

````ruby
Please Dry Me When you have time
def square(arr)
  arr.map do |x|
    x ** 2
  end
end
def same(arr_one,arr_two)
  freq_one = {}
  freq_two = {}
  return false if arr_one.length != arr_two.length
  arr_one = arr_one.sort
  arr_two = arr_two.sort
  len = arr_one.length - 1
  for i in 0..len do
    freq_one[arr_one[i]] = (freq_one[arr_one[i]] || 0 ) + 1
  end
  for i in 0..len do
    freq_two[arr_two[i]] = (freq_two[arr_two[i]] || 0 ) + 1
  end
  arr_one_key = []
  arr_one_key << freq_one.keys
  arr_two_key = []
  arr_two_key << freq_two.keys
  len = arr_one_key.length - 1
  arr_one_values = []
  arr_one_values << freq_one.values
  arr_two_values = []
  arr_two_values << freq_two.values
  for i in 0..len
    return false if square(arr_one_key[i]) != arr_two_key[i]
    return false if freq_one[arr_one_key[i]] != freq_two[arr_two_key[i]]
    if square(arr_one_key[i]) != arr_two_key[i]
      return false 
    elsif arr_one_values[i] != arr_two_values[i]
      return false
    end
  end
  true
end
 
puts same([1, 2, 3], [4, 1, 9])
puts same([1, 2, 3], [1, 9])
puts same([1, 2, 1], [4, 4, 1])
````

### ValidAnagram(arr1, arr2)
Given two strings, write a function called validAnagram to determine if the second string is an anagram of the first. An anagram is a word, phrase, or name formed by rearranging the letters of another, such as cinema, formed from iceman.

````ruby 
def validAnagram str_one,str_two
  return false if str_one.length != str_two.length
  freq_one = {}
  len = str_one.length - 1
  str_two = str_two.split("")
  # frequency counter pattern
  for i in 0..len
    freq_one[str_one[i]] = (freq_one[str_one[i]]||0)+1
  end

  for i in 0..len
    return false if !freq_one.key?(str_two[0])
    # check if present then minus 1 from the hash value 
    freq_one[str_two[0]] = freq_one[str_two[0]] - 1
    #if the hash value is equal to zero delete it
    if freq_one[str_two[0]] == 0
      freq_one.delete(str_two[0])
    end
    str_two.shift
  end
  true
end


puts validAnagram('', '')
puts validAnagram('aaz', 'zza')
puts validAnagram('anagram', 'nagaram')
puts validAnagram('anagam', 'nagaram')
````
## AreThereDuplicates(...args)
Implement a function called, areThereDuplicates which accepts a variable number of arguments, and checks whether there are any duplicates among the arguments passed in. You can solve this using the frequency counter pattern OR the multiple pointers pattern.

````ruby
def areThereDuplicates *args
  freq_one = {}
  len = args.length - 1
  for i in 0..len
   return true if freq_one.include?(args[i]) 
   freq_one[args[i]] = (freq_one[args[i]] || 0 ) + 1
  end
  false
end



puts areThereDuplicates(1, 2, 3)
puts areThereDuplicates(1, 2, 2)
puts areThereDuplicates('a', 'b', 'c', 'a')
````
