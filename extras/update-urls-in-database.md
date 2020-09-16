# Update URLs in database

Run this in SQL query to update URLs in WordPress database when moving from local machine to server.

```

UPDATE wp_options SET option_value = replace(option_value, 'http://www.old-domain.com', 'http://www.new-domain.com') WHERE option_name = 'home' OR option_name = 'siteurl';
UPDATE wp_posts SET guid = replace(guid, 'http://www.old-domain.com','http://www.new-domain.com');
UPDATE wp_posts SET post_content = replace(post_content, 'http://www.old-domain.com', 'http://www.new-domain.com');
UPDATE wp_postmeta SET meta_value = replace(meta_value, 'http://www.old-domain.com', 'http://www.new-domain.com');

```