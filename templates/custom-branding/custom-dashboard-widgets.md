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

## WYSIWYG instructions dashboard widget

```

// Function that outputs the contents of the dashboard widget
function dashboard_widget_function( $post, $callback_args ) {
    echo "Use the below tags inside textareas (i.e. not WYSIWYGS) to format text.";
    echo "<br/>";
    echo "<br/>";
    echo "<br/>";
    echo "<b>Bold Text</b> = <code>" . htmlspecialchars('<b>Bold Text</b>') . "</code>";
    echo "<br/>";
    echo "<br/>";
    echo "<i>Italic Text</i> = <code>" . htmlspecialchars('<i>Italic Text</i>') . "</code>";
    echo "<br/>";
    echo "<br/>";
    echo "<u>Underlined Text</u> = <code>" . htmlspecialchars('<u>Underlined Text</u>') . "</code>";
    echo "<br/>";
    echo "<br/>";
    echo "Super<sup>script</sup> = <code>" . htmlspecialchars('Super<sup>script</sup>') . "</code>";
    echo "<br/>";
    echo "<br/>";
    echo "Sub<sub>script</sub> = <code>" . htmlspecialchars('Sub<sub>script</sub>') . "</code>";
    echo "<br/>";
    echo "<br/>";
    echo '<a href="www.website.com">Link</a> = <code>' . htmlspecialchars('<a href="www.website.com">Link</a>') . "</code>";
    echo "<br/>";
    echo '<b>Add target="_blank" after or before <i>href</i> in order to make the link open in a new tab.</b>';
    echo "<br/>";
    echo "<br/>";
    echo "<br/>";
    echo "<b>The above tags can be used in conjuction with eachother, see example below:</b>";
    echo "<br/>";
    echo "<br/>";
    echo "Several tags <b><i>used <u>in <sup>conjuction</sup></u></i></b> = <code>" . htmlspecialchars('Several tags <b><i>used <u>in <sup>conjuction</sup></u></i></b>') . "</code>";

}

// Function used in the action hook
function add_dashboard_widgets() {
    wp_add_dashboard_widget('dashboard_widget', 'Basic Formatting', 'dashboard_widget_function');
}

// Register the new dashboard widget with the 'wp_dashboard_setup' action
add_action('wp_dashboard_setup', 'add_dashboard_widgets' );

```