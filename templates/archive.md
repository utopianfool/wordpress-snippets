# Archive

## archive.php

Save this snippet as archive.php in the theme's main directory. Include get_header and get_footer parts.

```
<div class="container">
    <div class="row">
        <div class="col-xs-12">
            <?php get_template_part('/template-parts/breadcrumbs'); ?>
        </div>
    </div>
    <div class="row">
        <div class="col-xs-12 col-sm-9">
            <div class="page-content">

                <h1><?php echo get_the_title(); ?></h1>

                <?php if (have_posts()): ?>

                    <?php while(have_posts()): the_post(); ?>
                    
                        <?php
                        // Fields
                        if (get_field('featured_description'))
                        {
                            $featuredDescription = get_field('featured_description');
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

                    <?php endwhile; ?>

                    <?php paginate_posts($range = 2, false, false); ?>

                <?php else: ?>

                    <p>Sorry, no results found...</p>
                    <h3><a href="<?php echo site_url(); ?>" target="_self">Return to home</a></h3>

                <?php endif; ?> 

            </div>
        </div>
        <div class="col-xs-12 col-sm-3">
            <div class="page-sidebar">
                <?php get_template_part('/template-parts/sidebar-menu'); ?>
            </div>
        </div>
    </div>
</div>
```