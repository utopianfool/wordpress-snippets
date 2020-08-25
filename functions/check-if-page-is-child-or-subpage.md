# Check if Page is Child or Subpage

Useful article for simple function [css-tricks](https://css-tricks.com/snippets/wordpress/if-page-is-parent-or-child/)

Add to functions file to check if page is a child or subpage of a child.

```
<?php

/* 
* Function for checking if page is child or subpage
*/
function is_tree( $page_id, $use_slug = false ) {

    if ( $use_slug === true && !is_string( $page_id ) ) {
        return false;
    } else if ( $use_slug !== true && !is_int( $page_id ) ) {
        return false;
    }

    if ( $use_slug === true ) {
        $page_data = get_page_by_path( $page_id );
        if ( null === $page_data ) {
            return false;
        }
        $page_id = $page_data->ID;
    }

    global $post;         // load details about this page
    if( is_page( $page_id ) ) {
        return true;   // we're at the page or at a sub page
    }

    if ($post) {
        $anc = get_post_ancestors( $post->ID );
        foreach ( $anc as $ancestor ) {
            if( is_page() && $ancestor == $page_id ) {
                return true;
            }
        }
    }

    return false;  // we're elsewhere

};

?>
```

## Usage

if page is a child or subpage of tha page id or slug the display a certain navigation:

```
<?php
// Variables for navigation
if ( is_tree( 49, 'schools' ) || isset( $GLOBALS['nav'] ) && $GLOBALS['nav'] == 'school-event' || ( get_post_type( get_the_ID() ) == 'resources') || ( get_post_type( get_the_ID() ) == 'news') || ( get_page( get_the_ID() ) == 'search' ) ) {
    $siteLogoFilename = 'icon_schools.svg';
    $siteTitle = 'Schools';
    $siteNav = 'primary';
    $siteLink = '/schools/';
} elseif ( is_tree( 51, 'volunteer' ) || isset( $GLOBALS['nav'] ) && $GLOBALS['nav'] == 'volunteer-event' ) {
    $siteLogoFilename = 'icon_volunteers.svg';
    $siteTitle = 'Volunteers';
    $siteNav = 'secondary';
    $siteLink = '/volunteer/';
} 

?>
```

Example above used in nav header:

```
<div class="collapse navbar-collapse" id="cisconav">   
    <?php if ( ! is_front_page() || isset( $siteNav ) ) : ?>

        <?php if ( isset( $siteNav ) ) : ?>
            <div class="ml-auto nav-container">
                <?php
                if (has_nav_menu( $siteNav )) {
                    wp_nav_menu(array('theme_location' => $siteNav, 'container' => false));
                }
                ?>
            </div>
        <?php endif; ?>
        
        <div class="search-tool">
            <a href="#searchContainer" class="" data-toggle="collapse" role="button" aria-expanded="false" aria-controls="#searchContainer"><img src="<?php echo get_template_directory_uri(); ?>/images/icons/search-icon.png"/></a>
        </div>
        <div class="profile-access">
            <?php if(!is_user_logged_in()): ?>
                <a href="#" class="wpmem_loginout"><img src="<?php echo get_template_directory_uri(); ?>/images/icons/profile-icon.png"/></a>
            <?php else: ?>
                <a class="btn btn-logout" href="<?php echo get_site_url(); ?>/logout.php">
                    Logout
                </a>
            <?php endif; ?>
        </div>

    <?php endif; ?>
</div>
```