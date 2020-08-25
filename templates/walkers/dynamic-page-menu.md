#Dynamic Page Menu Walker

## dynamic_page_menu.php

Save this snippet as dynamic_page_menu.php in the theme's walker directory.

```
<?php

class dynamic_page_menu extends Walker_Page
{
    private $currentPage;

    public function start_lvl(&$output, $depth = 0, $args = array())
    {
        $indent = str_repeat("\t", $depth);

        // Get children for the current page
        $children = $this->getChildren($this->currentPage);

        // Check if the current page is an ancestor of an active child page OR if the current page has children and is active
        if (is_ancestor($this->currentPage->ID) || $children && $this->currentPage->ID == get_the_ID())
        {
            $classes = 'collapse in active';
        }
        else
        {
            $classes = 'collapse active';
        }

        $output .= $indent;
        $output .= '<ul id="sidebar-menu-'.$this->currentPage->ID.'" class="has-children '.$classes.'">';
    }

    function start_el(&$output, $page, $depth = 0, $args = array(), $current_page = 0)
    {
        $this->currentPage = $page;

        $class = array();

        if ($depth)
        {
            $indent = str_repeat("\t", $depth);
        }
        else
        {
            $indent = '';
        }

        extract($args, EXTR_SKIP);

        // Get children for the current page
        $children = $this->getChildren($page);

        // Add a class if the current page has children
        if ($children)
        {
            $class[] = 'has-children';
        }

        // Add a class if the current page matches the global post
        if ($this->currentPage->ID == get_the_ID())
        {
            $class[] = 'active';
        }

        // Check if the current page is an ancestor of an active child page OR if the current page has children and is active
        if (is_ancestor($this->currentPage->ID) || $children && $this->currentPage->ID == get_the_ID())
        {
            $isActive = true;
        } 
        else
        {
            $isActive = false;
        }

        // List output
        $output .= $indent;
        $output .= '<li class="'.implode(' ', $class).'">';
            $output .= '<a href="' . get_permalink($page->ID) . '" title="' . esc_attr(wp_strip_all_tags(apply_filters('the_title', $page->post_title, $page->ID))) . '">';
                $output .= $link_before . apply_filters( 'the_title', $page->post_title, $page->ID ) . $link_after;

                if ($children)
                {
                    $output .= '<span href="#sidebar-menu-'.$page->ID.'" role="button" data-toggle="collapse" aria-expanded="false" aria-controls="sidebar-menu-'.$page->ID.'">';
                    if ($isActive)
                    {
                        $output .= '<span class="glyphicon glyphicon-triangle-top" aria-hidden="true"></span>';
                    }
                    else
                    {
                        $output .= '<span class="glyphicon glyphicon-triangle-bottom" aria-hidden="true"></span>';
                    }
                    $output .= '</span>';
                }

            $output .= '</a>';
    }

    public function end_el(&$output, $page, $depth = 0, $args = array()) 
    {
        //$output .= '<span class="glyphicon glyphicon-triangle-bottom" aria-hidden="true"></span>';
        $output .= "</li>";
    }

    public function end_lvl(&$output, $depth = 0, $args = array())
    {
        $indent = str_repeat("\t", $depth);

        $output .= $indent;
        $output .= '</ul>';
    }

    protected function getChildren($page)
    {
        $childPages = array(
            'post_parent' => $page->ID,
            'post_type'   => 'page',
            'numberposts' => -1,
            'post_status' => 'published'
        );
        return $children = get_children($childPages);
    }
}
```

Include this code to functions.php.

```
/**
 * Register Custom Sidebar Page Walker
 */
require get_template_directory().'/walkers/dynamic_page_menu.php';
```

Go to [Walkers](functions/walkers.md)