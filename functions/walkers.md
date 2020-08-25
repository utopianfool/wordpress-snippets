# Walkers

Insert into functions.php to enable bootstrap walkers, custom sidebar walker and sitemap walker.

## Bootstrap Deafult Navigation
```
/**
 * Register Bootstrap Default Navigation Walker
 */
require get_template_directory().'/walkers/bootstrap_nav.php';
```
File for [bootstrap_nav.php](templates/walkers/bootstrap-nav.md)

## Bootstrap Hover Navigation
```
/**
 * Register Bootstrap Hover Navigation Walker
 */
require get_template_directory().'/walkers/bootstrap_hover_nav.php';
```
File for [bootstrap_hover_nav.php](templates/walkers/bootstrap-hover-nav.md)

## Dynamic Page Menu Walker
```
/**
 * Register Custom Sidebar Page Walker
 */
require get_template_directory().'/walkers/dynamic_page_menu.php';
```
File for [dynamic_page_menu.php](templates/walkers/dynamic-page-menu.md)

## Site Map
```
/**
 * Register Sitemap Walker
 */
require get_template_directory().'/walkers/sitemap_walker.php';
```
File for [sitemap_walker.php](templates/walkers/sitemap-walker.md)
