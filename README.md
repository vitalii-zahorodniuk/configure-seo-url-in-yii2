Configure SEO-friendly URLs in Yii2:
=

1. In `.htaccess` file add:

  ```apache
  # Add a slash at the end of the URLs
  RewriteCond %{REQUEST_URI} !(/$|\.)
  RewriteRule .* %{REQUEST_URI}/ [R=301,L]
  # Remove the double slashes from URLs
  RewriteCond %{THE_REQUEST} //
  RewriteRule .* /$0 [R=301,L]
  ```
  
1. Add slash suffix & disable normalizer in urlManager component config:
  ```php
  'urlManager' => [
    'suffix' => '/',
    'normalizer' => false,
    // other url manager config
  ],
  ```
