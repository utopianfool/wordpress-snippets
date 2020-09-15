# Move Excerpt Box to Top of Page

Add to functions.php to remove the default excert box, create a new position and add it back in to the new position.

```

/**
 * Removes the regular excerpt box. We're not getting rid
 * of it, we're just moving it above the wysiwyg editor
 *
 * @return null
 */
function removeExcerptBox( $post_type ) {
    if ( in_array( $post_type, array( 'post', 'page', 'news' ) ) ) {
        remove_meta_box( 
            'postexcerpt', 
            'post', 
            'normal' 
        );
    }
}
add_action( 'admin_menu' , 'removeExcerptBox' );
 
/**
 * Add the excerpt meta box back in with a custom screen location
 *
 * @param  string $post_type
 * @return null
 */
function addExcerptBox( $post_type ) {
    if ( in_array( $post_type, array( 'post', 'page', 'news' ) ) ) {
        add_meta_box(
            'postexcerpt',
            __( 'Excerpt' ),
            'post_excerpt_meta_box',
            $post_type,
            'after_title',
            'high'
        );
    }
}
add_action( 'add_meta_boxes', 'addExcerptBox' );
 
/**
 * You can't actually add meta boxes after the title by default in WP so
 * we're being cheeky. We've registered our own meta box position
 * `after_title` onto which we've registered our new meta boxes and
 * are now calling them in the `edit_form_after_title` hook which is run
 * after the post tile box is displayed.
 *
 * @return null
 */
function exceprtTop() {
    global $post, $wp_meta_boxes;
    # Output the `below_title` meta boxes:
    do_meta_boxes( get_current_screen(), 'after_title', $post );
}
add_action( 'edit_form_after_title', 'exceprtTop' );

```