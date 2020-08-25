# Search

## search.php
Save this snippet as search.php in the theme's main directory. Include get_header and get_footer parts.

```
<?php
// Get user search terms
$term = $_GET['s'];

// Setup the terms for use in the WP database query
$terms = explode(' ', $term);

$searchTerms = array();
$termsReadable = '';

foreach($terms as $term)
{
    $searchTerms[] = "`meta_value` LIKE '%{$term}%'";
    $termsReadable .= $term.' ';
}

$searchTerms[] = "`post_content` LIKE '%{$term}%'";

// Setup WP search query 
$query = "SELECT wp_posts.* FROM wp_postmeta LEFT JOIN wp_posts ON wp_postmeta.post_id = wp_posts.ID WHERE (".implode(' OR ', $searchTerms).") AND `post_status` = 'publish' AND `post_type` IN ('page', 'post') GROUP BY post_id";

// Setup pagination
$total = $wpdb->get_var("SELECT COUNT(1) FROM (${query}) AS combined_table");
$items_per_page = 10;
$page = isset($_GET['cpage']) ? abs((int) $_GET['cpage']) : 1;
$offset = ($page * $items_per_page) - $items_per_page;

// Save the search results for output
$searchPosts = array();
$searchPosts = $wpdb->get_results($query . " ORDER BY post_date LIMIT ${offset}, ${items_per_page}");
?>

<div class="container">
    <div class="row">
        <div class="col-xs-12">
            <?php get_template_part('/template-parts/breadcrumbs'); ?>
        </div>
    </div>
    <div class="row">
        <div class="col-xs-12 col-sm-9">
            <div class="page-content">

                <h1>Search</h1>
                <p><strong>Results for:</strong> <?php echo $termsReadable; ?></p>
                <hr>
                <?php if ($searchPosts): ?>

                    <?php foreach($searchPosts as $post): setup_postdata($post); ?>
                    
                        <?php
                        // Fields
                        if (get_field('featured_description'))
                        {
                            $featuredDescription = get_field('featured_description');
                        }
                        else
                        {
                            $featuredDescription = '';
                        }
                        ?>

                        <div id="post-<?php the_ID(); ?>" <?php post_class('news-article'); ?>>
                            <h2><?php echo get_the_title(); ?></h2>
                            <?php if ($featuredDescription): ?>
                                <p><?php echo $featuredDescription; ?></p>
                            <?php endif; ?>
                            <p><strong><a href="<?php echo get_permalink($post->ID); ?>" target="_self">Read More</a></strong></p>
                        </div>
                        <hr>

                    <?php endforeach; ?>

                    <div class="pagination-links text-center">
                        <?php
                        echo paginate_links( array(
                            'base' => add_query_arg('cpage', '%#%'),
                            'prev_text' => __('&laquo; Previous'),
                            'next_text' => __('Next &raquo;'),
                            'total' => ceil($total / $items_per_page),
                            'current' => max(1, get_query_var('cpage'))
                        ));
                        ?>
                    </div>

                <?php else: ?>

                    <p>Sorry, no results found...</p>
                    <h3><a href="<?php echo site_url(); ?>" target="_self">Return to home</a></h3>

                <?php endif; ?> 

            </div>
        </div>
        <div class="col-xs-12 col-sm-3">
            <div class="page-sidebar">
                <?php get_template_part('/template-parts/sidebar-blog'); ?>
            </div>
        </div>
    </div>
</div>
```