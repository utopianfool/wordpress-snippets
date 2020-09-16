# Selective Loading of Plugins

Add to functions.php to load plugin on certain page and also dequeue scripts and styles on certain page.

## Only load plugin on certain page

```

/**
 * Only load plugin on certain page
 */
// function my_conditional_fancybox() {
//     if ( is_home() || is_front_page() ) {
//         if ( class_exists('easyFancyBox') )
//             easyFancyBox::$add_scripts = false;
//     }
// }
// add_action( 'wp_enqueue_scripts', 'my_conditional_fancybox', 0 );

```

## Dequeue scripts except on a certain page

```

/**
 * Dequeue scripts except on a certain page
 */
// add_action( 'wp_enqueue_scripts', 'speed_script_dequeue', 11 );
// function speed_script_dequeue() {
//     if ( ! is_page('123' ) ) {
//         wp_dequeue_style( 'sb_instagram_styles' );
//         wp_dequeue_script( 'sb_instagram_scripts' );
//         wp_dequeue_style('sb-font-awesome');
//     }
// }

```