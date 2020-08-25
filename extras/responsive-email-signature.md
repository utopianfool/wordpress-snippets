# Responsive Email Signature Template

Out of the box this provides 2 columns with image in one and details in the other. The details section has a seperator column with a border.
The template is responsive and is a good guide to use for email signatures.

```
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" xmlns:v="urn:schemas-microsoft-com:vml" xmlns:o="urn:schemas-microsoft-com:office:office">
<head>
    <meta charset="utf-8"> <!-- utf-8 works for most cases -->
    <meta name="viewport" content="width=device-width"> <!-- Forcing initial-scale shouldn't be necessary -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge"> <!-- Use the latest (edge) version of IE rendering engine -->
    <meta name="x-apple-disable-message-reformatting">  <!-- Disable auto-scale in iOS 10 Mail entirely -->
    <title></title> <!-- The title tag shows in email notifications, like Android 4.4. -->

    <!-- Web Font / @font-face : BEGIN -->
    <!-- NOTE: If web fonts are not required, lines 10 - 27 can be safely removed. -->

    <!-- Desktop Outlook chokes on web font references and defaults to Times New Roman, so we force a safe fallback font. -->
    <!--[if mso]>
        <style>
            * {
                font-family: 'Arimo', sans-serif !important;
            }
        </style>
    <![endif]-->

    <!-- All other clients get the webfont reference; some will render the font and others will silently fail to the fallbacks. More on that here: http://stylecampaign.com/blog/2015/02/webfont-support-in-email/ -->
    <!--[if !mso]><!-->
        <!-- <link href="https://fonts.googleapis.com/css?family=Arimo&display=swap" rel="stylesheet">  -->
    <!--<![endif]-->

    <!-- Web Font / @font-face : END -->

    <!-- CSS Reset -->
    <style>
        @import url('https://fonts.googleapis.com/css?family=Arimo&display=swap');
        /* What it does: Remove spaces around the email design added by some email clients. */
        /* Beware: It can remove the padding / margin and add a background color to the compose a reply window. */
        html,
        body {
            font-family: 'Arimo', sans-serif;
            margin: 0 auto !important;
            padding: 0 !important;
            height: 100% !important;
            width: 100% !important;
        }

        /* What it does: Stops email clients resizing small text. */
        * {
            -ms-text-size-adjust: 100%;
            -webkit-text-size-adjust: 100%;
        }

        /* What it does: Centers email on Android 4.4 */
        div[style*="margin: 0"] {
            margin:0 !important;
        }

        /* What it does: Stops Outlook from adding extra spacing to tables. */
        table,
        td {
            mso-table-lspace: 0pt !important;
            mso-table-rspace: 0pt !important;
        }

        /* What it does: Fixes webkit padding issue. Fix for Yahoo mail table alignment bug. Applies table-layout to the first 2 tables then removes for anything nested deeper. */
        table {
            border-spacing: 0 !important;
            border-collapse: collapse !important;
            table-layout: fixed !important;
            margin: 0 auto !important;
            padding: 0 !important;
        }
        table table table {
            table-layout: auto;
        }

        /* What it does: Uses a better rendering method when resizing images in IE. */
        img {
            -ms-interpolation-mode:bicubic;
        }

        /* What it does: A work-around for email clients meddling in triggered links. */
        *[x-apple-data-detectors],  /* iOS */
        .x-gmail-data-detectors,    /* Gmail */
        .x-gmail-data-detectors *,
        .aBn {
            border-bottom: 0 !important;
            cursor: default !important;
            color: inherit !important;
            text-decoration: none !important;
            font-size: inherit !important;
            font-family: inherit !important;
            font-weight: inherit !important;
            line-height: inherit !important;
        }

        /* What it does: Prevents Gmail from displaying an download button on large, non-linked images. */
        .a6S {
            display: none !important;
            opacity: 0.01 !important;
        }
        /* If the above doesn't work, add a .g-img class to any image in question. */
        img.g-img + div {
            display:none !important;
           }

        /* What it does: Removes right gutter in Gmail iOS app: https://github.com/TedGoas/Cerberus/issues/89  */
        /* Create one of these media queries for each additional viewport size you'd like to fix */
        /* Thanks to Eric Lepetit @ericlepetitsf) for help troubleshooting */
        @media only screen and (min-device-width: 375px) and (max-device-width: 413px) { /* iPhone 6 and 6+ */
            .email-container {
                min-width: 375px !important;
            }
        }
    </style>

    <!-- Progressive Enhancements -->
    <!-- <style>
        /* Media Queries */
        @media screen and (max-width: 600px) {
            /* What it does: Forces elements to resize to the full width of their container. Useful for resizing images beyond their max-width. */
            .fluid {
                width: 100% !important;
                max-width: 100% !important;
                height: auto !important;
                margin-left: auto !important;
                margin-right: auto !important;
            }
            /* What it does: Forces table cells into full-width rows. */
            .stack-column,
            .stack-column-center {
                display: block !important;
                width: 100% !important;
                max-width: 100% !important;
                direction: ltr !important;
            }
            /* And center justify these ones. */
            .stack-column-center {
                text-align: center !important;
            }
            /* What it does: Adjust typography on small screens to improve readability */
          .email-container p {
            font-size: 13px !important;
            line-height: 24px !important;
          }
        }
      @media screen and (max-width: 400px) {
        .hide{display:none!important;}
        .block{display:block!important;}
      }
      
      

    </style> -->
</head>
<body width="100%"  style="margin: 0; mso-line-height-rule: exactly;">
        <div style="max-width: 680px; margin: 0;" class="email-container">
            <!--[if mso]>
            <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="680" align="center">
            <tr>
            <td>
            <![endif]-->
            <!-- Email Body : BEGIN -->
            <table role="presentation" cellspacing="0" cellpadding="0" border="0" align="left" width="100%" style="max-width: 680px; color: #000000;" class="email-container">
               <!-- 1 Column Text  -->
               <!--  <tr>
                    <td bgcolor="#ffffff">
                        <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
                            
                            <tr>
                                <td style="padding: 15px; text-align: left;">
                                  <span style="font-family:'Open Sans', sans-serif; font-weight:600; font-size: 46px; line-height: 36px; color: #555555; ">
                                  Celeste <br />Alonso
                                  </span> <br />
                                  <span style="font-size: 11px; font-weight:600;  line-height: 20px; color: #555555; ">THE PROPERTY AGENT</span>
                                </td>
                            </tr>
                          

                        </table>
                    </td>
                </tr> -->
                <!-- 1 Column Text + Button : END -->
                <tr>
                    <td dir="ltr" align="center" height="100%" valign="top" width="100%" style="color:#ffffff;padding: 0;">
                        <!--[if mso]>
                        <table role="presentation" border="0" cellspacing="0" cellpadding="0" align="center" width="660" style="width: 660px;">
                        <tr>
                        <td align="center" valign="top" width="660" style="width: 660px;">
                        <![endif]-->
                        <table role="presentation" border="0" cellpadding="0" cellspacing="0" align="center" width="100%" style="max-width:660px;">
                            <tr>
                                <td align="left" valign="center" style="font-size:0; padding: 0;">
                                    <!--[if mso]>
                                    <table role="presentation" border="0" cellspacing="0" cellpadding="0" align="center" width="660" style="width: 660px;">
                                    <tr>
                                    <td align="left" valign="center" width="220" style="width: 220px;">
                                    <![endif]-->
                                    <div style="display:inline-block; margin: 0 -2px; max-width: 271px; min-width:160px; vertical-align:middle; width:100%;" class="stack-column">
                                        <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
                                            <tr>
                                                <td  dir="ltr" style="padding: 0;">
                                                    <a href="https://paa-automation.com" title="Peak Analysis and Automation" alt="Peak Analysis and Automation"><img src="http://devnation.co.uk/emailers/paa-email/images/logo-sm.png" width="271" style="width: 100%;  max-width: 271px; height: auto;"/></a>
                                                    
                                                </td>
                                            </tr>
                                        </table>
                                    </div>
                                    <!--[if mso]>
                                    </td>
                                    <td align="left" valign="top" width="440" style="width: 440px;">
                                    <![endif]-->
                                    <div style="display:inline-block; margin: 0px; max-width:388px; min-width:320px; vertical-align:top;" class="stack-column">
                                        <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
                                            <tr>
                                                <td width="30" height="100%" style="vertical-align: top;">
                                                    <table width="100%" align="top" border="0" cellspacing="0" cellpadding="0">
                                                        <tr style="height: 45px; width: 30px;"></tr>
                                                        <tr>
                                                            <td style="width: 15px; border-right: 1px solid #9d9d9d; color: #9d9d9d; text-align: left; height: 80px;"></td>
                                                            <td style="width: 15px;"></td>
                                                        </tr>
                                                        <tr></tr>
                                                    </table>
                                                </td>
                                                <td dir="ltr" style="font-family: sans-serif; font-size: 10px; color: #9d9d9d; text-align: left;" class="center-on-narrow">
                                                    <table align="center" border="0" cellspacing="0" cellpadding="0">
                                                        <tr>
                                                            <td width="20" style="height: 42px;"></td>
                                                        </tr>
                                                    </table>
                                                    <span style="color: #007499; font-size: 18px;">Caroline Buggisch</span><br>
                                                    Marketing Manager<br>
                                                    <br>
                                                    T: <span style="color: #007499;">+44 (0) 01252 373000</span><br>
                                                    M: <span style="color: #007499;">+44 (0) 7807 554862</span><br>
                                                    E: <a style="color: #007499; text-decoration: none;" href="mailto:caroline.buggisch@paa-automation.com">caroline.buggisch@paa-automation.com</a><br><br>
                                                    <table width="100%" align="left" border="0" cellspacing="0" cellpadding="0">
                                                        <tr height="40">
                                                            <td width="7%">
                                                                <a href="https://twitter.com" title="Twitter" alt="Twitter"><img src="http://devnation.co.uk/emailers/paa-email/images/twitter.png"/></a>
                                                            </td>
                                                            <td width="7%">
                                                                <a href="https://linkedin.com" title="Linkedin" alt="Linkedin"><img src="http://devnation.co.uk/emailers/paa-email/images/linkedin.png"/></a>
                                                            </td>
                                                            <td width="7%"></td>
                                                            <td width="7%"></td>
                                                            <td width="60%"></td>
                                                        </tr>
                                                    </table>
                                                    <table width="100%" style="font-size: 8px;">
                                                        <tr>
                                                            <td>
                                                                This e-mail and any files transmitted are CONFIDENTIAL and they are intended solely for the use of the individual or entity to whom they are addressed. If you receive this e-mail in error, please notify info@paa-automation.com<br><br>
                                                                Company registration number: UK 2749962. Registered office: 6 Armstrong Mall, Southwood Business Park, Farnborough, Hampshire, GU14 0NR, UK
                                                            </td>
                                                        </tr>
                                                    </table>
                                                </td>
                                            </tr>
                                        </table>
                                    </div>
                                    <!--[if mso]>
                                    </td>
                                    </tr>
                                    </table>
                                    <![endif]-->
                                </td>
                            </tr>
                        </table>
                        <!--[if mso]>
                        </td>
                        </tr>
                        </table>
                        <![endif]-->
                    </td>
                </tr>
                <!-- Thumbnail Left, Text Right : END -->

                

            </table>
            <!-- Email Body : END -->

           

            <!--[if mso]>
            </td>
            </tr>
            </table>
            <![endif]-->
        </div>
</body>
</html>

```