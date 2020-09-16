# Defer scripts

Use thes efunctions to defer Javascript files to speed up load time. Add to functions.php.

Note: Careful of what you defer, some scripts may be required to load site.

## Global defer scripts

```

/**
 * Defer scripts
 */
// function defer_parsing_of_js ( $url ) {
//     if ( FALSE === strpos( $url, '.js' ) ) return $url;
//     if ( strpos( $url, 'jquery.js' ) ) return $url;
//     return "$url' defer ";
// }
// add_filter( 'clean_url', 'defer_parsing_of_js', 11, 1 );

```

## Defer individual scripts

```

/**
 * Defer individual scripts
 */
function choose_defer_scripts( $tag, $handle, $src ) {

    // The handles of the enqueued scripts we want to defer
    $defer_scripts = array( 
        'cffscripts',
        'devicepx',
        'cookie-consent',
        'hui_scripts',
        'hustle_front',
        'hustle_front_fitie',
        'modernizr_js',
        'unveil_js',
        'magnific_js',
        'bootstrap_js',
        'owl_js',
        'site_js',
        'jquerycookie',
        'locationcookie_js',
        'menu_js',
        'navpipes_js',
        'menuscrollheight_js',
        'mapplic_js',
        'map_js',
        'addthis',
        'hoverIntent',
        'megamenu',
    );

    if ( in_array( $handle, $defer_scripts ) ) {
        return '<script src="' . $src . '" defer="defer" type="text/javascript"></script>' . "\n";
    }
    
    return $tag;
}

add_filter( 'script_loader_tag', 'choose_defer_scripts', 10, 3 );

```