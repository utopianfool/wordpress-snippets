# Add Carets to Submenu

## add-carets-to-submenu.js

Add this function to theme.js or in separate file in *core/assets/js* to add carets to submenu. Uses Bootstrap 4 classes.

```
jQuery(function($) {

    /**
     * Navigation
     */  
    // Add carets to subnav
    $('.menu-item-has-children > a').after('<span class="caret mobile-caret"></span>');
    $('.menu-item-has-children > a').append('<span class="caret"></span>');

    // Mobile Menu toggle functionality 
    $('.menu-toggle').on('click',function(){
        var menuToggle = $(this); 
        if( menuToggle.hasClass('menu-active') ){
            menuToggle.removeClass('menu-active');
            $('.main-navigation').removeClass('menu-toggled');
            $('.sub-menu').removeClass('submenu-toggled');
        } else {
            $('.main-navigation').toggleClass('menu-toggled');
            menuToggle.addClass('menu-active');
        }
    });

    // Mobile Submenu 
    $('.mobile-caret').on('click',function(){
        var submenuToggle = $(this); 
        if( submenuToggle.parent().hasClass('submenu-toggled') ){
            submenuToggle.parent().removeClass('submenu-toggled').children('.sub-menu').slideUp();
        } else {
            submenuToggle.parent().addClass('submenu-toggled').children('.sub-menu').slideDown();
        }
    });


});    
```

## Alternative add carets to submenu with Sidr

```
jQuery(function($) {

    /**
     * Navigation
     */  
    // Add carets to subnav
    $('.menu-item-has-children').append('<span class="caret d-lg-none"><i class="fa fa-chevron-right"></i></span>');
    $('.menu-item-has-children > a').append('<span class="caret d-none d-lg-inline-block"><i class="fa fa-chevron-down"></i></span>');
    $('.sub-menu').prepend('<li class="submenu-close d-lg-none"><span class="caret-close"><i class="fa fa-chevron-left"></i></span> Back</li>');

    // Mobile Menu toggle functionality 
    $('.menu-toggle').on('click',function(){
        var menuToggle = $(this); 
        if( menuToggle.hasClass('menu-active') ){
            menuToggle.removeClass('menu-active');
            $('.main-navigation').removeClass('menu-toggled');
            $('.sub-menu').removeClass('submenu-toggled');
        } else {
            $('.main-navigation').toggleClass('menu-toggled');
            menuToggle.addClass('menu-active');
        }
    });

    // Mobile Submenu 
    $('.caret').on('click',function(){
        $(this).parent().children('.sub-menu').addClass('submenu-toggled');
    });
    $('.submenu-close').on('click',function(){
        $(this).parent().removeClass('submenu-toggled');
    });

});
```