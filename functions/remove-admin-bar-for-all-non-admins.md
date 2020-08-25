# Remove Admin Bar for all Non Admins

Add to functions.php to remove the admin bar for all users that are not administrators.

```
/**
 * Remove the admin bar for all users that are not administrators
 */
function remove_admin_bar()
{
   global $wp_admin_bar, $current_user;

    if (! current_user_can('administrator') && ! is_admin())
    {
        return show_admin_bar(false);
    }
}
add_action('after_setup_theme', 'remove_admin_bar');
```