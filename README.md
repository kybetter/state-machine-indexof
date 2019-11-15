# state-machine-indexof
State machine implementation of indexOf method with O(n) and easy way.

indexOf 方法的状态机实现，只需 O(n) 复杂度，而且写法简单。

```js
let str = "abcdefgabcdefoobcdefgabcdefg";
let match = "foo";

let k = 0; let tmp = ''; let idx = -1;
function start(c, i) {
  console.log(c);
  if (tmp === match) {
    console.log('matched');
    return false;
  } else if (c === match[k]) {
    tmp += c;
    k++;
    if (idx === -1) {
      idx = i;
    }
    console.log('---', tmp);
    return start;
  } else {
    tmp = '';
    k = 0;
    idx = -1;
    return start;
  }
}

let state = start;
for (let i = 0; i <= str.length; i++) {
  state = state(str[i], i);
  if (state === false) {
    break;
  }
}
console.log(idx);
```
