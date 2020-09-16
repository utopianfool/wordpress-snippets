# Check Post Children and Ancestors

```

/**
 * Check if the current post is a child of the specified post
 */
function is_child($post_id)
{
    global $post;

    if(is_page() && ($post->post_parent == $post_id))
    {
       return true;
    }
    else
    {
       return false;
    }
}

```

```

/**
 * Check if the current post is an ancestor of the specified post
 */
function is_ancestor($post_id)
{
    global $wp_query;

    $ancestors = $wp_query->post->ancestors;

    if (in_array($post_id, $ancestors))
    {
        return true;
    }
    else
    {
        return false;
    }
}

```

```

/**
 * Check if the post has a password protected ancestor
 */
function has_protected_parents($post)
{
    foreach (get_post_ancestors($post) as $parent)
    {
        if (post_password_required($parent))
        {
            return true;
        }
    }
    return false;
}

```

```

/**
 * Get the direct ancestor of a post
 */
function get_post_ancestor()
{
    global $post;

    return $post->post_parent;
}

```

```

/**
 * Get the post children
 */
function get_post_children($postId = 0, $postType = 'any')
{
    $args = array(
        'post_parent' => $postId,
        'post_type'   => $postType,
        'numberposts' => -1,
        'post_status' => 'published',
        'orderby'     => 'menu',
        'order'       => 'ASC'
    );
    return get_children($args, ARRAY_A);
}

```