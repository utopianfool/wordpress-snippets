# Advanced Custom Fields Options

Insert into functions.php to add custom ACF options page and sub menu items

```
/**
 * ACF PRO Options Page Menu
 */
if (function_exists('acf_add_options_page'))
{
    acf_add_options_page(array(
        'page_title'    => 'Site Options',
        'menu_title'    => 'Site Options',
        'menu_slug'     => 'site-options',
        'capability'    => 'edit_posts',
        'parent_slug'   => '',
        'position'      => false,
        'icon_url'      => false,
    ));

    // Add Sub Menu Items
    acf_add_options_sub_page(array(
        'page_title'    => 'Contact Info',
        'menu_title'    => 'Contact Info',
        'menu_slug'     => 'contact-info',
        'capability'    => 'edit_posts',
        'parent_slug'   => 'site-options',
        'position'      => false,
        'icon_url'      => false,
    ));
    acf_add_options_sub_page(array(
        'page_title'    => __('Scripts', 'wpbase'),
        'menu_title'    => __('Scripts', 'wpbase'),
        'menu_slug'     => 'scripts',
        'capability'    => 'edit_posts',
        'parent_slug'   => 'site-options',
        'position'      => false,
        'icon_url'      => false,
    ));
    acf_add_options_sub_page(array(
        'page_title'    => 'Social Media',
        'menu_title'    => 'Social Media',
        'menu_slug'     => 'social-media',
        'capability'    => 'edit_posts',
        'parent_slug'   => 'site-options',
        'position'      => false,
        'icon_url'      => false,
    ));
}
```