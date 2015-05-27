# Smooth Anchor Scrolling

Smooth scrolling uses hash anchor links and jQuery to scroll the current page to a specified ID within that page.

To use this feature: 

1. Add a link on your page that links to an ID
2. Then add the .page-scroll class to the link itself

Now when the link is clicked the page will scroll down or up to the html element with that associated ID

# Example

#### HTML
```html
<a class="page-scroll" href="#contact">Contact Me</a>

<div id="contact">
    <!-- Insert contact information here -->
</div>
```

#### jQuery
```javascript
(function($) {
    $('a.page-scroll').bind('click', function(event) {
        var anchor = $(this);
        $('html, body').stop().animate({
            scrollTop: ($(anchor.attr('href')).offset().top - 50)
        }, 1250, 'easeInOutExpo');
        event.preventDefault();
    });
})(jQuery);
```

\*Please note that ```scrollTop: ($(anchor.attr('href')).offset().top - 50)``` means that the top of the page will scroll to 50px above the specifed \*\*html element (\*\*as denoted via the elements ID)
