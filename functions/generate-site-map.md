# Generate Site Map

```
/**
 * Generate Sitemap
 */
function generate_sitemap($post_type = 'page', $child_of = 0, $depth = 0, $sort_column = 'menu_order, post_title', $sort_order = 'ASC')
{
    $args = array(
        'child_of'    => $child_of,
        'depth'       => $depth,
        'post_type'   => $post_type,
        'post_status' => 'publish',
        'sort_column' => $sort_column,
        'sort_order'  => $sort_order,
        'title_li'    => null,
        'echo'        => 0,
        'walker'      => new sitemap_walker()
    );

    $output = '<ul class="sitemap">';
        $output .= wp_list_pages($args);
    $output .= '</ul>';

    return $output;
}
```