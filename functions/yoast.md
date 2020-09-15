# Yoast

Insert into functions.php to add filter to Yoast meta prioity and override breadcrumb trail. 

- [Filter Meta Priority](#filter-meta-priority)
- [Override SEO Breadcrumb Trail](#override-seo-breadcrumb-trail)

## Filter Meta Priority

```
/**
 * Filter Yoast Meta Priority
 */
add_filter('wpseo_metabox_prio', function()
{
    return 'low';
}); 
```

## or

```

 /*-------------------------------------
  Move Yoast to the Bottom
---------------------------------------*/
function yoasttobottom() {
    return 'low';
}
add_filter( 'wpseo_metabox_prio', 'yoasttobottom');

```

## Override SEO Breadcrumb Trail

```
/**
 * Override Yoast SEO Breadcrumb Trail
 */
function wpseo_override_yoast_breadcrumb_trail($links)
{
    global $post;

    if (is_singular('post_type_1'))
    {
        $postId = '';
    }
    elseif (is_singular('post_type_2'))
    {
        $postId = '';
    }
    else
    {
        $postId = '';
    }

    if ($postId)
    {
        $breadcrumb[] = array(
            'url' => get_permalink($postId),
            'text' => get_the_title($postId),
        );

        array_splice($links, 1, -2, $breadcrumb);
    }

    return $links;
}
add_filter('wpseo_breadcrumb_links', 'wpseo_override_yoast_breadcrumb_trail');

```