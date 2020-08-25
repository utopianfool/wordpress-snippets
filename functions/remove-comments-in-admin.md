# Remove Comments in Admin

```
/**
 * Get rid of comments in wp_admin
 */
function remove_menus()
{
    // remove_menu_page('edit.php');          // Default Posts
    remove_menu_page('edit-comments.php'); // Comments
}
add_action('admin_menu', 'remove_menus');
```