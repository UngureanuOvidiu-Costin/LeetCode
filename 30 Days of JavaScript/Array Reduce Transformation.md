```JavaScript
/**
 * @param {number[]} nums
 * @param {Function} fn
 * @param {number} init
 * @return {number}
 */
var reduce = function(nums, fn, init) {
    var val = init;
    for(var i = 0; i < nums.length; i = i + 1){
        val = fn(val, nums[i]);
    }
    return val;
};
```
