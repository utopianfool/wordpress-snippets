# Admin Bar Logo

Custom branding of the admin bar logo.

Create a custom-branding.php file inside an appropriate folder like functions and include it in functions.php

```

/**
 * Include custom branding functions
 */
require_once( __DIR__ . '/functions/custom-branding.php');


```

Add the following to replace the default WordPress admin bar logo

## custom-branding.php

```

/**
 * Add custom logo to admin bar
 * Original image 428px illustrator file
 */
function wpb_custom_logo() {
    echo '
    <style type="text/css">
        #wpadminbar #wp-admin-bar-wp-logo > .ab-item .ab-icon:before {
            background-image: url(' . get_bloginfo('stylesheet_directory') . '/images/admin-icon.png) !important;
            background-position: 0 0;
            color:rgba(0, 0, 0, 0);
            background-size: contain;
            background-repeat: no-repeat;
        }
        #wpadminbar #wp-admin-bar-wp-logo.hover > .ab-item .ab-icon {
            background-position: 0 0;
            background-size: contain;
            background-repeat: no-repeat;
        }
    </style>
    ';
}
//hook into the administrative header output
add_action('wp_before_admin_bar_render', 'wpb_custom_logo');

```