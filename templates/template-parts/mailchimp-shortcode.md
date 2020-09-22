# Mailchimp Shortcode

Add this to functions.php

```

/**
 * Add custom shortcode
 */
function mailchimp_shortcode() {
    ob_start();
    require_once( __DIR__ . '/inc/shortcode-mailchimp.html');
    $output = ob_get_clean();
    return $output;
}

add_shortcode('mailchimp', 'mailchimp_shortcode');

```

Add the file shortcode-mailchimp.html. Replace the form action="" with mailchimp list url.

```

<div class="post-signup-form">
    <h2>Find this article useful?</h2>
    <p>Get regular web design and development news updates, tips and resources delivered straight to your inbox</p>
    <form action="https://website.list-manage.com/subscribe/post?u=0cf2abe664672cb1aeabc9912&amp;id=b70ac4dc96" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
        <div id="mc_embed_signup_scroll">
            <input type="email" value="" name="EMAIL" class="email" id="mce-EMAIL" placeholder="Email address" required>
            <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_0cf2abe664672cb1aeabc9912_b70ac4dc96" tabindex="-1" value=""></div>
            <div class="">
                <input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button">
            </div>
        </div>
    </form>
</div>

```
