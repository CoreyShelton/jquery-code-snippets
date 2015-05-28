# Zebra Striped Unordered List

With this snippet you can easily create zebra striped unordered lists.
This places the background you define on every odd list item 
so that you can place the default one for the even ones in your CSS file. 
You can add this snippet to any type of markup, from tables to plain divs, anything you want to be zebra stripped.

# Example

### jQuery
```javascript
$('.stripe li:odd').css('background', '#E8E8E8’);
```

### HTML
```html
<ul class="stripe">
    <li>One</li>
    <li>Two</li>
    <li>Three</li>
    <li>Four</li>
</ul>
```

***

*Ref: http://www.webdesignerdepot.com/2014/01/10-jquery-snippets-every-designer-should-know/*
