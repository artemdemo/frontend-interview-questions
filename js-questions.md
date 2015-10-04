# JavaScript questions

**Q.** What will be value of `y`?

```javascript
    var y,
        x = 1;
        
    y = x+++x;
```

**A.** `y = 3`

**Explanation** First will be calculated `x++`, it will return `1` and after the value of `x` will be increased by `1`.
Therefore at the end we will have `1 + 2`

---

**Q.** You have following code:

```javascript
    var foo;
        
    foo = '20' + 10;
```

What will be value of `foo` and what you suggest to do to improve this code?

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
