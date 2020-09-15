# Web Servers

It is typical to use the front-controller pattern to funnel appropriate HTTP requests received by your web server to a single PHP file. The instructions below explain how to tell your web server to send HTTP requests to your PHP front-controller file.

### Serving Your Application using server
To serve your project locally you may use the built-in PHP development server:

```bash
php -S localhost:8000
```

Or any php local server application like [Xampp](https://www.apachefriends.org/index.html).

> **Warning**: The built-in web server was designed to aid application development. It may also be useful for testing purposes or for application demonstrations that are run in controlled environments. It is not intended to be a full-featured web server. It should not be used on a public network.


## Apache configuration

Ensure your `.htaccess` and index.php files are in the same public-accessible directory. The `.htaccess` file should contain this code:

```bash
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php/$1 [QSA,L]
```

This `.htaccess` file requires URL rewriting. Make sure to enable Apache’s mod_rewrite module and your virtual host is configured with the AllowOverride option so that the `.htaccess` rewrite rules can be used:

```bash
AllowOverride All
```


## Nginx configuration
This is an example Nginx virtual host configuration for the domain `example.com`. It listens for inbound HTTP connections on port 80. It assumes a PHP-FPM server is running on port `9123`. You should update the `server_name`, `error_log`, `access_log`, and root directives with your own values. The root directive is the path to your application’s public document root directory; your `MiniPHP` app’s index.php front-controller file should be in this directory.

```php
server {
    listen 80;
    server_name example.com;
    index index.php;
    error_log /path/to/example.error.log;
    access_log /path/to/example.access.log;
    root /path/to/project;

    location / {
        try_files $uri /index.php$is_args$args;
    }

    location ~ \.php {
        try_files $uri =404;
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        fastcgi_param SCRIPT_NAME $fastcgi_script_name;
        fastcgi_index index.php;
        fastcgi_pass 127.0.0.1:9123;
    }
}
```