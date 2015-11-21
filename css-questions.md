# CSS questions

**Q.** You have two `<div>` elements side by side in the row.

```html
<div class="row">
    <div class="item"></div>
    <div class="item"></div>
</div>
```

The right one has fixed width of 200px, the left one should take all the rest.

**A.** There is two options.

The first one:

```css
.row {
    position: relative;
}
.left {
    margin-right: 200px;
    background-color: blue;
    height: 50px;
}
.right {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    width: 200px;
    background-color: red;
}
```

The second:

```css
.row {
    display: table;
    width:100%;
}
.left {
    display: table-cell;
    background-color: blue;
    height: 50px;
}
.right {
    display: table-cell;
    width: 200px;
    background-color: red;
}
```
[Example of 2 divs side by side](http://codepen.io/artemdemo/pen/vNxvYx)


## Pseudo classes


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

Describe what you will see on the screen after applying following style

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

[Example of .item:nth-child(1):nth-last-child(5)](http://codepen.io/artemdemo/pen/BoWGeJ)


## Aligning elements

**Q.** You have following html code. Please align text horizontally in the center and vertically in the middle.
You have also `item-base` style, that shouldn't be changed.

```html
<div class="item-base item">
    Some awesome text
</div>
```

```css
.item-base {
    width: 100%;
    height: 100px;
}
```

**A.** There is more than one option

In the question we see only one line, therefore one of solutions can be the following one:

```css
.item {
    text-align: center;
    line-height: 100px;
}
```

It's sort of ok, but it has problems, it's like to write:

```css
.item {
    box-sizing: border-box;
    -moz-box-sizing: border-box;
    -webkit-box-sizing: border-box;
    text-align: center;
    padding: 40px;
}
```

Both of this solutions have it's own problems

More creative way of thinking:

```css
body {
    display: table;
    width: 100%;
}

.item {
    text-align: center;
    display: table-cell;
    vertical-align: middle;
}
```

---


**Q.** You have following html code. Please align *element* `item-inner` horizontally in the center
and vertically in the middle.
You have also `item-base` style, that shouldn't be changed.

```html
<div class="item-base item">
    <div class="item-inner">Some awesome text</div>
</div>
```

```css
.item-base {
    width: 100%;
    height: 100px;
}
```

**A.**


---

**Q.** You need to add footer stocked to the bottom of the page.
It should work also in mobile. What is your solution and what problems you may face.

**A.** There is no problems nowadays. You can simple use `position: fixed`. 
The only problem can appear if you're aiming really old smartphones: Android 2.1 and below or iOS 4 and below.
For this devices you will need to use JS plugins like [iScroll](https://github.com/cubiq/iscroll),
case they not support position: fixed and footer will scroll along with the page.