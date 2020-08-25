# Navbar Hides on Scroll

## navbar-hide-scroll.js
Applys classes *navigation-up* and *navigation-down* to navbar.

Add this javascript to the theme.js or main.js file in *core/assets/js* folder.
Add the CSS styling to appropriate div. For example ```<nav class="navbar">```

Uncomment alert("DOWN") and alert("UP") for debugging.

```
jQuery(function($) {

    $(function(){
          //Keep track of last scroll
          var lastScroll = 0;
              $(window).scroll(function(event){
                  //Sets the current scroll position
                  var st = $(this).scrollTop();
                  //Determines up-or-down scrolling
                  if (st > lastScroll){
                     //Replace this with your function call for downward-scrolling
                     //alert("DOWN");
                     $('nav.navbar').removeClass('navigation-down').addClass('navigation-up');
                  }
                  else {
                     //Replace this with your function call for upward-scrolling
                     //alert("UP");
                     $('nav.navbar').removeClass('navigation-up').addClass('navigation-down');
                  }
                  //Updates scroll position
                  lastScroll = st;
          });
    });

});

```

## navbar-hide-scroll.css
Apply this CSS to appropriate file.

```
nav.navbar.navigation-up {
        margin-top:-100px;
        -webkit-transition: all 0.5s ease;
        -moz-transition: all 0.5s ease;
        -ms-transition: all 0.5s ease;
        -o-transition: all 0.5s ease;
        transition:all 0.5s ease!important;
}
nav.navbar.navigation-down {
        margin-top:0px;
        -webkit-transition: all 0.5s ease;
        -moz-transition: all 0.5s ease;
        -ms-transition: all 0.5s ease;
        -o-transition: all 0.5s ease;
        transition:all 0.5s ease!important;
}
```