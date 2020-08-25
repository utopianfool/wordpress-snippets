# Change Default Search Page Slug URL

Add to functions file to change the default slug of the search results in the URL

```
<?php

/**
 * Change default search page slug URL
 */
function wpb_change_search_url() {
    if ( is_search() && ! empty( $_GET['s'] ) ) {
        wp_redirect( home_url( "/search/" ) . urlencode( get_query_var( 's' ) ) );
        exit();
    }   
}
add_action( 'template_redirect', 'wpb_change_search_url' );

?>
```