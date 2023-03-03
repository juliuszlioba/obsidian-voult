Static build + Wordpress
```
# FROM: https://stackoverflow.com/questions/39666414/redirect-subfolder-to-root-and-hide-it-in-the-url

RewriteEngine On

# HTTP to HTTPS
RewriteCond %{SERVER_PORT} 80
RewriteRule ^(.*)$ https://zustellpartner.at/$1 [R,L,NC]

# Exceptions
RewriteCond %{REQUEST_URI} ^/(wp-admin|wp-login)/ [NC]
RewriteRule ^ - [L]

# Ensure that all directory requests include a trailing slash
RewriteCond %{REQUEST_URI} /+[^\.]+$
RewriteRule ^(.+[^/])$ %{REQUEST_URI}/ [R=301,L]

# Make /build/20220914a like it was root
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{THE_REQUEST} /build/20220914a/([^\s]+) [NC]
RewriteRule ^ /%1 [NC,L,R=301]
RewriteCond %{REQUEST_URI} !^/build/20220914a
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(.*)$ /build/20220914a/$1 [NC,L,QSA]

# Wordpress config
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
```