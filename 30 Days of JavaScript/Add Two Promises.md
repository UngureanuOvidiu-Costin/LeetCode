```JavaScript
var addTwoPromises = async function(promise1, promise2) {
    return new Promise((resolve, reject) => {
    Promise.all([promise1, promise2])
      .then(([value1, value2]) => {
        const sum = value1 + value2;
        resolve(sum);
      })
      .catch(reject);
  });
};
```