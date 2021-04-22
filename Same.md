````ruby

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
