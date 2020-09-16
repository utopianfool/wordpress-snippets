# Flexible Content ACF Example

```

<?php if( have_rows('flexible_content_standard') ): ?>
    <div class="container-fluid">
    <?php $layoutCount = 1; ?>

    <?php while ( have_rows('flexible_content_standard') ) : the_row(); ?>

        <?php if( get_row_layout() == 'text' ): ?>
            <section class="flexible-content text-section my-3">
                <div class="row">
                    <div class="col-12">
                    <?php echo get_sub_field('content'); ?>
                    </div>
                </div>
            </section>

        <?php elseif( get_row_layout() == 'accordions' ): ?> 
            <section class="flexible-content accordions my-3">
                <div class="row">
                    <?php if(have_rows('left')): ?>
                        <?php $counter = 1; ?>
                    <div class="col-12 col-md-6 left-accordions">
                        <?php while(have_rows('left')): the_row(); ?>
                            <?php
                                $title = get_sub_field('title');
                                $content = get_sub_field('content');
                            ?>
                        <div class="accordion-wrapper">
                            <button class="accordion-trigger " type="button" data-toggle="collapse" data-target="#accordionLeft<?php echo $counter; ?>-<?php echo $layoutCount; ?>" aria-expanded="false" aria-controls="accordionLeft<?php echo $counter; ?>-<?php echo $layoutCount; ?>">
                                <?php echo $title; ?>
                            </button>
                            <div class="collapse" id="accordionLeft<?php echo $counter; ?>-<?php echo $layoutCount; ?>">
                                <div class="accordion-content-wrapper">
                                <?php echo $content; ?>
                                <span class="close-expansion" data-target="#accordionLeft<?php echo $counter; ?>-<?php echo $layoutCount; ?>" data-toggle="collapse">close</span>
                                </div>
                            </div>
                        </div>
                            <?php $counter++; ?>
                        <?php endwhile; ?>
                    <?php if(have_rows('right')): ?>
                        <?php $counter = 1; ?>
                        <?php while(have_rows('right')): the_row(); ?>
                            <?php
                                $title = get_sub_field('title');
                                $content = get_sub_field('content');
                            ?>
                        <div class="accordion-wrapper hidden-md hidden-lg">
                            <button class="accordion-trigger " type="button" data-toggle="collapse" data-target="#accordionRight-small-<?php echo $counter; ?>-<?php echo $layoutCount; ?>" aria-expanded="false" aria-controls="accordionRight-small-<?php echo $counter; ?>-<?php echo $layoutCount; ?>">
                                <?php echo $title; ?>
                            </button>
                            <div class="collapse" id="accordionRight-small-<?php echo $counter; ?>-<?php echo $layoutCount; ?>">
                                <div class="accordion-content-wrapper">
                                <?php echo $content; ?>
                                <span class="close-expansion" data-target="#accordionRight-small-<?php echo $counter; ?>-<?php echo $layoutCount; ?>" data-toggle="collapse">close</span>
                                </div>
                            </div>
                        </div>
                            <?php $counter++; ?>
                        <?php endwhile; ?>
                    <?php endif; ?>
                    </div>
                    <?php endif; ?>
                        
                    <?php if(have_rows('right')): ?>
                        <?php $counter = 1; ?>
                    <div class="col-12 col-md-6 right-accordions hidden-xs hidden-sm">
                        <?php while(have_rows('right')): the_row(); ?>
                            <?php
                                $title = get_sub_field('title');
                                $content = get_sub_field('content');
                            ?>
                        <div class="accordion-wrapper">
                            <button class="accordion-trigger " type="button" data-toggle="collapse" data-target="#accordionRight<?php echo $counter; ?>-<?php echo $layoutCount; ?>" aria-expanded="false" aria-controls="accordionRight<?php echo $counter; ?>-<?php echo $layoutCount; ?>">
                                <?php echo $title; ?>
                            </button>
                            <div class="collapse" id="accordionRight<?php echo $counter; ?>-<?php echo $layoutCount; ?>">
                                <div class="accordion-content-wrapper">
                                <?php echo $content; ?>
                                <span class="close-expansion" data-target="#accordionRight<?php echo $counter; ?>-<?php echo $layoutCount; ?>" data-toggle="collapse">close</span>
                                </div>
                            </div>
                        </div>
                            <?php $counter++; ?>
                        <?php endwhile; ?>
                    </div>
                    <?php endif; ?>
                </div>
            </section>
        <?php elseif( get_row_layout() == 'pdf_download' ): ?>
            <?php
                $altTitle = get_sub_field('title');
                $attachment_id = get_sub_field('file');
                $url = wp_get_attachment_url( $attachment_id );
                $title = get_the_title( $attachment_id );
                $filesize = filesize( get_attached_file( $attachment_id ) );
                $filesize = size_format($filesize, 2);  
                $path_info = pathinfo( get_attached_file( $attachment_id ) );
            ?>

            <div class="row">
                <div class="col">
                    <a target="_blank" rel="noreferrer" class="pdf-download-link" type="<?php echo $path_info['extension']; ?>" data-size="<?php echo $filesize; ?>" href="<?php echo $url; ?>">
                        <img class="mr-2 mt-4" src="<?php echo get_template_directory_uri(); ?>/images/pdficon.png"/>
                        <p class="mt-1"><?php if($altTitle): ?>
                                <?php echo $altTitle; ?>
                            <?php else: ?>
                                <?php echo $title; ?>
                            <?php endif; ?>
                        </p>
                    </a>
                </div>
            </div>

        <?php elseif( get_row_layout() == 'sidebar_left' ): ?>
            <?php
                $sidebarLeft = get_sub_field('left_sidebar');
                $contentRight = get_sub_field('content_right');
            ?>
            <div class="row my-5">
                <div class="col-12 col-md-3 order-1 order-md-2">
                    <?php echo $sidebarLeft; ?>
                    <?php get_template_part('/template-parts/tp-widget-sidebar'); ?>
                </div>
                <div class="col-12 col-md-9 order-2 order-md-1">
                    <?php echo $contentRight; ?>
                </div>
            </div>

        <?php elseif( get_row_layout() == 'sidebar_right' ): ?>
            <?php
                $sidebarRight = get_sub_field('right_sidebar');
                $contentLeft = get_sub_field('content_left');
            ?>
            <div class="row my-3">
                <div class="col-12 col-md-9">
                    <?php echo $contentLeft; ?>
                </div>
                <div class="col-12 col-md-3">
                    <?php echo $sidebarRight; ?>
                    <?php get_template_part('/template-parts/tp-widget-sidebar'); ?>
                </div>
            </div>

        <?php elseif( get_row_layout() == 'product_section' ): ?>
            <?php
                $title = get_sub_field('title');
                $description = get_sub_field('description');
                $imageBand = get_sub_field('image_band');

                $brochureTitle = get_sub_field('brochure_title');
                $attachment_id = get_sub_field('brochure');
                $url = wp_get_attachment_url( $attachment_id );
                $fileTitle = get_the_title( $attachment_id );
                $filesize = filesize( get_attached_file( $attachment_id ) );
                $filesize = size_format($filesize, 2);  
                $path_info = pathinfo( get_attached_file( $attachment_id ) );

                $brochureLink = get_sub_field('brochure_link');
            ?>

            <section class="product-section my-3">
                <div class="row">
                    <div class="col">
                        <h2><?php echo $title; ?></h2>
                        <p><?php echo $description; ?></p>
                    </div>
                </div>
                <?php if($imageBand): ?>
                <div class="row">
                    <?php if( have_rows('image_band') ): ?>

                        <?php while( have_rows('image_band') ): the_row(); 

                            $image = get_sub_field('image');
                        ?>

                            <div class="col-3">
                                <img alt="<?php echo $image['title']; ?>" src="<?php echo $image['url']; ?>"/>
                            </div>

                        <?php endwhile; ?>

                    <?php endif; ?>
                </div>
                <?php endif; ?>
                <?php if($attachment_id || $brochureLink): ?>
                    <div class="row">
                        <div class="col">
                            <a class="pdf-download-link mt-3" type="<?php echo $path_info['extension']; ?>" data-size="<?php echo $filesize; ?>" href="<?php echo $url; ?>">
                                <img class="mr-2 mt-4" width="24" src="<?php echo get_template_directory_uri(); ?>/images/pdficon.png"/>
                                <?php if($brochureTitle): ?>
                                    <p class="mt-1"><?php echo $brochureTitle; ?></p>
                                <?php else: ?>
                                    <p class="mt-1"><?php echo $fileTitle; ?></p>
                                <?php endif; ?>
                            </a>
                        </div>
                    </div>
                <?php endif; ?>
            </section>

        <?php elseif( get_row_layout() == 'button_row' ): ?>

            <section class="button-row">
                <div class="row">

                    <?php if( have_rows('button_links') ): ?>

                        <?php while( have_rows('button_links') ): the_row(); 

                            $link = get_sub_field('link');
                            $text = get_sub_field('button_text');
                        ?>

                            <div class="col-12 col-sm-6 col-md-3 col-lg-2">
                                <a class="btn button-link text-uppercase" href="<?php echo $link; ?>" title="<?php echo $link; ?>">
                                    <?php echo $text; ?>
                                </a>
                            </div>

                        <?php endwhile; ?>

                    <?php endif; ?>

                </div>
            </section>

        <?php elseif( get_row_layout() == 'testimonial_bar' ): ?>

            <?php get_template_part('/template-parts/testimonials'); ?>

        <?php elseif( get_row_layout() == 'twitter_bar' ): ?>

            <?php 
                $twitterLink = get_field('twitter_link', 'option');
                $twitterName = get_field('twitter_handle', 'option');
            ?>

            <section class="twitter-bar">
                <div class="row align-items-center">
                    <div class="col-12 col-md-3 align-self-center">
                        <div class="twitter-name text-center">
                            <?php if($twitterLink): ?>
                                <p><a target="_blank" rel="noopener noreferrer" href="<?php echo $twitterLink; ?>"><i class="mr-3 fab fa-twitter fa-lg"></i><?php echo $twitterName; ?></a></p>
                            <?php endif; ?>
                        </div>
                    </div>
                    <div class="col-12 col-md-8 align-self-center">
                        <div class="twitter-text text-center text-md-left">
                            <p><?php echo do_shortcode('[custom-twitter-feeds]'); ?></p>
                        </div>
                    </div>
                    <div class="col-12 col-md-1 d-none d-md-block align-self-center">
                        <div class="twitter-follow text-center">
                            <p><a target="_blank" rel="noopener noreferrer" href="<?php echo $twitterLink; ?>">Follow</a></p>
                        </div>
                    </div>
                </div>
            </section>

        <?php elseif( get_row_layout() == 'promotional_accordions' ): ?>

            <section class="promotional-card-with-title clickthroughs my-3">
                <div class="row justify-content-center">

                    <?php if( have_rows('promotional_card') ): ?>

                        <?php while( have_rows('promotional_card') ): the_row(); 

                            $heading = get_sub_field('heading');
                            $image = get_sub_field('image');
                            $title = get_sub_field('title');
                            $titleColour = get_sub_field('title_bar_colour');
                            $linkText = get_sub_field('link_button_text');
                            $accordionText = get_sub_field('accordion_text');
                          
                            $url = get_sub_field('link');
                            $pageLink = get_sub_field('page_link');
                            $link = '';

                            if($url) {
                                $link = $url;
                            } elseif($pageLink) {
                                $link = $pageLink;
                            }

                        ?>

                            <div class="col-12 col-sm-6 col-md-4 col-lg-3">
                                <div class="promo-heading">
                                    <h3 class="mt-4"><?php echo $heading; ?></h3>
                                </div>
                                <div class="promo-card aspect ratio16-9 open-expansion operation-open" style="background-image: url(<?php echo $image; ?>);">
                                    <div class="promo-title <?php echo $titleColour; ?>">
                                        <h4 class="text-white text-uppercase"><?php echo $title; ?></h4>
                                    </div>
                                </div>
                                <div class="promo-snippet expansion">
                                    <div class="inner-snippet">
                                        <?php if ($accordionText): ?>
                                            <p><?php echo $accordionText; ?></p>
                                        <?php endif; ?>
                                        <?php if (!empty($link)): ?>
                                            <?php if($url): ?>
                                                <a href="<?php echo $link; ?>" target="_blank" rel="noopner noreferrer" class="button-link"><?php echo $linkText; ?></a>
                                            <?php else: ?>
                                                <a href="<?php echo $link; ?>" class="button-link"><?php echo $linkText; ?></a>
                                            <?php endif; ?>
                                        <?php endif; ?>
                                    </div>
                                </div>
                            </div>

                        <?php endwhile; ?>

                    <?php endif; ?>

                </div>
            </section>

            <?php elseif( get_row_layout() == 'clients_slider' ): ?>

            <section class="clients-slider-bar d-none d-md-block">
                <div class="slider-wrapper"></div>
                <div class="row align-items-center">
                    <div class="col-3 align-self-center">
                        <h2><?php the_sub_field('slider_text'); ?></h2>
                    </div>
                    <div class="col-9">
                        <div class="clients-slider">

                            <?php if( have_rows('slider_logos') ): ?>

                                <?php while( have_rows('slider_logos') ): the_row(); 

                                    $image = get_sub_field('image');
                                    $link = get_sub_field('link');
                                ?>

                                    <div class="clients-slide">
                                      
                                            <a href="<?php echo $link; ?>" target="_blank" rel="noopener noreferrer">
                                       
                                                <img class="img-fluid" alt="<?php echo $image['alt']; ?>" title="<?php echo $image['title']; ?>" src="<?php echo $image['url']; ?>"/>
                                       
                                            </a>
                                       
                                    </div>

                                <?php endwhile; ?>

                            <?php endif; ?>

                        </div>
                    </div>
                </div>
            </section>

            <?php elseif( get_row_layout() == 'variable_content_for_mobile' ): ?>

                <section class="standard-content-section">
                    <div class="row">
                        <?php 
                            $mobileOnlyContent = get_sub_field('content_mobile');
                            $content = get_sub_field('content'); 
                        ?>
                        <?php if($mobileOnlyContent): ?>
                            <div class="col-12 d-none d-md-block">
                                <?php echo $content ?>
                            </div>
                            <div class="col-12 d-block d-md-none">
                                <?php echo $mobileOnlyContent; ?>
                            </div>
                        <?php else: ?>
                            <div class="col-12">
                                <?php echo $content ?>
                            </div>
                        <?php endif; ?>
                    </div>
                </section>

        <?php endif; ?>
    <?php $layoutCount++; ?>

    <?php endwhile; ?>
    </div>
<?php endif; ?>

```