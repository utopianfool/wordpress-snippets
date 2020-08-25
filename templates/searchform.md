# Search Form

## searchform.php
Save this snippet as searchform.php in the theme's main directory.

```
<?php
/**
 * The template for displaying the search form
 * 
 * @package WordPress
 * @subpackage WP_Base
 * @since WP Base 1.0
 */
?>

<form role="search" method="get" class="form form-inline search-form" action="<?php echo esc_url(home_url('/')); ?>">
    <label for="form-search-input" class="sr-only"><?php _ex('Search for', 'label', 'bootstrap-basic'); ?></label>
    <input type="search" id="form-search-input" class="form-control" placeholder="Search..." value="<?php echo esc_attr(get_search_query()); ?>" name="s" title="Search for:">
    <button type="submit" class="btn btn-default">
        <span class="glyphicon glyphicon-search" aria-hidden="true"></span>
    </button>
</form>
```