# Twitter Cards

To display twitter cards from featured images in wordpress sites, as of Feb 2019

## Add to header of site

```
<head>

<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@EvolveDigitalUK">
<meta name="twitter:creator" content="@EvolveDigitalUK">
<meta name="twitter:title" content="<?php echo get_the_title($post->ID); ?>" />
<meta name="twitter:description" content="<?php echo get_the_excerpt($post->ID); ?>" />
<meta name="twitter:image" content="<?php echo $metaImage; ?>" />

</head>
```