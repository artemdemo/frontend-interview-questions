# JavaScript questions

* [Operators](https://github.com/artemdemo/frontend-interview-questions/blob/master/js-questions.md#operators)
* [Types](https://github.com/artemdemo/frontend-interview-questions/blob/master/js-questions.md#types)
* [Reference/alias](https://github.com/artemdemo/frontend-interview-questions/blob/master/js-questions.md#referencealias)
* [Functions](https://github.com/artemdemo/frontend-interview-questions/blob/master/js-questions.md#functions)
* [URL, data](https://github.com/artemdemo/frontend-interview-questions/blob/master/js-questions.md#url-data)

---

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

---

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

```javascript
5 - "4"    // number 1
5 + "4"    // string "54"
5 + null   // number 5
!{}[true]  // boolean true
+[1]       // number 1
+[1, 2]    // NaN
7 - "a"    // NaN
7 / 0      // Infinity
```

---

**Q.** What will be result ofeach of following exprassions? Explain why their are differ:

```javascript
0 == false
0 == null
null == false
```

**A.**

```javascript
0 == false      // true
0 == null       // false
null == false   // false
```


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

---

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
We can use JSONP as a solution (see next question).

---

**Q.** What is JSONP? How and when you will use it?

**A.**
JSONP, which stands for "JSON with Padding" (and JSON stands for JavaScript Object Notation), is a way to get data from another domain that bypasses CORS (Cross Origin Resource Sharing) rules.

Say you're on domain example.com, and you want to make a request to domain example.net. To do so, you need to cross domain boundaries, a no-no in most of browserland. We can bypasses this limitation by using `<script>` tags.

We can use following link witk callback in order to process data:

```javascript
script = document.createElement('script');
script.type = 'text/javascript';
script.src = 'http://www.example.net/sample.php?callback=mycallback';
```

Then we can add global function `mycallback`, that will get data from the server.

```javascript
mycallback = function(callbackData){
  console.log(callbackData);
};
```
