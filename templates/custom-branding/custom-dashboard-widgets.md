# Custom Dashboard Widgets

Custom branding of the dashboard widgets. 

Create a custom-branding.php file inside an appropriate folder like functions and include it in functions.php

```

/**
 * Include custom branding functions
 */
require_once( __DIR__ . '/functions/custom-branding.php');


```

Add the following to replace the default WordPress dashboard widgets

## custom-branding.php

```

/**
 * Add custom Dashboard widgets
 */
add_action('wp_dashboard_setup', 'my_custom_dashboard_widgets');
 
function my_custom_dashboard_widgets() {

    global $wp_meta_boxes;
    wp_add_dashboard_widget('custom_help_widget', 'Theme Support', 'custom_dashboard_help');
    // wp_add_dashboard_widget('custom_guide_widget', 'Theme Guide', 'custom_dashboard_guide');
}
 
function custom_dashboard_help() {

echo '<p>Need help? <br />Tutorial on using the <a href="https://make.wordpress.org/support/user-manual/content/editors/visual-editor/">Visual Editor</a><br /> For more WordPress tutorials visit: <a href="https://www.wpbeginner.com" target="_blank">WPBeginner</a></p>';
}

// function custom_dashboard_guide() {
//     echo '<p>Chain functions in my_custom_dashboard_widgets()</p>';
// }

```