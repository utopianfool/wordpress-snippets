# Custom Post Taxonomy

Add to functions.php to enable custom post type taxonomy. Use with [Custom Post Types](functions/custom-post-types.md)


```
// Create Custom Post taxonomy
add_action( 'init', 'create_custom_post_taxonomy' );

function create_custom_post_taxonomy() {
    register_taxonomy(
        'custom_taxonomy',
        'custom-post',
        array(
            'show_ui' => true,
            'show_in_quick_edit' => true,
            'show_admin_column' => true,
            'label' => __( 'Custom Taxonomy' ),
            'rewrite' => array( 'slug' => 'custom-taxonomy' ),
            'hierarchical' => true,
        )
    );
}
```