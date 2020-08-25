# Disable Active Links When Screen Resized

Add this to the the theme's javascript file to disable active links when the screen is resized.

```
$(function(){
    // disable active links when screen resized
    $(window).resize(function() {
        if ($(this).width() > 990) {
            $('.your-menu-class').attr('style', '');
        }
    })
});
```