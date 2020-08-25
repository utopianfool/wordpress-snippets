#Custom Login Form

Add the functions below to add custom logo and styling to login page

```

/**
 * Add custom logo to login
 */
function evolve_login_logo() { ?>
    <style type="text/css">
        #login h1 a, .login h1 a {
            background-image: url(<?php echo get_stylesheet_directory_uri(); ?>/images/login-logo.png);
        height:65px;
        width:320px;
        background-size: 320px 65px;
        background-repeat: no-repeat;
            padding-bottom: 30px;
        }
        body.login form[id="loginform"] {
            background-image: url(<?php echo get_stylesheet_directory_uri(); ?>/images/home-bg.png);
            background-repeat: no-repeat;
            background-size: cover;
            background-position: center;
        }
        body.login form[id="loginform"] label {
            color: #fff;
        }
    </style>
<?php }
add_action( 'login_enqueue_scripts', 'evolve_login_logo' );

```

```

/**
 * Change link values in login page
 */
function evolve_login_logo_url() {
    return home_url();
}
add_filter( 'login_headerurl', 'evolve_login_logo_url' );

function evolve_login_logo_url_title() {
    return 'Evolve Digital';
}
add_filter( 'login_headertitle', 'evolve_login_logo_url_title' );

```