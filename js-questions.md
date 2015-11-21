# JavaScript questions

## Operators

**Q.** What will be value of `y`?

```javascript
var y,
    x = 1;
    
y = x+++x;
```

**A.** `y = 3`

**Explanation** First will be calculated `x++`, it will return `1` and after the value of `x` will be increased by `1`.
Therefore at the end we will have `1 + 2`


## Types

**Q.** What types javascript has?

**A.** There is 6 types:

```
object
number
string
boolean
null
undefined
```

**Q.** In the following code - what will be value of `foo` and what you suggest to do to improve this code?


```javascript
var foo;
    
foo = '20' + 10;
```

**A.** `foo = 2010`.

There is 3 ways to improve it:

```javascript
foo = +'20' + 10;
```

or

```javascript
foo = parseInt('20') + 10;
```

or

```javascript
foo = Number('20') + 10;
```

---

**Q.** You have variable that may or may not be a number.
Write function `isNumber()` that will return `true` if it is in fact number or `false` otherwise.

**A.**

```javascript
function isNumber(str) {
    return Number(str) == Number(str);
}
```

**Explanation** `Number()` of something that can't be converted to number will return `NaN`
and by specification of ECMAScript `NaN` not equal to `NaN`

---

**Q.** Explain what will be output of each of following expressions:

```javascript
5 - "4"
5 + "4"
5 + null
!{}[true]
+[1]
+[1, 2]
7 - "a"
7 / 0
```

**A.**

---

**Q.** What will be result ofeach of following exprassions? Explain why their are differ:

```javascript
0 == false
0 == null
null == false
```

**A.**


## Reference/alias


**Q.** What output you will see in the console?

```javascript
var obj = {
    foo: []
}
var boo = obj.foo;

boo.push('Hi there!');

obj.foo = obj.foo.concat(boo)

console.log(obj);
```

**A.**

```javascript
{
    foo: [
        'Hi there!',
        'Hi there!'
    ]
}
```

**Explanation** `boo` will contain reference to the `obj.foo` and not the value of it.
Therefore by pushing to the `boo` you'll actually push to `obj.foo`


## Functions


**Q.** Describe what is the following construction, when and why you will use it

```javascript
(function() {})()
```

**A.**
It's immediately-invoked function expression (IIFE). JavaScript will execute whatever will be in this function as soon as it gets here. Code inside of thies funcion will have its own scope.


**Q.** Write code, that will provide following behaviour:

```
add(3)(4) == 7;
```

**A.** You should use carrying

```
function (a) {
    return function (b) {
        return a + b;
    }
}
```




## URL, data

**Q.** You have relative URL `category/15/products?sort=name&order=DESC`, how you will get full URL from it?

**A.**

```javascript
var link = document.createElement('a');
link.href = 'category/15/products?sort=name&order=DESC';
console.log(link.protocol+'//'+link.host+link.pathname+link.search+link.hash)
```

---

**Q.** You have cross domain error for your script, how you will load it.

**A.**

---

**Q.** What is JSONP? How and when you will use it?

**A.**


