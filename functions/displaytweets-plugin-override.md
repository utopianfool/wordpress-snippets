# DisplayTweets Plugin Override

```
/**
 * Override DisplayTweets plugin feed output
 */
function custom_displaytweets_template($tweet)
{
    // Split posted date
    $day = date('j', strtotime($tweet->created_at));
    $month = get_month(date('n', strtotime($tweet->created_at)));
    $year = date('Y', strtotime($tweet->created_at));
    $time = date('g:ia', strtotime($tweet->created_at));
    $ordinalIndicator = get_ordinal_indicator(date('S', strtotime($tweet->created_at)));

    // Format posted date
    $posted_since = $day.$ordinalIndicator.' '.$month.' '.$year.' - '.$time;

    // Format tweet text
    $text = $tweet->text;
    $text = preg_replace("#(^|[\n ])([\w]+?://[\w]+[^ \"\n\r\t< ]*)#", "\\1<a href=\"\\2\" target=\"_blank\">\\2</a>", $text);
    $text = preg_replace("#(^|[\n ])((www|ftp)\.[^ \"\t\n\r< ]*)#", "\\1<a href=\"http://\\2\" target=\"_blank\">\\2</a>", $text);
    $text = preg_replace("/@(\w+)/", "<a href=\"http://www.twitter.com/\\1\" target=\"_blank\">@\\1</a>", $text);
    $text = preg_replace("/#(\w+)/", "<a href=\"http://twitter.com/search?q=%23\\1&src=hash\" target=\"_blank\">#\\1</a>", $text);

    //print_r($tweet->user);

    // Tweet output
    $output = '<div class="tweet tweet-row clearfix">';
        $output .= '<div class="tweet-col-avatar clearfix">';
            $output .= '<img src="'.$tweet->user->profile_image_url.'">';
        $output .= '</div>';
        $output .= '<div class="tweet-col-profile clearfix">';
            $output .= '<p class="twitter-name">'.$tweet->user->name.'</p>';
            $output .= '<p class="twitter-handle">@'.$tweet->user->screen_name.'</p>';
            $output .= '<p class="twitter-tweet">'.$text.'</p>';
            $output .= '<p class="twitter-date"><small>'.$posted_since.'</small></p>';
        $output .= '</div>';
    $output .= '</div>';

    echo $output;
}
add_filter('displaytweets_tweet_template', 'custom_displaytweets_template');
```