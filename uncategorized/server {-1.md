server {
    listen	 80;
    server_name  invoice.aandb.xyz;

        root  /www/html/anb/simpleinvoices;
        index  index.php index.html index.htm;

    location / {
        try_files $uri $uri/ /index.php?q=$uri&$args;
    }
     	error_page 404 /404.html;
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
        root   /usr/share/nginx/html;
    }
     	location ~ \.php$ {
            expires        -1;
            try_files $uri =404;
            fastcgi_intercept_errors on;
            include        fastcgi_params;
            fastcgi_index  index.php;
            #fastcgi_split_path_info ^(.+\.php)(/.+)$;
            fastcgi_param HTTPS $https;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            fastcgi_pass   127.0.0.1:9000;
        #try_files $uri =404;
        #fastcgi_pass unix:/var/run/php-fpm/php-fpm.sock;
        #fastcgi_index index.php;
        #fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        #include fastcgi_params;
    }

}

________X_________
server {
        listen   80; 

        root /var/www/; 
        index index.php index.html index.htm;

        server_name example.com; 

        location / {
        try_files $uri $uri/ /index.php;
        }

        location ~ \.php$ {
        
        proxy_set_header X-Real-IP  $remote_addr;
        proxy_set_header X-Forwarded-For $remote_addr;
        proxy_set_header Host $host;
        proxy_pass http://127.0.0.1:8080;

         }

         location ~ /\.ht {
                deny all;
        }
}

