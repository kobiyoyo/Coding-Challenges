# Coding-Challenges 
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
#### Let’s create an example problem with a matrix. Given a matrix, print the elements in spiral order.
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

