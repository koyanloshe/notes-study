server {
    listen 80;
    server_name  aandb.xyz;
    return 301 https://www.aandb.xyz$request_uri;
}

————————————————————————————————————————

server {
    listen	 80;
    listen	 443 ssl;
    server_name  aandb.xyz;

    #charset koi8-r;
    #access_log  /var/log/nginx/log/host.access.log  main;

    =

    ssl_certificate             /etc/letsencrypt/live/aandb.xyz/fullchain.pem;
    ssl_certificate_key         /etc/letsencrypt/live/aandb.xyz/privkey.pem;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_prefer_server_ciphers on;
    ssl_dhparam /etc/ssl/certs/dhparam.pem;
    ssl_ciphers 'ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM$
    ssl_session_timeout 1d;
    ssl_session_cache shared:SSL:50m;
    ssl_stapling on;
    ssl_stapling_verify on;
    add_header Strict-Transport-Security max-age=15768000;

    location /ko1admin {
        if ($scheme != "https") {
                return 301 https://$host$uri;
        }
	root /www;
        index index.php;
        auth_basic "Admin Login";
        auth_basic_user_file /etc/nginx/pma_pass;
        location ~ \.php$ {
            expires        -1;
            try_files $uri =404;
            fastcgi_intercept_errors on;
            include        fastcgi_params;
            fastcgi_index  index.php;
            fastcgi_param HTTPS $https;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            fastcgi_pass   127.0.0.1:9000;
        }
    }

    location / {
        # try_files $uri $uri/ =404;
        try_files $uri $uri/ /index.php?q=$uri&$args;
    }

     	#location ~ /staging/(.*)/wp-admin/ {
        #        try_files $uri $uri/  /staging/$1/wp-admin/index.php?q=$uri&$args;
location ~ /staging/(.*)-blog {
                index   index.html index.htm index.php;
                try_files $uri $uri/ /staging/$1-blog/index.php?$args;

                location ~ \.php$ {
            expires        -1;
            try_files $uri =404;
            fastcgi_intercept_errors on;
            include        fastcgi_params;
            fastcgi_index  index.php;
            fastcgi_param HTTPS $https;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            fastcgi_pass   127.0.0.1:9000;
                }

        }

    error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }
    location = /404.html {
        root   /usr/share/nginx/html;
    }

    # proxy the PHP scripts to Apache listening on 127.0.0.1:80
    #
    #location ~ \.php$ {
    #    proxy_pass   http://127.0.0.1;
    #}

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    location ~ \.php$ {
            expires        -1;
            try_files $uri =404;
            fastcgi_intercept_errors on;
            include        fastcgi_params;
            fastcgi_index  index.php;
            #fastcgi_split_path_info ^(.+\.php)(/.+)$;
            fastcgi_param HTTPS $https;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        #include fastcgi_params;
    }
 location ~* \.(jpg|jpeg|gif|png|css|js|ico|xml|ttf|otf|woff)$ {
         access_log        off;
         log_not_found     off;
         expires           30d;
     }

    location ~ /.well-known
    {
        allow all;
    }

    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    #location ~ /\.ht {
    #    deny  all;
    #}
}

