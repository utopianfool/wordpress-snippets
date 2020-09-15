# Footer in Admin Panel

Custom branding of the footer in admin panel.

Create a custom-branding.php file inside an appropriate folder like functions and include it in functions.php

```

/**
 * Include custom branding functions
 */
require_once( __DIR__ . '/functions/custom-branding.php');


```

Add the following to replace the default WordPress footer in admin panel

## custom-branding.php

```

/**
 * Change footer in admin panel
 */
function remove_footer_admin () {
 
echo '<a href="https://example.com" target="_blank">Example Site</a> | Built with <a href="https://wordpress.org/" target="_blank">WordPress</a></p>';
 
}
 
add_filter('admin_footer_text', 'remove_footer_admin');

```