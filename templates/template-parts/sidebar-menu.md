# Sidebar Menu

## sidebar-menu.php

Using [dynamic_page_menu.php](templates/walkers/dynamic-page-menu.md)

Save this snippet as sidebar-menu.php in the theme's template-parts directory.

```
<?php
// Get current page id
$currentPageId = get_the_ID();

// Get uppermost parent of current page
$parent = array_reverse(get_post_ancestors($post->ID));
$parentPage = get_page($parent[0]);
$parentPageId = $parentPage->ID;
$parentPageName = $parentPage->post_title;

// Get subpages of the current page
$args = array(
    'child_of'    => $parentPageId,
    'depth'       => 0,
    'post_type'   => 'page',
    'post_status' => 'publish',
    'sort_column' => 'menu_order, post_title',
    'sort_order'  => 'ASC',
    'title_li'    => null,
    'walker'      => new dynamic_page_menu()
);
?>

<div id="sidebar-menu-wrapper">
    <div id="sidebarMenu" class="sidebar-menu">
        <ul>
            <?php wp_list_pages($args); ?> 
        </ul>
    </div>
</div>

<script>
jQuery(function(){
    // Sidebar menu glyphicon rotate
    jQuery('.sidebar-menu .glyphicon').click(function() {
        var parentLi = jQuery(this).closest('.has-children');
        if(parentLi.hasClass('animate-glyphicon') && ! parentLi.hasClass('active')) {
            parentLi.removeClass('animate-glyphicon');
        } else {
            parentLi.addClass('animate-glyphicon');
        }
    })
})
</script>
```