# Coding-Challenges 
- [Array](#array)



## Array
````javascript
class MyArray {
  constructor(){
    this.length = 0 
    this.data = {}
  }
  getAll(){
    return this.data // get all data
  }
  get(index){
    return this.data[index]
  }
  push(item){
    this.data[this.length++] = item; // insert a new data and increase length by 1
    return this.data
  }
  pop(){
    const lastItem = this.data[this.length - 1]; 
    delete this.data[this.length - 1]; //remove the last data
    this.length --; //reduce length by one
    return lastItem
  }
  deleteindex(index){
    const item = this.data[index]
    this.shift(index) 
    return item 
  } 
  shift(index){
    for(let i = index; i < this.length; i++ ){
      this.data[i] = this.data[i + 1] // change data as from index till the end
    }
    delete this.data[this.length - 1] //remove the last data
    this.length --; //reduce length by one
  }
}

const array = new MyArray();
array.push(4)
array.push(5)
array.push(4)
array.push(7)
array.deleteindex(2)
array.getAll()

````
## Spriral Print
### Let’s create an example problem with a matrix. Given a matrix, print the elements in spiral order.
###### Solution
https://www.techiedelight.com/print-matrix-spiral-order/
 

````javascript
 const sprialPrint = (m) => {
 let top = 0;
 let bottom = m.length - 1;
 let left = 0;
 let right = m[0].length - 1;
while (1)
	{
		if (left > right)
			break;
		// print top row
		for (let i = left; i <= right; i++){
			console.log(m[top][i]);
    }
		top++;

		if (top > bottom)
			break;
		// print right column
		for (let i = top; i <= bottom; i++){
			console.log(m[i][right]);
    }
		right--;

		if (left > right)
			break;
		// print bottom row
		for (let i = right; i >= left; i--){
			console.log(m[bottom][i]);
    }
		bottom--;

		if (top > bottom)
			break;
		// print left column
		for (let i = bottom; i >= top; i--){
			console.log(m[i][left]);
    }
		left++;
	}
}

const m = [
  [1,87,5,6],
  [11,2,3,1],
  [9,3,35,4],
  [5,2,27,8]
]

sprialPrint(m)
````
Toeplitz Matrix
A Toeplitz matrix is a matrix where every left-to-right-descending diagonal has the same element. Given a non-empty matrix arr, write a function that returns true if and only if it is a Toeplitz matrix. The matrix can be any dimensions, not necessarily square.


````ruby
def toePmatrix(a)
  c  = a.length - 1
  r  =  a[0].length - 1
  c.times do |i|
    r.times do |j|
      if a[i][j] != a[i + 1][j + 1]
        return false
      end
    end
  end
  return true
end
	a = [
		[3, 7, 0, 9, 8],
		[5, 3, 7, 0, 9],
		[6, 5, 3, 7, 0],
		[4, 6, 5, 3, 7]
	]
puts toePmatrix(a)
````


#### Rotate Image
You are given an n x n 2D matrix that represents an image. Rotate the image by 90 degrees (clockwise).
##### Solution 
https://github.com/tinwatchman/2d-array-rotation/blob/master/2d-array-rotation.js
https://medium.com/front-end-weekly/matrix-rotation-%EF%B8%8F-6550397f16ab
````javascript

a = [[1, 2, 3],
     [4, 5, 6],
     [7, 8, 9]]
 
function rotateImage(a) {
   	const c = a.length;
	const r = a[0].length;
	let b = new Array(r);
	for (let y=0; y<r; y++) {
		b[y] = new Array(c);
		for (let x=0; x<c; x++) {
			b[y][x] = a[c-1-x][y];
		}
	}
	return b;
	}
=========================================================================
function rotateImage(a) {
const flipMatrix = a => (
  a[0].map((column, index) => (
    a.map(row => row[index])
  ))
);
const rotateMatrix = a => (
  flipMatrix(a.reverse())
);

return rotateMatrix(a)
}
=========================================================================
Ruby
def rotateImage(a)
  def flip(a)
    a.transpose.each do |ary|
     ary
    end
  end
  def reverseMe(a)
    flip(a.reverse)
  end
 reverseMe(a)
end

//Another solution

def rotateImage(a)
    b = []
    a.transpose.each do |ary|
     b << ary.reverse
    end
  b
end
````



### MaxSubarraySum
````ruby
Write a function callled maxSubarraySum which accepts an array of intergers and a number called n.The function should calculate the maximum sum of n consecutive elements in the array.
def max_sub_array(nums,k)
    newSize = k 
    result = 0
    len = nums.size - 1
    newSize.times do |i|
        result += nums[i]  
    end

    temp = result
    for i in newSize..len
        temp = (temp - nums[i - newSize]) + nums[i]
        result = temp > result ? temp : result
    end
    result
end
puts max_sub_array([4,2,1,6],2)
````
````ruby 
Given an array of integers, find the pair of adjacent elements that has the largest product and return that product.

Example

For inputArray = [3, 6, -2, -5, 7, 3], the output should be
adjacentElementsProduct(inputArray) = 21.

7 and 3 produce the largest product.


def adjacentElementsProduct(inputArray)
# use sliding window to check for the max product
  numIn = 2 
  result = 1
  numIn.times{|i|
      result *= inputArray[i]
  } 
  if result == 0
    return 0
  end 
  temp = result
  for i in numIn..inputArray.length - 1
    temp = (temp / inputArray[i - numIn ]) * inputArray[i]
    result = result < temp ? temp : result
  end
  result
end
````
### Given an array of integers, return indices of the two numbers such that they add up to a specific target.
https://levelup.gitconnected.com/solving-the-two-sum-problem-in-javascript-three-ways-4d43067fcfc7
https://medium.com/@paulrohan/solving-the-classic-two-sum-and-three-sum-problem-in-javascript-7d5d1d47db03
`````javascript
var twoSum = function(nums, target) {
    let newObj = {};
  let newArr = [];
  for(let j = 0; j<nums.length; j++){
    let diff = target - nums[j]; // minus the array element and the sum
    if(diff in newObj){ // check if the difference is in the hash
      newArr.push(nums.indexOf(diff), nums.indexOf(nums[j])); //add the array element and the diff into a new array
    }
    newObj[nums[j]] = j; // for every iteration create a new hash
  }
  return newArr;
};
`````

## Binary 
### Calculate the sum of two integers a and b, but you are not allowed to use the operator + and -.
https://www.geeksforgeeks.org/add-two-numbers-without-using-arithmetic-operators/
#### Recursion approach
````javascript
var getSum = function(a, b) {
 if (b == 0){
     return a 
     }else{
  return getSum(a ^ b, (a & b) << 1)   
 }
};
````
## Normal approach
````javascript
var getSum = function(a, b) {
    while(b!=0){
        const carry = a & b //set bit of a and b
        a = a ^ b //sum of the bits of a & b
        b = carry << 1 // carry is shifted by one so that adding it to a gives the required sum
    }
return a
};
`````

