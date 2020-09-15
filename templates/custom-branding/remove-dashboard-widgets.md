# Remove Dashboard Widgets

Custom branding of the dashboard widgets.

Create a custom-branding.php file inside an appropriate folder like functions and include it in functions.php

```

/**
 * Include custom branding functions
 */
require_once( __DIR__ . '/functions/custom-branding.php');


```

Add the following to remove the default WordPress and other plugin dashboard widgets

## custom-branding.php

```

/**
 * Removing other dashboard widgets
 */
function remove_dashboard_meta() {

    remove_meta_box( 'dashboard_incoming_links', 'dashboard', 'normal' );
    remove_meta_box( 'dashboard_plugins', 'dashboard', 'normal' );
    remove_meta_box( 'dashboard_primary', 'dashboard', 'side' );
    remove_meta_box( 'dashboard_secondary', 'dashboard', 'normal' );
    remove_meta_box( 'dashboard_quick_press', 'dashboard', 'side' );
    remove_meta_box( 'dashboard_recent_drafts', 'dashboard', 'side' );
    remove_meta_box( 'dashboard_recent_comments', 'dashboard', 'normal' );
    remove_meta_box( 'dashboard_right_now', 'dashboard', 'normal' );
    remove_meta_box( 'dashboard_activity', 'dashboard', 'normal' );//since 3.8

    remove_meta_box( 'simple_history_dashboard_widget', 'dashboard', 'normal' ); // Simple history
    remove_meta_box( 'wpseo-dashboard-overview', 'dashboard', 'normal' ); // Yoast
}
add_action( 'admin_init', 'remove_dashboard_meta' );

```