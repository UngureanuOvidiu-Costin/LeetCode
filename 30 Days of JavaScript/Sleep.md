```JavaScript
async function sleep(millis) {
    await new Promise(r => setTimeout(r, millis));
}
```