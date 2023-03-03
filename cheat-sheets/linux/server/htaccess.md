Static folder with SGS  + Wordpress

```
# FROM: https://stackoverflow.com/questions/39666414/redirect-subfolder-to-root-and-hide-it-in-the-url

<IfModule mod_rewrite.c>

RewriteEngine On

# HTTP to HTTPS
RewriteCond %{SERVER_PORT} 80
RewriteRule ^(.*)$ https://connect724.at/$1 [R,L,NC]

# Exceptions
RewriteCond %{REQUEST_URI} ^/(wp-admin|wp-login)/ [NC]
RewriteRule ^ - [L]

# Ensure that all directory requests include a trailing slash
RewriteCond %{REQUEST_URI} /+[^\.]+$
RewriteRule ^(.+[^/])$ %{REQUEST_URI}/ [R=301,L]

# Make /dist/2023-03-03-0900 like it was root
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{THE_REQUEST} /dist/2023-03-03-0900/([^\s]+) [NC]
RewriteRule ^ /%1 [NC,L,R=301]
RewriteCond %{REQUEST_URI} !^/dist/2023-03-03-0900
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(.*)$ /dist/2023-03-03-0900/$1 [NC,L,QSA]

# WordPress
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]

</IfModule>
```