# ES2015 (ES6) questions

* [var / let / const](https://github.com/artemdemo/frontend-interview-questions/blob/master/es2015-questions.md#var--let--const)
* [Templates](https://github.com/artemdemo/frontend-interview-questions/blob/master/es2015-questions.md#templates)
* [Declare](https://github.com/artemdemo/frontend-interview-questions/blob/master/es2015-questions.md#declare)
* [Is it legal or not](https://github.com/artemdemo/frontend-interview-questions/blob/master/es2015-questions.md#is-it-legal-or-not)

---

## var / let / const

**Q.** What's the output?

```javascript
const KEY = 'white_rabbit';
if (true) {
  const KEY = 'ginger_rabbit';
}
console.log(KEY);
```

**A.**

```
white_rabbit
```

---

**Q.** What's the output?

```javascript
let x = 42;
if (true) {
  let x = 1337;
}
console.log(x);
```

**A.**

```
42
```

---

**Q.** What's the output?

```javascript
let x = 42;
if (true) {
  console.log(x);
  let x = 1337;
}
```

**A.**

```
ERROR
```

## Templates

**Q.** What's the output?

```javascript
var x = `foo ${y}`,
    y = `bar ${x}`;

console.log(x);
```

**A.**

```
foo undefined
```

---

**Q.** What's the output?

```javascript
var x = `foo ${y}`,
    y = `bar ${x}`;

console.log(y);
```

**A.**

```
bar foo undefined
```

## Declare

**Q.** In ES6, is there a better way to create this object?

```javascript
let options = {
  protocol: protocol,
  url: url,
  method: method,
  callback: callback
};
```

**A.**

```javascript
let options = {
  protocol,
  url,
  method,
  callback
};
```

## Is it legal or not

**Q.** 

```javascript
var score = [12, 7, 14];
Math.max(...score);
```

**A.**

```
Yes
```

---

**Q.** 

```javascript
function stuff(x, y=x/3) {
  // Do stuff..
}
stuff(6);
```

**A.**

```
Yes
```
