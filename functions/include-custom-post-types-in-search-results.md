# Include Custom Post Types in Search Results

Add to functions.php to enable custom post types to appear in search results. Use with [Custom Post Types](functions/custom-post-types.md)

```

/*
 * Include custom post types in search
 * Add post type name to $query array, use 'post' to include default posts
 */
add_action( 'pre_get_posts', 'custom_post_types_in_search_results' );

function custom_post_types_in_search_results( $query ) {
    if ( $query->is_main_query() && $query->is_search() && ! is_admin() ) {
        $query->set( 'post_type', array( 'post', projects', 'portfolio' ) );
    }
}

```