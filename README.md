# Coding-Challenges
## Array
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

