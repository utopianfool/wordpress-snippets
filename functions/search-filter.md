# Search Filter


## Search Filter to Only Show Posts
```
/**
 * Default the search filter to show posts only 
 */
function search_filter($query)
{
    if (! is_admin())
    {
        if ($query->is_search) {
            // Only get posts
            $query->set('post_type', 'post');
        }
    }
    return $query;
}
add_filter('pre_get_posts', 'search_filter');
```