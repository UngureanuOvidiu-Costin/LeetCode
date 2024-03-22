```JavaScript
/**
 * @param {number[]} arr
 * @param {Function} fn
 * @return {number[]}
 */
var filter = function(arr, fn) {
    var resultArray = [];
    var temp;
    var truthy;
    for (var i = 0; i < arr.length; i++) {
        temp = fn(arr[i], i)
        truthy = Boolean(temp)
        if(truthy === true){
            resultArray.push(arr[i]);
        }
    }
    
    return resultArray;
};
```
