# Simulate Browser Back Button

Add to theme.js or main.js in *core/assets/js* to simulate the browser back button.

```
(function($) {

// Simulate browser back button

     $(document).ready(function(){
        $('a.back-button').click(function(){
            parent.history.back();
            return false;
        });
    });

})(jQuery);
```


## Simulate Back Button and Redirect on Direct Link

This version of the browser back button redirects the user to the home page if the user navigates to a direct link on the site and not from an internal page.

```
function backButton() {
        var historyBack = document.referrer;

        if (!document.referrer) {
            var historyBack = '/';
        }

        $('a.back-button').attr("href", historyBack);
     }
backButton();
```