# Admin Notices

Custom branding of the admin notices.

Create a custom-branding.php file inside an appropriate folder like functions and include it in functions.php

```

/**
 * Include custom branding functions
 */
require_once( __DIR__ . '/functions/custom-branding.php');


```

Add the following to display new admin notices

## custom-branding.php

### Displays notice with yellow border and button to close notice

```

/**
 * Add other colours by changing notice class
 * notice-error, notice-warning, notice-success, notice-info
 */

function general_admin_notice(){
    global $pagenow;
    if ( $pagenow == 'options-general.php' ) {
         echo '<div class="notice notice-warning is-dismissible">
             <p>This notice appears on the settings page.</p>
         </div>';
    }
}
add_action('admin_notices', 'general_admin_notice');

```

### Adds notice with blue border, close button and only to the role of editor

```

function author_admin_notice(){
    global $pagenow;
    if ( $pagenow == 'index.php' ) {
    $user = wp_get_current_user();
    if ( in_array( 'editor', (array) $user->roles ) ) {
    echo '<div class="notice notice-info is-dismissible">
          <p>Click on <a href="edit.php">Posts</a> to start writing.</p>
         </div>';
    }
}
}
add_action('admin_notices', 'author_admin_notice');

```

### Adds custom html guide page into notices admin panel

```

/**
 * Add WP guide page as warning notice to admin panel
 * 
 * This adds a notice to the dashboard page from an html guide page in /functions
 * 
 */
function general_admin_notice(){
    global $pagenow;
    $guide = file_get_contents(get_template_directory_uri() . '/core/functions/guide.html');
    // $message = '';
    // $messageClasses = '';
    if ( $pagenow == 'index.php' ) {
         echo "<div class='notice notice-success'>
                    $guide
                </div>";
         // // var classes
         // $messageClasses = 'notice notice-success';
         // // message structure
         // $message = "<div class='$messageClasses'>";
         // $message .= '<p>I am talking about a banana.</p>';
         // $message .= '</div>';
         // // output
         // echo $message;
    }
}
add_action('admin_notices', 'general_admin_notice');

```

### Add custom styles to admin

```

/**
 * Add custom styles to admin
 */
add_action('admin_head', 'guide_fonts');

function guide_fonts() {
  echo '<style>
    .guide-wrapper {
        padding: 20px 0;
        font-family: "Helvetica", sans-serif;
        max-width: 600px;
        margin: 0 auto;
    }
    .guide-wrapper h1 {
        text-align: center;
        font-size: 2rem;
    }
    .guide-wrapper p {
        font-size: 14px;
    }
  </style>';
}

```