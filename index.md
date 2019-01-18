## Use the following .htaccess rule

```
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteCond %{HTTPS} !=on
  RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
</IfModule>
```

That's it, your site will now redirect all traffic to `https://` and allow secure browsing.
