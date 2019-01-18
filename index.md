## 1. Make sure you have a valid SSL certificate

All modern hosting companies offer free [Let's encrypt](https://letsencrypt.org/) certificates. If you aren't sure, check with your hosting company.

## 2. Running a webserver with `mod_rewrite`

Your webserver should be interpreting `.htaccess` files and have `mod_rewrite` available. It's usually an Apache webserver or similar. Some nginx webservers interpret `.htaccess` too. If you are not sure, check with your hosting company.

## 2. Use the following .htaccess rule

The following rule should be placed on top or close to the top of your `.htaccess` file. Copy the code, save it in the file and check if you get redirected from `http://your-domain.wtf` to `https://your-domain.wtf`.

```
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteCond %{HTTPS} !=on
  RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
</IfModule>
```

That's it, your site will now redirect all traffic to `https://` and allow secure browsing.
