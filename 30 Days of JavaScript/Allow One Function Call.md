```JavaScript
var once = function(fn) {
    
    let neverCalled = true;
    let result = undefined;

    return function(...args){
        if(neverCalled === true){
            neverCalled = false;
            return fn.apply(this, arguments);
        }else{
            return result;
        }
    }
};
```