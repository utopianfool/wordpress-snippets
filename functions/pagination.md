# Pagination
Add these snippets to the functions.php file for Bootstrap pagination, custom pagination and previous and next post links.

- [Bootstrap Pagination](#bootstrap-pagination)
- [Custom Pagination](#custom-pagination)
- [Previous Post Link Attributes](#previous-post-link-attributes)
- [Next Post Link Attributes](#next-post-link-attributes)

## Bootstrap Pagination

```
/**
 * Bootstrap pagination
 */
function bootstrap_pagination($pages = '', $range = 4)
{
     $showitems = ($range * 2) + 1;  

     global $paged;

     if(empty($paged)) $paged = 1;

     if($pages == '')
     {
         global $wp_query; 
         $pages = $wp_query->max_num_pages;

         if(!$pages)
         {
             $pages = 1;
         }
     } 

     if(1 != $pages)
     {
        echo '<div class="text-center">'; 
        echo '<nav><ul class="pagination"><li class="disabled hidden-xs"><span><span aria-hidden="true">Page '.$paged.' of '.$pages.'</span></span></li>';

        if($paged > 2 && $paged > $range+1 && $showitems < $pages) echo "<li><a href='".get_pagenum_link(1)."' aria-label='First'>&laquo;<span class='hidden-xs'> First</span></a></li>";

        if($paged > 1 && $showitems < $pages) echo "<li><a href='".get_pagenum_link($paged - 1)."' aria-label='Previous'>&lsaquo;<span class='hidden-xs'> Previous</span></a></li>";

        for ($i=1; $i <= $pages; $i++)
        {
            if (1 != $pages &&( !($i >= $paged+$range+1 || $i <= $paged-$range-1) || $pages <= $showitems ))
            {
                echo ($paged == $i)? "<li class=\"active\"><span>".$i." <span class=\"sr-only\">(current)</span></span></li>":"<li><a href='".get_pagenum_link($i)."'>".$i."</a></li>";
            }
        } 

         if ($paged < $pages && $showitems < $pages) echo "<li><a href=\"".get_pagenum_link($paged + 1)."\"  aria-label='Next'><span class='hidden-xs'>Next </span>&rsaquo;</a></li>";  

         if ($paged < $pages-1 &&  $paged+$range-1 < $pages && $showitems < $pages) echo "<li><a href='".get_pagenum_link($pages)."' aria-label='Last'><span class='hidden-xs'>Last </span>&raquo;</a></li>";

         echo "</ul></nav>";
         echo "</div>";
     }
}
```

## Custom Pagination

```
/**
 * Custom pagination
 */
function paginate_posts($range = 2, $showPreviousLink = true, $showNextLink = true, $previousLinkLabel = 'Previous', $nextLinkLabel = 'Next')
{
    // Setup options
    global $wp_query;
    $max_num_pages = $wp_query->max_num_pages;
    $postsPerPage = $wp_query->query_vars['posts_per_page'];
    $paged = ($wp_query->query_vars['paged'] ? absint($wp_query->query_vars['paged']) : 1);

    // Stop execution if there's only 1 page
    if ($max_num_pages <= 1)
    {
        return;
    }
        
    // Add current page to the array
    if ($paged >= 1)
    {
        $links[] = $paged;
    }

    // Add the pages around the current page to the array
        // Setup previous pages
        if ($paged >= ($range + 1))
        {
            for ($i = 1; $i <= $range; $i++)
            {
                 $links[] = $paged - $i;
            }
        }
        // Setup next pages
        if (($paged + $range) <= $max_num_pages)
        {
            for ($i = 1; $i <= $range; $i++)
            {
                 $links[] = $paged + $i;
            }
        }

    // Calculate start/end/total pages
    $end = $postsPerPage * $paged;
    $start = $end - $postsPerPage + 1;
    $total = $wp_query->found_posts;

    if ($end > $total)
    {
        $end = $total;
    }

    // Start pagination output
    echo '<div class="pagination">'."\n";
    echo '<div class="pull-left">Showing '.$start.' to '.$end.' of '.$total.'</div>'."\n";
    echo '<div class="pull-right">'."\n";

        // Previous link
        if ($showPreviousLink && get_previous_posts_link())
        {
            echo get_previous_posts_link($previousLinkLabel)."\n";
        }

        // Link to first page, plus ellipses if necessary
        if (! in_array(1, $links))
        {
            if ($paged != 1)
            {
                echo '<a href="'.esc_url(get_pagenum_link(1)).'" class="page-numbers">1</a></li>'."\n";
            }
            else
            {
                echo '<span class="page-numbers current">1</span>'."\n";
            }

            if (! in_array(2, $links))
            {
                echo '<span class="page-numbers dots">...</span>'."\n";
            }
        }

        // Link to current page, plus 2 pages in either direction if necessary
        sort($links);
        foreach ((array) $links as $link)
        {
            if ($paged != $link)
            {
                echo '<a href="'.esc_url(get_pagenum_link($link)).'" class="page-numbers">'.$link.'</a></li>'."\n";
            }
            else
            {
                echo '<span class="page-numbers current">'.$link.'</span>'."\n";
            }
        }

        // Link to last page, plus ellipses if necessary
        if (! in_array($max_num_pages, $links))
        {
            if (! in_array($max_num_pages - 1, $links))
            {
                echo '<span class="page-numbers dots">...</span>'."\n";
            }

            if ($paged != $max_num_pages)
            {
                echo '<a href="'.esc_url(get_pagenum_link($max_num_pages)).'" class="page-numbers">'.$max_num_pages.'</a></li>'."\n";
            }
            else
            {
                echo '<span class="page-numbers current">'.$max_num_pages.'</span>'."\n";
            }
        }

        // Next link
        if ($showNextLink && get_next_posts_link())
        {
            echo get_next_posts_link($nextLinkLabel)."\n";
        }

    // End pagination output
    echo '</div>'."\n";
    echo '</div>'."\n";
}
```

## Previous Post Link Attributes

```
/**
 * Previous post link attributes
 */
function previous_posts_link_attributes()
{
    return 'class="previous-post page-numbers page-buttons"';
}
add_filter('previous_posts_link_attributes', 'previous_posts_link_attributes');
```

## Next Post Link Attributes

```
/**
 * Next post link attributes
 */
function next_posts_link_attributes()
{
    return 'class="next-post page-numbers page-buttons"';
}
add_filter('next_posts_link_attributes', 'next_posts_link_attributes');
```