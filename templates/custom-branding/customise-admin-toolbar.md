# Customise Admin Toolbar

Custom branding of the admin toolbar. 

Create a custom-branding.php file inside an appropriate folder like functions and include it in functions.php

```

/**
 * Include custom branding functions
 */
require_once( __DIR__ . '/functions/custom-branding.php');


```

Add the following to customise the default WordPress admin toolbar

## custom-branding.php

### Add link to toolbar

```

/**
 * add a link to the WP Toolbar
 */
function custom_toolbar_link($wp_admin_bar) {
    $args = array(
        'id' => 'title_of_link',
        'title' => 'Title of Link', 
        'href' => 'https://www.google.com/', 
        'meta' => array(
            'class' => 'title', 
            'title' => 'Search Google'
            )
    );
    $wp_admin_bar->add_node($args);
}
add_action('admin_bar_menu', 'custom_toolbar_link', 999);

```

### Remove links from toolbar

```

/**
 * Remove link to the WP Toolbar
 */
function remove_links_toolbar($wp_admin_bar) 
{
    global $wp_admin_bar;
    $wp_admin_bar->remove_menu('comments');
    $wp_admin_bar->remove_menu('updates');
    $wp_admin_bar->remove_menu('logo');
}

add_action( 'admin_bar_menu', 'remove_links_toolbar', 999 );

```

### Remove toolbar

```

/**
 * Remove WP Toolbar for all users
 */
add_filter('show_admin_bar', '__return_false');

```