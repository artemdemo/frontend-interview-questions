# CSS questions

# Pseudo classes

**Q.** You have the following html code:

```html
<div class="row">
    <div class="item"></div>
    <div class="item"></div>
    <div class="item"></div>
    <div class="item"></div>
    <div class="button"></div>
</div>
```

Please describe what you will see on the screen after applying following style

```css
    .item {
        display: inline-block;
        width: 40px;
        height: 40px;
        margin-right: 10px;
        background-color: blue;
    }
    .item:last-of-type {
        background-color: red;
    }
```

**A.** Four blue squares in the line.

**Explanation** `:last-of-type` is applying to the elements and not to the classes.
Basically `.item:last-of-type` is saying: find elements that have class `.item`
and are last of the type among siblings

[Example of .item:last-of-type](http://codepen.io/artemdemo/pen/LpWXvp)

---

**Q.** You have rows in the page. Each row has number of items with the same classes.
Amount of items differ from row to row.
Without adding new classes change color of elements, when there are exactly five in the row.

```html
<div class="row">
    <div class="item"></div>
    <div class="item"></div>
</div>
<div class="row">
    <div class="item"></div>
    <div class="item"></div>
    <div class="item"></div>
    <div class="item"></div>
    <div class="item"></div>
</div>
<div class="row">
    <div class="item"></div>
    <div class="item"></div>
    <div class="item"></div>
</div>
```

```css
    .item {
        display: inline-block;
        width: 40px;
        height: 40px;
        margin-right: 10px;
        background-color: blue;
    }
```

**A.** You need to use combination of `:nth-child` and `:nth-last-child`

```css
    .item:nth-child(1):nth-last-child(5),
    .item:nth-child(1):nth-last-child(5) ~ .item {
        background-color: red;
    }
```

**Explanation** `:nth-last-child` is counting backwards, therefore the code 
`.item:nth-child(1):nth-last-child(5)` is saying: find elements that have class `.item` are first among siblings and fifth from the end

[Example of .item:nth-child(1):nth-last-child(5](http://codepen.io/artemdemo/pen/BoWGeJ)

