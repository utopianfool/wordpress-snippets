#Social Share and Bookmark Page

Add this into single.php to show icons to share to various social media and email, plus include a bookmark option. Style as appropriate.

These icons are referenced from [Fontawesome 4.7.0](https://fontawesome.com/v4.7.0/icons/)

```

<?php
    $shareTitle = str_replace(array('&#038;', '&amp;', '&'), 'and', get_the_title());
    $shareDescription = 'Check out the latest content';
    $shareUrl = urlencode(get_permalink());
    $shareEmailSubject = str_replace(' ', '%20', 'Have you seen this?');
    $shareEmailMessage = str_replace(' ', '%20', $shareDescription.' - '.$shareUrl);
    // https://fontawesome.com/v4.7.0/icons/
?>

<div class="social-share-to">
    <h4>Share to:</h4>
    <a target="_self" title="Email this to a friend" href="mailto:?subject=<?php echo $shareEmailSubject; ?>&body=<?php echo $shareEmailMessage; ?>">
        <i class="fa fa-envelope" aria-hidden="true"></i>
    </a>
    <a target="_blank" title="Share this on Facebook" href="http://www.facebook.com/sharer/sharer.php?u=<?php echo $shareUrl; ?>">
        <i class="fa fa-facebook-square" aria-hidden="true"></i>
    </a>
    <a target="_blank" title="Share this on Twitter" href="https://twitter.com/share?url=<?php echo $shareUrl; ?>&via=utopianfool&text=<?php echo $shareDescription; ?>">
        <i class="fa fa-twitter-square" aria-hidden="true"></i>
    </a>
    <a target="_blank" title="Share this on LinkedIn" href="http://www.linkedin.com/shareArticle?mini=true&url=<?php echo $shareUrl; ?>&title=<?php echo $shareTitle; ?>&summary=<?php echo $shareDescription; ?>">
        <i class="fa fa-linkedin-square" aria-hidden="true"></i>
    </a>
    <a id="bookmark-this" href="#" title="Bookmark this page">
        <i class="fa fa-bookmark" aria-hidden="true"></i> Bookmark this page
    </a>
</div>

```

## Bookmark function

Create a separate file called 'addtohomescreen.js' and enqueue in functions.php

```

jQuery(function ($) {

  $('#bookmark-this').click(function (e) {
    var bookmarkTitle = document.title;
    var bookmarkUrl = window.location.href;

    if ('addToHomescreen' in window && addToHomescreen.isCompatible) {
      // Mobile browsers
      addToHomescreen({ autostart: false, startDelay: 0 }).show(true);
    } else if (/CriOS\//.test(navigator.userAgent)) {
      // Chrome for iOS
      alert('To add to Home Screen, launch this website in Safari, then tap the Share button and select "Add to Home Screen".');
    } else if (window.sidebar && window.sidebar.addPanel) {
      // Firefox <=22
      window.sidebar.addPanel(bookmarkTitle, bookmarkUrl, '');
    } else if ((window.sidebar && /Firefox/i.test(navigator.userAgent) && !Object.fromEntries) || (window.opera && window.print)) {
      // Firefox 23-62 and Opera <=14
      $(this).attr({
        href: bookmarkUrl,
        title: bookmarkTitle,
        rel: 'sidebar'
      }).off(e);
      return true;
    } else if (window.external && ('AddFavorite' in window.external)) {
      // IE Favorites
      window.external.AddFavorite(bookmarkUrl, bookmarkTitle);
    } else {
      // Other browsers (Chrome, Safari, Firefox 63+, Opera 15+)
      alert('Press ' + (/Mac/i.test(navigator.platform) ? 'Cmd' : 'Ctrl') + '+D to bookmark this page.');
    }

    return false;
  });

});

```