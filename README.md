# Coding-Challenges
https://levelup.gitconnected.com/solving-the-two-sum-problem-in-javascript-three-ways-4d43067fcfc7
https://medium.com/@paulrohan/solving-the-classic-two-sum-and-three-sum-problem-in-javascript-7d5d1d47db03
`````javascript
var twoSum = function(nums, target) {
    let newObj = {};
  let newArr = [];
  for(let j = 0; j<nums.length; j++){
    let diff = target - nums[j];
    if(diff in newObj){
      newArr.push(nums.indexOf(diff), nums.indexOf(nums[j]));
    }
    newObj[nums[j]] = j;
  }
  return newArr;
};
````
