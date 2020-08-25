# Remove Post from Admin Menu

Add to functions file to remove the default "post" menu item in the WP admin menu

```
<?php

/**
 * Removes post menu in admin
 */
function remove_post_menu () {
   remove_menu_page('edit.php');
} 
add_action('admin_menu', 'remove_post_menu');

?>
```