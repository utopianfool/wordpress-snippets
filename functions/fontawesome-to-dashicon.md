# Fontawesome to Dashicon

Replace the WordPress dashicons with font awesome icons.

Create a new folder in the themes main directory called something appropriate like functions and add a new file called fontawesome-to-dashicon.php with the following code:

```

<?php
/*
 * Replace dashicons with fontawesome icons
 */

function fontawesome_dashboard() {
   wp_enqueue_style('fontawesome', 'http:////netdna.bootstrapcdn.com/font-awesome/4.5.0/css/font-awesome.css', '', '4.5.0', 'all');
}

add_action('admin_init', 'fontawesome_dashboard');

function fontawesome_icon_dashboard() {
   echo "<style type='text/css' media='screen'>
            // #adminmenu .menu-icon-{menu-slug} div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }

            // /* Dashboard */
            // #adminmenu .menu-icon-dashboard div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }

            // /* Posts */
            // #adminmenu .menu-icon-post div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }

            // /* Media */
            // #adminmenu .menu-icon-media div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }

            // /* Pages */
            // #adminmenu .menu-icon-page div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }

            // /* Comments */
            // #adminmenu .menu-icon-comments div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }

            // /* Appearance */
            // #adminmenu .menu-icon-appearance div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }

            // /* Plugins */
            // #adminmenu .menu-icon-plugins div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }

            // /* Users */
            // #adminmenu .menu-icon-users div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }

            // /* Tools */
            // #adminmenu .menu-icon-tools div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }

            // /* Settings */
            // #adminmenu .menu-icon-settings div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }

            // /* Custom post type icons */
            // #adminmenu .menu-icon-portal div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }

            // /* Overriding other embeded dashicons */
            // #adminmenu .toplevel_page_contact-info div.wp-menu-image:before {
            //     font-family: Fontawesome !important;
            //     content: '\\f03e';
            // }
            // #adminmenu .toplevel_page_contact-info div.wp-menu-image img {
            //     display: none;
            // }
            // #adminmenu .toplevel_page_contact-info div.wp-menu-image {
            //     background: none !important;
            // }
        </style>";
 }
add_action('admin_head', 'fontawesome_icon_dashboard');

?>

```

## Include this file in functions.php

```

/**
 * Include custom fontawsome dashicons
 */
require_once( __DIR__ . '/functions/fontawesome-to-dashicon.php');

```

### Dashicons Mixin for Wordpress Admin

[SCSS mixins](https://gist.github.com/apisandipas/7991046)

### Fontawesome 4.5.0 cheat sheet

[Cheet sheet pdf](http://swwwitch.com/dl/Font-Awesome-Cheetsheet-4.5.0.pdf)