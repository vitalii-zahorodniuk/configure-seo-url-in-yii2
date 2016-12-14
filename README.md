Configure SEO-friendly URLs in Yii2:
=
1. In main `.htaccess` file, after `RewriteEngine` or `RewriteBase` *(if exist)* add:

  ```apache
  # see 
  RewriteCond %{REQUEST_URI} !(/$|\.)
  RewriteRule (.*) %{REQUEST_URI}/ [R=301,L]
  ```

1. Configure yii url manager component with next params:
  ```php
  'urlManager' => [
    'enablePrettyUrl' => true,
    'showScriptName' => false,
    'suffix' => '/',
    'normalizer' => [
      'class' => \yii\web\UrlNormalizer::className(),
      'normalizeTrailingSlash' => false,
      'action' => \yii\web\UrlNormalizer::ACTION_REDIRECT_PERMANENT,
    ],
  ],
  ```
