# Login Page Logo

Custom branding of the login page logo.

Create a custom-branding.php file inside an appropriate folder like functions and include it in functions.php

```

/**
 * Include custom branding functions
 */
require_once( __DIR__ . '/functions/custom-branding.php');


```

Add the following to replace the default WordPress login logo

## custom-branding.php

```

/**
 * Add custom logo to login
 */
function new_login_logo() { ?>
    <style type="text/css">
        #login h1 a, .login h1 a {
            background-image: url(<?php echo get_stylesheet_directory_uri(); ?>/images/login-logo.png);
            height:101px;
            width:250px;
            background-size: 250px 101px;
            background-repeat: no-repeat;
            padding-bottom: 30px;
        }
    </style>
<?php }
add_action( 'login_enqueue_scripts', 'new_login_logo' );

```