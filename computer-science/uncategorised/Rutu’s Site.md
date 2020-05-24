# Rutu’s Site

Original Password: 0db084b293098711de18dbcdc7

Present Password: C7y0g3n

Server IP: _174.138.21.21_
_
_
Floating IP: 139.59.223.186

Private IP: 10.130.61.95 

User: rutu
Pass: rutu123_
_
_
_
server {
    listen       80;
    server_name www.lipsticksnmore.com lipsticksnmore.com;

    try_files $uri $uri/ /index.php?$args;
    root  /usr/share/nginx/html/lipsticksnmore;
    index  index.php;

    error_page 404 /404.html;
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }
     location ~ \.php$ {
        try_files $uri =404;
        include fastcgi.conf;
        fastcgi_pass unix:/run/php/php7.0-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }
}

Post LEMP install
server {
    listen 80 default_server;
#    listen [::]:80 default_server;

    root /usr/share/nginx/html/;
    index index.php index.html index.htm index.nginx-debian.html;

    server_name thebudgetindian.com www.thebudgetindian.com;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.0-fpm.sock;
    }

    location ~ /\.ht {
        deny all;
    }
}

PhpMyAdmin

username: root
password: a2730d25db1f25db20a39caff77be0167c999cf77e34af7e

Mysql pass a2730d25db1f25db20a39caff77be0167c999cf77e34af7e

thebudgetindian
rutu.ladage.123

