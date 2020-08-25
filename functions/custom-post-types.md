# Custom Post Types

Add to functions.php to generate custom post types. Use with [Custom Post Taxonomy](functions/custom-post-taxonomy.md)

- [Custom Post Type Setup](#custom-post-type-setup)
- [Placeholder Titles](#placeholder-titles)

## Custom Post Type Setup
```
/*
 * Setup Custom Post Types
 */
function custom_post_types()
{
    register_post_type('portal',
        array(
            'labels' => array(
                'name'               => 'Portals',
                'singular_name'      => 'Portal',
                'add_new'            => 'Add New',
                'add_new_item'       => 'Add New Portal',
                'edit_item'          => 'Edit Portal',
                'new_item'           => 'New Portal',
                'all_items'          => 'All Portals',
                'view_item'          => 'View Portal',
                'search_items'       => 'Search Portals',
                'not_found'          => 'No Portals Found',
                'not_found_in_trash' => 'No Portals found in Trash',
                'parent_item_colon'  => '',
                'menu_name'          => 'Portals',
            ),
            'menu_icon'          => 'dashicons-screenoptions',
            'public'             => true,  
            'publicly_queryable' => true,
            'show_ui'            => true,
            'show_in_menu'       => true,
            'has_archive'        => false,
            'rewrite'            => array(
                'slug'       => 'portal',
                'with_front' => false
            ),
            'supports' => array(
                'title',
                'editor',
                'thumbnail',
                'page-attributes',
                'revisions'
            ),
            'capability_type' => 'post',
            'hierarchical'    => true,
        )
    );
}
add_action('init', 'custom_post_types');
```

## Placeholder Titles
```
/*
 * Setup Custom Post Type Placeholder Titles
 */
function post_type_change_default_title($title)
{
    $screen = get_current_screen();

    if ('portal' == $screen->post_type)
    {
        $title = __('Enter portal name here', 'wpbase');
    }
    return $title;
}
add_filter('enter_title_here', 'post_type_change_default_title');
```