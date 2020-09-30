# Redirect Login URL


Add to functions.php to redirect login page.

```

add_filter( 'login_url', 'another_login_url', 10, 2);
function another_login_url( $force_reauth, $redirect ){
    $login_url = 'your_chosen_login_url';

    if ( !empty($redirect) )
        $login_url = add_query_arg( 'redirect_to', urlencode( $redirect ), $login_url );

    if ( $force_reauth )
        $login_url = add_query_arg( 'reauth', '1', $login_url ) ;

    return $login_url ;
}

```

## Redirect action

```

add_action( 'login_redirect', 'mysite_login_redirect');
function mysite_login_redirect(){
    return 'your_url';
}

```