# Set Session Cookie for Popup

Create a popup message using session cookies to remeber if user has closed the popup. Session lasts for 2 days.

## jQuery

```

// Set cookie for popup
function sessionCookie(exdays) {
    var date = new Date();
    date.setTime(date.getTime() + (exdays*2*60*60*1000));
    document.cookie = "popupClosed=yes;expires="+ date.toGMTString() + ';path=/;';
    // console.log("cookie set");
}
    
// Pop up message on page load
$(document).on('ready', function() {
    if(document.cookie.indexOf('popupClosed') < 0 ) {
        if($('body').hasClass('home')) {
            setTimeout(function() {
                $('#cover-message').addClass('display-pop');
            }, 1000);
        }
        // console.log("no cookie");
    }
    // Message close
    $('.close').on('click', function() {
        $('#cover-message').removeClass('display-pop');
        sessionCookie(1);
    });
});

```

## HTML/PHP using ACF fields

```

<?php $enablePop = get_field('show_pop_up_message', 'option'); ?>

<?php if( $enablePop ): ?>
    <div id="cover-message">
        <div class="message-inner">
            <div class="message">
                <div class="message-body">
                    <div class="close">Close X</div>
                    <?php the_field('message_text', 'option'); ?>
                </div>
            </div>
        </div>
    </div>
<?php endif; ?>

```

## CSS

```

/* Pop up message */
#cover-message {
     transition: all 0.5s ease-in-out;
     visibility: hidden;
     opacity: 0;
     display: none;
     position: absolute;
     top: 0;
     left: 0;
     height: 100vh;
     width: 100%;
     z-index: 9999;
     color: #fff;
}
 #cover-message.display-pop {
     visibility: visible;
     opacity: 1;
     display: flex;
}
 #cover-message .message-inner {
     position: absolute;
     top: 0;
     bottom: 0;
     left: 0;
     right: 0;
     background-color: transparent;
}
#cover-message .message-inner .message {
    padding-top: 130px;
    min-width: 360px;
    width: 50%;
    margin: 0 auto;
}
#cover-message .message-inner .message .message-body {
    padding: 40px;
    background-color: rgba(112, 125, 132, 1);
    border-radius: 10px;
    border: 1px solid #ff0000;
    box-shadow: 1px 0px 40px #2f3437;
    position: relative;
}
#cover-message .message-inner .message .message-body p {
    color:  #ffffff;
}
#cover-message .message-inner .message .message-body h2 {
    color:  #ffffff;
}
#cover-message .message-inner .message .message-body a {
    color: #163550;
}
#cover-message .message-inner .message .message-body a:hover {
    color: #800000;
    text-decoration: underline;
}
 #cover-message .close {
    cursor: pointer;
    position: absolute;
    right: 5px;
    top:  5px;
    font-weight: 300;
    font-size: 2rem;
    color: #fff;
    opacity: 1;
    padding: 5px 4px;
    border-radius: 2px;
    transition: all 0.3s ease-in-out;
}
#cover-message .close:hover {
    box-shadow: 1px 0px 5px #2f3437;
}

```