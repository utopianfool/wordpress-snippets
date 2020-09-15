# Register Guttenburg Editor for Custom Post Types

If your custom post doesn't show the guttenburg editor then use this function in functins.php to register your custom post type.

```

/*
 * Register WordPress Gutenberg Custom Post
 */
add_action( 'init', 'cw_post_type' );

function cw_post_type() {
    register_post_type( 'projects',
        // WordPress CPT Options Start
        array(
            'labels' => array(
                'name' => __( 'Projects' ),
                'singular_name' => __( 'Project' )
            ),
            'has_archive' => true,
            'public' => true,
            'rewrite' => array('slug' => 'projects'),
            'show_in_rest' => true,
            'supports' => array('editor')
        )
    );
}

```