# Make Multiple Divs The Same Height

Sometimes you want multiple divs to have the same height no matter what content they have in them. 
The following snippet enables you to set the min-height for multiple elements based upon the min-height of the main target 
div but never smaller. This is great for things such as masonry like layouts.

# Example

### jQuery
```javascript
$('.container').css('min-height', $('.main-container').height());
```

### HTML
```html
<div class="main-container"></div>
<div class="container"></div>
<div class="container"></div>
<div class="container"></div>
```

***

*Ref: http://www.webdesignerdepot.com/2014/01/10-jquery-snippets-every-designer-should-know/*
