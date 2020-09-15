# Child Theme

Create directory in wp-content/themes

In new directory create style.css file with the following:

## style.css

```

/*
Theme Name: Whatever name you want to call your theme
Theme URI: https://example.com
Description: A child theme for whatever parent theme you are using.
Author: Your name
Author URI: https://example.com
Template: name of parent theme folder (lowercase)
Version: 1.0
License: GNU General Public License v2 or later
License URI: https://www.gnu.org/licenses/gpl-2.0.html
*/

```

Create a functions.php file to include the parent theme's stylesheet.

## functions.php

```

<?php
/* 
 * Enqueue scripts and style from parent theme 
 */        
function parent_theme_styles() {
    wp_enqueue_style( 'parent', get_template_directory_uri() . '/style.css' );
}
add_action( 'wp_enqueue_scripts', 'parent_theme_styles');

/*
 * Enqueue scripts and styles whilst inside child theme (optional)
 */
function new_child_scripts() {

    wp_enqueue_script( 'navigation', get_stylesheet_directory_uri() . '/js/navigation.js', array(), false );
}
add_action( 'wp_enqueue_scripts', 'new_child_scripts' );


?>

```