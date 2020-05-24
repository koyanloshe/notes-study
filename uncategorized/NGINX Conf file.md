# NGINX Conf file

server {
    listen	 80;
    server_name  128.199.108.97;

    location / {
        try_files $uri $uri/ =404;
        root   /usr/share/nginx/html;
        index  index.php index.html index.htm;
    }
     	error_page 404 /404.html;
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }
     	location ~ \.php$ {
        try_files $uri =404;
        fastcgi_pass unix:/var/run/php-fpm/php-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }
}

———————————————————X———————————————————

server {
    listen	 80;
    server_name  mq.cityofmusic.in;

        root   /usr/share/nginx/html/cityofmusic;
        index  index.php index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }
     	error_page 404 /404.html;
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
        root   /usr/share/nginx/html;
    }
     	location ~ \.php$ {
        try_files $uri =404;
        fastcgi_pass unix:/var/run/php-fpm/php-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }
}

———————————————————X—————————————————————

server {
    listen	 80;
    server_name staging.aandb.xyz;

    location / {
        try_files $uri $uri/ =404;
        root   /usr/share/nginx/html;
        index  index.php index.html index.htm;
    }
     	error_page 404 /404.html;
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }
     	location ~ \.php$ {
        try_files $uri =404;
        fastcgi_pass unix:/var/run/php-fpm/php-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }
}

———————————————X——————————————————

server {
    listen	 80;
    server_name  groupintegrated.com www.groupintegrated.com;

        root   /usr/share/nginx/html/integrated-spaces;
        index  index.php index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }
     	error_page 404 /404.html;
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
        root   /usr/share/nginx/html;
    }
     	location ~ \.php$ {
        try_files $uri =404;
        fastcgi_pass unix:/var/run/php-fpm/php-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }
}

location /blog {
        try_files $uri $uri/ /blog/index.php?$args;
       }
        # Add trailing slash to */wp-admin requests.
       rewrite /wp-admin$ $scheme://$host$uri/blog permanent;

————————————X——————————————

server {
    listen	 80;
    server_name  seoagencymumbai.in www.seoagencymumbai.in;

        root   /usr/share/nginx/html/seo-agency-mumbai;
        index  index.php index.html index.htm;

  location / {
	try_files $uri $uri/ =404;
    }
     	error_page 404 /404.html;
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }
     	location ~ \.php$ {
        try_files $uri =404;
        fastcgi_pass unix:/var/run/php-fpm/php-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }
}

