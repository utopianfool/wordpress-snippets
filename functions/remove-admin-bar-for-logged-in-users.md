# Remove Admin Bar for Logged in Users

Add to functions file to remove the admin bar from frontent logged in users.

```
<?php

// Remove admin bar for logged in users
add_filter('show_admin_bar', '__return_false');

?>
```